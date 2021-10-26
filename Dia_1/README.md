# Genotipagem de um cromossomo

>**Objetivo:** Identificar as variantes presentes nos dados fornecidos

>**Tempo de duração:** 12 horas

## 📜 Introdução

Nosso genoma (sim, de todos *Homo sapiens*) é grande, no sentido de que possui muitos nucleotideos em sua composição. Questões que parecem simples, como por exemplo: "Essa pequena sequencia existe no genoma?" ou "Consigo alinhar de alguma forma essa sequencia com o genoma refêrencia?", se tornam computacionalmente muito intensas.


<p align="center">
  <img style="float: right;" width="600px" src="../img/bioninja-genome-sizes.jpeg" alt="Tamanho dos genomas">
</p>

Imagem de: [https://ib.bioninja.com.au](https://ib.bioninja.com.au/standard-level/topic-3-genetics/32-chromosomes/genome-size.html)

A fim de tornar este desafio mais democrático optamos por disponibilizar apenas parte dos dados. Nesta etapa iremos disponibilizar os dados referentes ao cromossomo 22. Um genoma humano padrão possui 22 pares de cromossomos autossômicos e 1 par (X e Y) de cromossomos sexuais.

O cromossomo 22 não é o menor de nossos autossômicos, mas está entre eles.

Nesta primeira fase do nosso desafio iremos identificar todas as variantes presentes na amostra que fornecemos (FASTQs). Esta etapa é importante pois é com os resultados dela que iremos nos aprofundar na busca pelas variantes potencialmente patogênicas que podem estar presentes. Para mais informações gerais sobre testes genéticos leia o texto de nosso blog: [Efeito Angelina Jolie e testes geneticos](https://blog.mendelics.com.br/efeito-angelina-jolie-e-testes-geneticos-cancer-de-mama/).

> Não deixe de conferir os outros links para mais informações!

## 📦 Dados fornecidos

* 1 FASTA: sequência de nucleotídeos do cromossomo 22. A mesma disponível em bancos públicos. Adicionaremos aqui apenas para conveniência.
   - Este arquivo é popularmente conhecido como "Genoma Referência" quando contém os dados de todos os cromossomos da espécie. Caso queira baixar, ou esteja apenas curioso a respeito, dê uma olhada nos links no final desta página.
* 1 par de FASTQs: leituras de sequenciamento Illumina, biblioteca de sequenciamento preparada com kit de exomas.
* VCF - algumas variantes que esperamos que estejam no seu resultado final. Se elas estiverem ausentes é sinal de que algo na sua análise pode estar incorreto.

## 👷 Tarefa

🚧 Será divulgada às 12h do dia 28/10/21 🚧


## 🔗 Links

- [Google Life Sciences - Genomas referência](https://cloud.google.com/life-sciences/docs/resources/public-datasets/reference-genomes)
  - Já faz algum tempo que o Google vem investindo no desenvolvimento de produtos dedicados a problemas biológicos. Neste link é possível encontrar diferentes versões do genoma humano para download, bem como uma tabela com os dados e os metadados de projetos como 1,000 Genomas - no menu lateral.

- [t2t CHM13 - a versão mais completa do genoma humano](https://www.nature.com/articles/d41586-021-01506-w)
  - Em 2021 pesquisadores combinaram diversas técnicas de sequenciamento para completar regiões problemáticas do genoma humano. Neste trabalho existem informações interessantes sobre as principais diferenças em relação a versão que hoje é a mais amplamente utilizada - a GRCh38.

- [Biostars - Discussão sobre genotipagem/chamada de variantes](https://www.biostars.org/p/277927)
  - Existe uma resposta bastante informativa onde Kevin Blighe discorre sobre as principais diferenças nos termos com base na experiência dele. Também tem um apontamento importante sobre o contexto populacional que existe por trás da definição de SNP (Single Nucleotide Polymorfism). Nem toda variante é um SNP!
