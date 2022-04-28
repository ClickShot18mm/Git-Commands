# SWAP TWO NUMBERS WITHOUT TEMP VARIBALE
```
a = a+b  
b = a-b  
a = a-b  
```

# FIND MAX & MIN NUMBER FROM AN ARRAY
If rather than comparing each number with max and min, we can first compare the numbers in pair with each other. Then compare the larger number with max and compare the smaller number with min. in this way the number of comparison for a pair of numbers are 3. So number of comparisons are 1.5 *n.  

```
$arr = [4, 3, 5, 1, 2, 6, 9, 2, 10, 11, 66];
function findMinMax($arr){
  $min=0;
  $max=0;
  
  /*If there is only one element then return it as min and max both*/
  if(count($arr) == 1){
      $min=$max=$arr[0];
  }
  
  /* If there are more than one elements, then initialize min and max*/
  if($arr[0] > $arr[1]){
      $max = $arr[0];
      $min = $arr[1];
  } else{
      $max = $arr[1];
      $min = $arr[0];
  }
  
  for($i=2; $i<count($arr); $i++){
      if($arr[$i] > $max)  
          $max = $arr[$i];  
      else if ($arr[$i] < $min)  
       	  $min = $arr[$i];  
  }
  
  print("Minimum element: " . $min . "\nMaximum element: " . $max);
}

findMinMax($arr);  
```
