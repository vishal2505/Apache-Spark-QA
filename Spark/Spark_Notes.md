## Load text file
  
      val lines = sc.textFile("filename.txt")

## Transformation -
      
  * map ()
    
        val newline = lines.map(line => (line, "length of line is " + line.length()))
      
  * filter ()
  
        val newline = lines.filter(line => line.length() > 0)
      
  * flatMap () - flatMap is useful in scenarios where multiple output from transformation is expected. In this case, flatMap will combine     output from multiple iterators and present as one. For example, to split a block of text by words, all the lines can be passed thru       flatMap and using split(" ") method. Instead of returning iterator for each line , flatmap will return one single iterator containing     all the words.
  
        val words = lines.flatMap(line => line.split(" "))
        
   * Distinct() - Return a new dataset that contains the distinct elements of the source dataset. Resource expensive.
   * groupByKey([numTasks])
   * reduceByKey(func, [numTasks])
   * aggregateByKey(zeroValue)(mergingFn, CombiningFn, [numTasks])
   * combineByKey(combiner, mergingFn, CombiningFn, [numTasks])
  



    
