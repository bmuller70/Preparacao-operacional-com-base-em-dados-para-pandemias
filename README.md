# Preparacao operacional com base em dados para pandemias
![](https://www.mackenzie.br/fileadmin/ARQUIVOS/Public/top/midias_noticias/noticias/2019/NOT%C3%8DCIAS_GEST%C3%83O_DE_CONTE%C3%9ADO_2019/coronavirus-4817450_1920.jpg)


### Colaboradores
@bmuller70/[Bruno Müller](https://www.linkedin.com/in/bruno-muller-335630196/) :computer:		

@marialuisamartins/[Maria Luisa Martins Brasil](https://www.linkedin.com/in/marialuisamartinsb/) :computer:	

@marialmrt97/[Maria Luiza Martins](https://www.linkedin.com/in/maria-luiza-martins-4115b213b/) :computer:	

@Pahmxx/[Phaola Oliveira Silva](https://www.linkedin.com/in/phaola-oliveira/) :computer:

## Introdução

Para construção dessa análise partimos da perspectiva de um hospital público localizado na cidade de São Paulo que opera no regime 100% SUS. Como instituição, buscamos observar os dados com objetivo de que em caso de uma nova pandemia de um vírus 
com características semelhantes a COVID-19 o hospital possa estar preparado a nível operacional para enfrentar essa situação. Frente a situações ocorridas, como no caso de Manaus , entendemos que o preparo operacional é fundamental para que o hospital 
consiga garantir uma capacidade de resposta eficiente e segura. A experiência adquirida durante a pandemia de COVID-19 destacou a importância de que medidas rápidas e integradas, tanto na gestão de recursos de saúde quanto no atendimento à população sejam pensadas de forma preventiva. 

## Método e Organização da Base

Para construir uma visão abrangente e integrada do cenário da pandemia em seus aspectos sociais,sintomatológicos e financeiros fizemos o uso da base de dados PNAD COVID-2019 a base disponibiliza os dados de pesquisas realizadas no ano de 2020 entre os meses de Maio e Novembro. 
Os meses selecionados para análise foram de Julho, Agosto e Setembro, a escolha desse período se deu por serem os meses mais iniciais da pandemia onde já haviam testes, assim foi possível filtrar os dados pelos seus resultados fazendo uma
análise mais assertiva sobre as características dos grupos. Também foram selecionados um grupo de itens que fazem parte do questionário realizado na pesquisa que servem de forma concisa ao nosso objetivo, de forma que 20 questões tratam sobre as características clínicas dos sintomas, econômicas da população e de comportamentos e outras auxiliares sobre características de distribuição geográfica.

### Colunas
```
    'v1013' : 'mes', #!
    'UF' : 'estado', #!
    'v1008': 'domicilio', #int de 1 a 14
    'v1016': 'entrevista_domicilio', #int 1 a 99
    'v1022': 'domicilio_urbano_rural',
    'v1023': 'tipo_area', #!
    'v1030': 'projecao_populacao',
    'B0014': 'dificuldade_respiracao', #!
    'B00111': 'perda_olfato_paladar', #!
    'B0012': 'tosse', #!
    'B002': 'estabelecimento_saude', ## Foi a algum estabelecimento? #!
    'B0042': 'pronto_socorro_pub', ## pronto socorro que buscou atendimento? #!
    'B0043': 'hospital_sus', ## local que buscou atendimento foi um hospital do sus? #!
    'B0045': 'pronto_socorro_priv', ## pronto socorro privado ou das forças armadas? #!
    'B0046': 'hospital_privado', # buscou hospital particular #!
    'B005': 'internação', #!
    'B008':'Teste_Covid', #!
    'B011': 'restricao_contato', #!
    'C001': 'trabalhou_min_1h',
    'C002': 'afastamento_trabalho',
    'C013': 'trabalho_remoto',
    'C004': 'trabalho_remunerado', #!
    'B007': 'plano_saude', #!
    'A002': 'idade', #!
    'F001': 'situacao_domicilio', #!
    'B009A': 'exame_swab',#!
    'B009B': 'resultado_swab',#!
    'B009C': 'exame_sangue_dedo', #!
    'B009D': 'resultado_sangue_dedo', #!
    'B009E': 'exame_sangue_braco', #!
    'B009F': 'resultado_sangue_braco' #!
```
### Utilização PySpark 

A concatenação dos dados dos 3 meses selecionados resultou em mais de 1 milhão de registros, o que exigiu o uso do PySpark devido ao grande volume de dados. O PySpark é ideal para manipulação de grandes datasets, permitindo operações distribuídas e paralelizadas de forma eficiente. Ele foi escolhido para processar e analisar a base de dados sem comprometer a performance, garantindo que o processamento em larga escala fosse otimizado.
Optamos pelo PySpark, considerando que os hospitais públicos frequentemente enfrentam restrições orçamentárias e já contam com infraestrutura on-premise. Nesse cenário, o PySpark se destaca não apenas pela eficiência no processamento, mas também por ser uma solução de código aberto, garantindo transparência em sua utilização. Além disso, sua adoção contribui para a redução de custos relacionados ao uso de serviços de nuvem de terceiros e assegura a confidencialidade dos dados dos pacientes, preservando a soberania nacional. Ao evitar o armazenamento dos dados de saúde em servidores de outros países, protegemos a privacidade e segurança da população.
