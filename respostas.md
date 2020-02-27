# Respostas Desafio Semantix

__Qual​ o objetivo​​ do​ comando__ ___cache___ __em Spark?__

As operações executadas pelo Spark são todas _lazy_ e, por isso, são repetidas a cada acesso aos dados que se faça necessário. O método _cache_ permite armazenar esses dados dentro de um cluster em memória, de modo que os dados possam ser acessados de modo muito mais rápido. No entanto, o comportamento _lazy_ usual do ambiente Spark (isto é, sucessivas leituras dos dados) é utilizado normalmente caso não haja memória suficiente para os dados armazenados via _cache_.

__O mesmo​ código implementado em Spark é normalmente mais rápido​ que a implementação​ equivalente em MapReduce. Por​ quê?__

Lorem ipsum

__Qual é a função do__ ___SparkContext​_____?__

Lorem ipsum

__Explique com suas palavras o que é__ ___Resilient Distributed Datasets___ __(RDD).__

Lorem ipsum

___GroupByKey___ __é menos eficiente que__ ___reduceByKey___ __em grandes datasets. Por quê?__

Lorem ipsum
