#![ ](https://panda.ime.usp.br/aulasPython/static/aulasPython/_images/python-logo.png "Python")

**A linguagem Python**

O Python é uma das linguagens de programação mais populares da atualidade. A linguagem tem se destacado nos últimos anos com bibliotecas robustas de data science e é apoiada por uma comunidade gigante e bastante participativa que busca sempre a evolução da linguagem.
Como um apaixonado por Python resolvi fazer o trabalho dando uma vasculhada sobre o que as pessoas mais andam falando a respeito do Python
***

**Pré-requisitos**

Knime Analytics - que pode ser baixado nesse [link](https://www.knime.org/downloads/overview). Algumas bibliotecas que não são padrões precisaram ser instaladas.

Token para acesso ao twitter

***
**KNIME**

Para o estudo vamos utilizar o sotware de mineração de dados KNIME. Uma ferramenta muito robusta e lider do quadrante do Gartner em ferramentas de mineraçãoo. O Knime foi construído há mais de uma década para acessar dados de forma intuitiva e interativa a fim de ajudar a comunidade de cientistas, analistas e engenheiro de dados e é uma solução OpenSource

***
**Obtendo Twitters**

A fonte de dados utilizada é o site https://twitter.com/, e será acessado pelo `Twitter API Connector`
Aqui é onde usamos o token para autenticação citado nos requisitos

![ ](https://github.com/ggdcdevel/TraballhoR1/blob/master/Acessando_o_twitter.png  "Twitter_API")

Nessa etapa, o nó `Twitter Search` busca os dados do Twiter de acordo com a minha chave de busca, nesse caso específico busquei pela chave "python  since:2015-01-01". Porque a ideia era trazer todos os twits contendo a palavra python desde 2015. Porém esse conector tem alguns limitadores e não traz todos os twitters de fato.

![ ](https://github.com/ggdcdevel/TraballhoR1/blob/master/tela_search.png  "Twitter_Config")
***
**Criando Banco de Dados Local**

Após coleta dos twitters, resolvi gravar um banco de dados utilizando nó `Database Writer` e `Mysql Connector`. Resolvi gravar no banco para não ter que fazer requisições repetidas e otimizar as consultas aos dados. 

![ ](https://github.com/ggdcdevel/TraballhoR1/blob/master/banco.png  "twitter_bd")

**Processando os dados**

Para o processamento e tratamento de textos, iremos usar o termos mais frequentes e exibí-los em uma Nuvem de palavras. Neste processo, o nó `Ponctuation Erasure` remove todos os caracteres de pontuação do meu saco de palavras (linhas obtidas de cada twitter). O `Stop Word Filter` é o responsável por remover todos os termos do documento de entrada que correspondem com termos de uma lista (biblioteca de termos, preposições, no meu caso específico já utilizei a padrão do Knime). Com o `Row Filter`, foi excluído o próprio termo Python apenas para ele não polir a nuvem. O `Case Converter` transformou todos os termos em minúsculo. Por fim, o `Bag of Words Creator` separa em linhas cada um dos termos para a devida ação do nó `TF` que é quem verificar a frequência de cada palavra para que seja montada a nuvem.

**Cloud Tag**

![ ](https://github.com/ggdcdevel/TraballhoR1/blob/master/TagCloudTwitter.png "twitter_cloud_tag")

**Evolução de posts - twitters**

Para gerar alguns insights estatísticos utilizei o Google Sheets. Como eu tinha salvo os tweets em uma base de dados Mysql foi possível acessar essa base realizar alguns estudos sobre a base. Um estudo interessante que fiz é da porcentagem de Tweets por país. Se notarmos bem no gráfico os dois países em destaque são Estados Unidos e Australia. A australia aparece aqui porque Python também é uma espécie de cobra muito conhecida por lá e alguns tweets coletados eram referentes a serpente.


![ ]( https://github.com/ggdcdevel/TraballhoR1/blob/master/tweet.png "twitter_coluna")

Foquei o trabalho na aplicação das técnicas aprendidas e não no resultado da pesquisa. O knime é uma  a ferramenta muito interessante e intuitiva e possui muito material para pesquisar na internet, assim como o Python. Os principal desafio encontrado foi justamente a ideia do que pesquisar.

