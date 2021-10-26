# Dicas para desenvolvimento

Acesso rápido:
- [Controle de versão](#controle-de-versão)
- [Workflow de análise](#workflow-de-análise)
- [Dependências do projeto](#dependências-do-projeto)
- [Scripts customizados](#scripts-customizados)

## Controle de versão

Utilize algum serviço para [controle de versão](https://www.atlassian.com/br/git/tutorials/what-is-version-control). Exemplos comuns são: GitHub e GitLab.

Este documento que você está lendo está armazenado no GitHub, de forma que toda alteração que ele venha a ter ficará registrada. Dessa forma, fica fácil verificar quais foram as mudanças e quem foram os responsáveis.

Também fica fácil voltarmos para uma versão anterior, caso isso seja necessário.

Explicar o funcionamento do Git foge um pouco ao escopo deste material, mas existem excelente materiais em que vocês podem estudar:

- Alura: [Git e Github: O que são, Como Configurar e Primeiros Passos](https://www.alura.com.br/artigos/o-que-e-git-github)
- [Como usar Git e Github na prática: Guia para iniciantes (YouTube)](https://www.youtube.com/watch?v=2alg7MQ6_sI)


## Workflow de análise

Existem diversas maneira de você organizar seu workflow (também chamado de pipeline). A mais simples delas é organizar tudo em um bash script junto com as instruções para a instalação das dependências, como neste exemplo:

- [playing-with-bioinformatics-files.sh](https://github.com/lmtani/lmtani.github.io/blob/main/_code/playing-with-bioinformatics-files/playing-with-bioinformatics-files.sh) - Bash script com o workflow de análise
- [environment.yml](https://github.com/lmtani/lmtani.github.io/blob/main/_code/playing-with-bioinformatics-files/environment.yml)- Arquivo que facilita a instalação de dependências, usando miniconda.


Existem também repositórios em que organizam as etapas utilizando uma outra linguagem ao invés de Bash, como o FunGAP que organiza cada uma das etapas em scripts em Python. As instruções para a instalação das dependências ficam em um segundo documento, e como usam diversos programas a configuração do ambiente é um pouco difícil. Exemplos:

[run_augustus.py](https://github.com/CompSynBioLab-KoreaUniv/FunGAP/blob/master/run_augustus.py) - Encapsula a chamada do programa de predição de genes Augustus utilizando Python.
[INSTALL.md](https://github.com/CompSynBioLab-KoreaUniv/FunGAP/blob/master/INSTALL.md) - Instruções sobre como instalar as dependências.

As linguagens dedicadas a construção de workflows visam facilitar esse processo. [Nextflow](https://www.nextflow.io/), [WDL](https://github.com/openwdl/wdl/blob/main/versions/1.1/SPEC.md) e [CWL](https://www.commonwl.org/user_guide/) são exemplos desse tipo de linguagem. Com elas você pode focar em escrever os processos que deseja separadamente, e então liga-los em um workflow completo de análise. Geralmente elas acompanham recursos como: reaproveitamento dos resultados que já foram obtidos anteriormente, portabilidade para infraestrutura de cluster ou de cloud (Google, Amazon, etc) e medidas a respeito do tempo que cada tarefa levou e também dos recursos computacionais consumidos.

Note que essas linguagens acabam adicionando uma camada a mais na complexidade a seu projeto e por isso você precisa avaliar se é algo que lhe será útil. Faça-se as perguntas: vou executar esta análise mais do que uma vez na vida? é importante que outras pessoas consigam reproduzir meu workflow? estou disposto a investir algumas horas no aprendizado disto? 

Resumindo: essas linguagens te oferecem reprodutibilidade, portabilidade e escalabilidade. Se tiver interesse consulte as documentações para aprender mais ou veja o trabalho [Practical guide for managing large-scale human genome data in research (2020)](https://www.nature.com/articles/s10038-020-00862-1) para saber mais sobre os cenários que me essas ferramentas brilham.


## Dependências do projeto

Os workflows de análise costumam ter várias etapas de processamento. Imagine uma analise em que as leituras de sequenciamento primeiro passam por um programa para controle de qualidade (QC), posteriormente passam por uma etapa de alinhamento e depois algumas métricas deste alinhamento são extraidas. 

Uma opção para esse fluxo seria realizar o controle de qualidade com o programa [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/), posteriormente o alinhamento com [BWA](https://github.com/lh3/bwa) e a extração de métricas do alinhamento com o  programa [Samtools](https://github.com/samtools/samtools). Dependendo do sistema operacional (Ubuntu, fedora, Windows, MacOS) cada uma delas pode ter uma maneira diferente de ser instalada, pode até mesmo não estar disponivel.

Caso fosse optado por resolver o problema das dependencias com miniconda a solução ficaria semelhante a este arquivo, nomeado `environment.yml`:

```yml
name: nome-arbitrario-do-ambiente
channels:
    - conda-forge
    - defaults
    - bioconda
dependencies:
    - bwa=0.7.17
    - samtools=1.14
    - fastqc=0.11.9
```

Para instalar suas dependencias poderia ser usado o comando `conda env create -f environment.yml`, e depois `conda activate nome-arbitrario-do-ambiente`.


Caso fosse optado pelo uso de uma imagem Docker, poderiamos ter um arquivo `Dockerfile` com:

```dockerfile
FROM mambaorg/micromamba:0.15.3

RUN micromamba install -c bioconda -c conda-forge -c defaults -y -n base \
        bwa=0.7.17 \
        samtools=1.14 \
        fastqc=0.11.9 && \
    micromamba clean --all --yes
```

Para usa-lo, poderia-se gerar a imagem com `docker build -t minha-imagem .` no mesmo diretório do Dockerfile. Posteriormente poderia rodar com `docker run -it --rm -v /caminho/que/quiser:/work minha-imagem bash`. Dessa forma você teria acesso a todos seus arquivos do diretorio `/caminho/que/quiser` dentro do container, bem como as dependencias.

Cada vez mais, ferramentas como Miniconda e Docker vem sendo usadas para contornar o problema das dependencias (e o famoso "funciona na minha máquina"). Para mais informações sobre como usar essas ferramentas consulte:

- [Bioconda: Getting Started](https://bioconda.github.io/user/install.html#getting-started)
- [Conda or Mamba for production](https://labs.epi2me.io/conda-or-mamba-for-production/) - Comparativo entre Conda e Mamba.
- [Docker](https://docs.docker.com/) - diferente da solução com miniconda, esta exige permissão de administrador no computador em que for ser instalada.
- [Ten simple rules for writing Dockerfiles for reproducible data science (2020)](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1008316) - Apenas para o caso de ser um aventureiro e quiser entender melhor a complexidade do mundo dos containers. Apesar do nome, acredito que não seja tão simples para quem ainda não é familiar com o problema.

## Scripts customizados

Algumas vezes precisaremos escrever instruções e optamos pela linguagem que mais nos sentimos confortáveis, geralmente para tarefas simples como organizar o dado de output de algum programa de controle de qualidade ou mesmo transformar um formato de arquivo em um outro.

Aqui podemos sofrer do mesmo mal que faz com que [a maior parte dos acidentes de carro ocorram próximos a residência do motorista](https://www.truscellolaw.com/blog/2021/03/car-accidents-happen-home/) - excesso de confiança. Para evitar cometer erros por minimizar a complexidade do problema sempre verifique todos os possiveis formatos que o dado pode se apresentar, por exemplo:

Arquivos no [formato VCF](https://en.wikipedia.org/wiki/Variant_Call_Format) podem ter muitos alelos alternativos descritos em uma mesma posição. Caso isso ocorra as colunas INFO (coluna 7) e os dados de cada amostra (coluna 9 para frente) terão campos que comportam cada um dos alelos. Se você assumir que sempre terá apenas um alelo alternativo por linha estará próximo a um acidente grave.

Sempre pense também a respeito de possiveis testes automáticos que você possa elaborar. Normalmente executamos sucessivas vezes o script até que o codigo esteja bom. Para ver se está bom inspecionamos manualmente alguns aspectos do output. Seus testes automáticos podem começar por delegar ao computador a tarefa de inspecionar os outputs.

Para quem já veio da computação isso é um pouco ["chover no molhado"](https://www.dicio.com.br/chover-no-molhado/#:~:text=Significado%20de%20Chover%20no%20molhado,pretens%C3%B5es%20do%20time%20no%20campeonato.), mas é importante destacar isso para os candidatos que vem de biológicas e estão embarcando agora na bioinformática. Uma biblioteca que facilita um pouco esta tarefa é a [pytest-workflows](https://pytest-workflow.readthedocs.io/en/stable/#introduction). Para os testes mais simples você nem irá precisar escrever em Python.
