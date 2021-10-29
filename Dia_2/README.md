# Controle de qualidade

>**Objetivo:** Evitar que um dado ruim atrapalhe suas interpretações ao final da análise. Evitar o problema [*"garbage in, garbage out"*](https://en.wikipedia.org/wiki/Garbage_in,_garbage_out)

>**Tempo de duração:** 12 horas

## 📜 Introdução

Na culinária é bom termos ingredientes de qualidade para prepararmos bons pratos. Na bioinformática isso não é muito diferente. Precisamos conferir aspectos como:

- O resultado do sequenciamento é bom o suficiente?
- As leituras sequenciadas são mesmo da espécie que eu espero?
- Tenho algum problema de contaminação?

Na etapa anterior pedimos para que fossem identificadas as variantes na amostra fornecida. Isso deve ter resultado em um arquivo com as variantes e um outro arquivo com o alinhamento das leituras de sequenciamento sobre o genoma referência usado (cromossomo 22).

Nesta etapa você deverá usar ferramentas que te possibilitem responder as perguntas citadas acima. Se você já trabalha com bioinformática é bem possível que já tenha em seu cinto de ferramentas as de sua preferência. Caso este não seja o caso, sinta-se livre para buscar a que melhor se encaixa as suas preferências. Listamos aqui alguns exemplos:

- [Samtools](http://www.htslib.org/): o verdadeiro canivete-suiço para quem trabalha com alinhamentos NGS.

- [Picard](https://broadinstitute.github.io/picard/): muito conveniente caso você seja familiar com as ferramentas GATK.

- [Mosdepth](https://github.com/brentp/mosdepth): Ferramenta especializada no cálculo de coberturas.

- [VerifyBamId](https://github.com/Griffan/VerifyBamID): Infere a porcentagem de contaminação que sua amostra possui. Também pode extrair informações que auxiliam na predição da ancestralidade global de sua amostra.


Há quem prefira escrever o próprio programa para extrair essas informações. Isso é extremamente produtivo para que você se familiarize com os diferentes dados que existem em cada formato de arquivo de bioinformática ([ideia compartilhada por Heng Li do BWA/Samtools](https://twitter.com/lh3lh3/status/1451600007115780098)), no entanto também é altamente arriscado, pois ao fazer isso muito provavelmente você será o único que conhece a fundo os detalhes de sua implementação. Se este caminho te atrai lembre-se de escrever testes automatizados para seu código e também pedir para que colegas [revisem o que foi escrito](https://docs.github.com/en/github/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews).

Caso você tenha mais experiência fora da computação e esteja embarcando apenas recentemente na bioinformática, talvez este texto publicado pela *Nature* possa lhe interessar: [A cartoon guide to bioinformatics by a novice coder](https://www.nature.com/articles/d41586-021-01485-y).

## 📦 Dados

### Fornecido

- 1 BED: delimita as regiões de captura do kit de exoma.

### Gerado em [Genotipagem de um cromossomo](../Dia_1/README.md)

* VCF: variantes identificadas na etapa anterior deste desafio.
* BAM: alinhamento das leituras de sequenciamento contra o cromossomo 22.

## 👷 Tarefa

**Conseguir extrair informações sobre as variantes encontradas. Para isso usem quaisquer ferramentas.**

### Downloads

Deixamos os arquivos disponíveis no Google Drive, para baixar acesse o link e clique no botão "fazer download", no canto superior direito da tela.

- [BED cobertura esperada](https://drive.google.com/file/d/17-vrNzHEMyH7VEV1_91WgG4Bcpr_QDak/view?usp=sharing) - Segundo o fabricante;

### Resolver as seguintes questões

1) Quais variantes deverão ser desconsideradas no seu VCF? - Qualquer métrica do software de escolha poderá ser utilizada. Discorra sobre a métrica utilizada.

2) Discorra sobre as regiões com baixa cobertura e quais foram seus critérios. Figuras são bem-vindas.

3) Obter informações sobre seu alinhamento. Quantos reads? Qual a porcentagem deles que foi mapeada corretamente? Muitos alinharam em mais de um local do genoma com a mesma qualidade?

### Resultados

- Para a questão 1 deverá ser enviado o VCF pós-filtragem.
- Para a questão 2 deverá ser enviado um BED, contendo as regiões não cobertas.
- Para a terceira questão deverá ser enviado um arquivo TSV, com as colunas "nreads" (número de reads usados),   "proper_pairs" (pares mapeados corretamente), "mapQ_0" (número de reads com qualidade de mapeamento == 0)
- Sendo que a parte escrita das questões deverá ser enviada em um arquivo de texto (no próprio `README.md`, por exemplo).

## 🔗 Links

- [A cartoon guide to bioinformatics by a novice coder](https://www.nature.com/articles/d41586-021-01485-y)

- [*"garbage in, garbage out"*](https://en.wikipedia.org/wiki/Garbage_in,_garbage_out)
