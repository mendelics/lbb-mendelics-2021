# Organização do trabalho

Algumas dicas para que você tenha uma boa organização


## Controle de versão

Utilize algum serviço para [controle de versão](https://www.atlassian.com/br/git/tutorials/what-is-version-control). Exemplos comuns são: GitHub e GitLab.

Este documento que você está lendo está armazenado no GitHub, de forma que toda alteração que ele venha a ter ficará registrada. Dessa forma, fica fácil verificar quais foram as mudanças e quem foram os responsáveis.

Também fica fácil voltarmos para uma versão anterior, caso isso seja necessário.

Explicar o funcionamento do Git foge um pouco ao escopo deste material, mas existem excelente materiais em que vocês podem estudar:

- Alura: [Git e Github: O que são, Como Configurar e Primeiros Passos](https://www.alura.com.br/artigos/o-que-e-git-github)
- [Como usar Git e Github na prática: Guia para iniciantes (YouTube)](https://www.youtube.com/watch?v=2alg7MQ6_sI)


## Workflow de análise

Existem diversas maneira de você organizar seu workflow (também chamado de pipeline). A mais simples delas é organizar tudo em um shell script junto com as instruções para a instalação das dependencias, como neste exemplo:

- [playing-with-bioinformatics-files.sh](https://github.com/lmtani/lmtani.github.io/blob/main/_code/playing-with-bioinformatics-files/playing-with-bioinformatics-files.sh) - Bash script com o workflow de análise
- [environment.yml](https://github.com/lmtani/lmtani.github.io/blob/main/_code/playing-with-bioinformatics-files/environment.yml)- Arquivo que facilita a instalação de dependencias, usando miniconda.


Existem também repositórios em que organizam as etapas utilizando uma outra linguagem ao invés de Bash, como o FunGAP que organiza cada uma das etapas em scripts em Python. As instruções para a instalação das dependencias fica em um documento a parte, e como usam diversos programas a configuração do ambiente é um pouco difícil. Exemplos:

[run_augustus.py](https://github.com/CompSynBioLab-KoreaUniv/FunGAP/blob/master/run_augustus.py) - Encapsula a chamada do programa de predição de genes Augustus utilizando Python.
[INSTALL.md](https://github.com/CompSynBioLab-KoreaUniv/FunGAP/blob/master/INSTALL.md) - Instruções sobre como instalar as dependencias.





Dois elementos muito importante que um bom bioinformata sempre precisa considerar são: reprodutibilidade e portabilidade. Se seu projeto também precisar processar muitas amostras em um curto período de tempo então pode-se adicionar escalabilidade à suas considerações.

> Para mais informações sobre estes aspectos consulte: [Practical guide for managing large-scale human genome data in research (2020)](https://www.nature.com/articles/s10038-020-00862-1)

