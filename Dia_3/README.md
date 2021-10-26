## Investigando as variantes

>**Objetivo:** Adicionar informações às variantes identificadas a fim de facilitar a interpretação dos resultados.

>**Tempo de duração:** 6 horas

## 📜 Introdução

Existem diversos bancos de dados com informações genéticas a respeitos de variantes conhecidas do genoma humano. Alguns são focados em estudos sobre populações, como o [gnomAD](https://gnomad.broadinstitute.org/), enquanto outros são dedicados a relacionar variantes à doenças, como o [ClinVar](https://www.ncbi.nlm.nih.gov/clinvar/).

Em um exoma padrão podemos ter entre 50 a 100 mil variantes. Conseguimos reduzir este número usando informações de bancos de dados como os citados acima. Além destes bancos existem ferramentas, como o [SnpEff](http://pcingola.github.io/SnpEff/) e o [VEP](https://www.ensembl.org/info/docs/tools/vep/index.html), que adicionam informações a cada uma de suas variantes, como por exemplo: se a variante causa um efeito sinonimo ou não sinonimo na proteína.

O Ensembl oferece uma ferramenta online muito conveniente, pois permite consultar pontualmente algumas informações, como por exemplo: qual a coordenada de determinado gene, se a variante já é conhecida, ou se já foi anotada pelo vep, entre várias outras informações. Todas as informações desta ferramenta estão disponiveis em [https://rest.ensembl.org/](https://rest.ensembl.org/).

> Caso tenha ficado curioso sobre a palavra REST, veja este texto da [RedHat - API REST](https://www.redhat.com/pt-br/topics/api/what-is-a-rest-api). Este conceito é bastante usado quando desenvolvemos serviços que respondem via internet.

Apesar de termos citado como exemplo algumas ferramentas, fique a vontade para explorar outras que lhe pareçam úteis, pois sempre estão saindo novas tools. Lembre-se de sempre documentar os passos que você seguiu.

## 📦 Dado gerado em [Controle de qualidade](../Dia_2/README.md)

* VCF com as variantes identificadas

## 👷 Tarefa

🚧 Será divulgada às 12h do dia 30/10/21 🚧

## 🔗 Links

- [API REST do Ensembl (GRCh38)](https://rest.ensembl.org/)
- [gnomAD](https://gnomad.broadinstitute.org/)
- [ClinVar](https://www.ncbi.nlm.nih.gov/clinvar/)