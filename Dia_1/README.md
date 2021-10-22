## Genotipagem de um cromossomo

O genoma humanos é muito longo, no sentido de que possui muitos nucleotideos. Isso torna necessário o uso de muitos recursos computacionais para que a análise seja concluida em tempo hábil.

<p align="center">
  <img style="float: right;" src="img/bioninja-genome-sizes.jpeg" alt="Tamanho dos genomas"/>
</p>

A fim de tornar o desafio mais democrático optamos por disponibilizar apenas parte dos dados. Um genoma humano padrão possui 22 pares de cromossomos autossomicos e 1 par (X e Y) de cromossomos sexuais.

Nesta etapa iremos disponiblizar dados referentes ao cromossomo 22. Não é o menor de nossos autossomicos mas está entre eles.

> Curiosidade: existe certo debate a respeito do termo correto para nomear esta etapa da análise. Não parece existir consenso mas existe uma discussão interessante no fórum Biostars. [Confira esta resposta caso queira mais detalhes](https://www.biostars.org/p/277927/#278051).

Objetivo: Identificar as variantes presentes nos dados fornecidos
Tempo de duração: 12 horas

### Dados fornecidos

* 1 FASTA: sequencia de nucleotídeos do cromossomo 22. A mesma disponível em bancos publicos. Adicionaremos aqui apenas para conveniência.
    - Este arquivo é popularmente conhecido como "Genoma Referencia" quando contém os dados de todos os cromossomos da espécie. Caso queira baixar, ou esteja apenas curiosos a respeito, de uma olhada nos links no final desta página.
* 1 par de FASTQs: leituras de sequenciamento Illumina, biblioteca de sequenciamento preparada com kit de exomas.
* VCF - algumas variantes que esperamos que estejam no seu resultado final. Se elas estiverem ausentes é sinal de que algo na sua análise pode estar incorreto.

### Tarefa

Será divulgada no dia do desafio.


### Links

- [Google Life Sciences - Genomas referência](https://cloud.google.com/life-sciences/docs/resources/public-datasets/reference-genomes)
  - Já faz algum tempo que o Google vem investindo no desenvolvimento de produtos dedicados a problemas biológicos. Neste link é possivel encontrar diferentes versões do genoma humano para download, bem como uma tabela com os dados e os metadados de projetos como 1,000 Genomas - no menu lateral.

- [t2t CHM13 - a versão mais completa do genoma humano](https://www.nature.com/articles/d41586-021-01506-w)
  - Em 2021 pesquisadores combinaram diversas tecnicas de sequenciamento para completar regiões problemáticas do genoma humano. Neste trabalho existem informações interessantes sobre as principais diferenças em relação a versão que hoje é a mais amplamente utilizada - a GRCh38.

- [Biostars - Discussão sobre genotipagem/chamada de variantes](https://www.biostars.org/p/277927)
  - Existe uma resposta bastante informativa onde Kevin Blighe discorre sobre as principais diferenças nos termos com base na experiencia que ele tem. Também tem um apontamento importante sobre o contexto populacional que existe por trás da definição de SNP (Single Nucleotide Polimorfism). Nem toda variante é um SNP!