## Load text file
  
      val lines = sc.textFile("filename.txt")

## Transformation -
      
  * map ()
    
        val newline = lines.map(line => (line, "length of line is " + line.length()))
      
  * filter ()
  
        val newline = lines.filter(line => line.length() > 0)
      
  * flatMap () - flatMap is useful in scenarios where multiple output from transformation is expected. In this case, flatMap will combine                  output from multiple iterators and present as one. For example, to split a block of text by words, all the lines can be                    passed through flatMap and using split(" ") method. Instead of returning iterator for each line , flatmap will return                      one single iterator containing all the words.
  
        val words = lines.flatMap(line => line.split(" "))
        
   * Distinct() - Return a new dataset that contains the distinct elements of the source dataset. Resource expensive.
   
   * groupByKey([numTasks])
   
   
   * reduceByKey(func, [numTasks])
   
   
   * aggregateByKey(zeroValue)(mergingFn, CombiningFn, [numTasks])
   
   
   * combineByKey(combiner, mergingFn, CombiningFn, [numTasks])
   
   
   * sortByKey([ascending], [numTasks]) -	When called on a dataset of (K, V) pairs where K implements Ordered, returns a dataset of 
                                          (K,V) pairs sorted by keys in ascending or descending order, as specified in the boolean                                                  ascending argument.

   * join(otherDataset, [numTasks])	- When called on datasets of type (K, V) and (K, W), returns a dataset of (K, (V, W)) pairs with all                                       pairs of elements for each key. Outer joins are supported through leftOuterJoin, rightOuterJoin,                                         and fullOuterJoin.

   * cogroup(otherDataset, [numTasks]) -	When called on datasets of type (K, V) and (K, W), returns a dataset of (K, (Iterable<V>,                                               Iterable<W>)) tuples. This operation is also called groupWith.
  
   * coalesce(numPartitions) - Decrease the number of partitions in the RDD to numPartitions. Useful for running operations more                                        efficiently after filtering down a large dataset.
   
   * repartition(numPartitions) - Reshuffle the data in the RDD randomly to create either more or fewer partitions and balance it across                                   them. This always shuffles all data over the network
  



    
