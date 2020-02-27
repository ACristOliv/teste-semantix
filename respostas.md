# Respostas Desafio Semantix

__Qual​ o objetivo​​ do​ comando `cache` em Spark?__

As operações executadas pelo Spark são todas _lazy_ e, por isso, são repetidas a cada acesso aos dados que se faça necessário. O método _cache_ permite armazenar esses dados dentro de um cluster em memória, de modo que os dados possam ser acessados de modo muito mais rápido. No entanto, o comportamento _lazy_ usual do ambiente Spark (isto é, sucessivas leituras dos dados) é utilizado normalmente caso não haja memória suficiente para os dados armazenados via _cache_.

__O mesmo​ código implementado em Spark é normalmente mais rápido​ que a implementação​ equivalente em MapReduce. Por​ quê?__

O MapReduce utiliza fontes de armazenamento de dados externas para conseguir implementar o paralelismo entre duas ou mais _tasks_ simultâneas, enquanto o Spark faz executa operações _lazy_ que podem ser salvas em _cache_ na memória. Como operações de entrada e saída entre um sistema de arquivos e a memória do computador costumam demandar um tempo muito maior do que o tempo de busca na memória RAM e seu respectivo processamento, o tempo necessário para a execução de um conjunto de tarefas costuma ser muito maior pelo MapReduce que pelo Spark.

__Qual é a função do `SparkContext`?__

O _SparkContext_ é a camada mais alta de abstração dentro do ambiente Spark. Ele monitora tanto o sistema gerenciador de leitura de arquivos quanto a máquina virtual que gerencia todas as operações permitidas para os RDDs.

__Explique com suas palavras o que é `Resilient Distributed Datasets` (RDD).__

Os resilient distributed dataset (RDDs) são a estrutura de dados básica do ecossistema Spark. São eles que armazenam os dados advindos de um dataset comum em memória, para que possam ser operados conforme os métodos permitidos. São os RDDs também que possibilitam ao Spark trabalhar sob o paradigma da computação paralela.

__`GroupByKey` é menos eficiente que `reduceByKey` em grandes datasets. Por quê?__

O método `reduceByKey()` é mais eficiente que `groupByKey()` para grandes datasets porque, com o primeiro, os dados de mesma chave são combinados entre si antes de serem randomizados. Assim, a grosso modo, a diferença de performance entre os dois métodos cresce polinomialmente de acordo com o tamanho do dataset.

__Explique o que o código Scala abaixo faz.__

```scala
val​ textFile = sc.textFile("hdfs://...")
val counts = textFile.flatMap(line => line.split(""))
        .map​(word => (word​, 1))
        .reduceByKey(_+_)
counts.saveAsTextFile("hdfs://...")
```
