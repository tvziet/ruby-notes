# Array methods

## each
- Call a block once for every given element in  an array.
- Return the original array.
```
result = [1, 2, 3].each do |number|
    puts "hi #{number}"
end

==========
hi 1
hi 2
hi 3
=> [1, 2, 3]
```

## map
- Return a new array with the result of executing the block once for every element in original array.
```
result = [1, 2, 3, 4].map do |number|
    number + 2
end

==========
=> result = [3, 4, 5]
```

## flat_map
- Loop nested array.
- Example 1:
```
result = []
[1, 2, 3].each do |number|
  ['a', 'b', 'c'].each do |letter|
    result << "#{number}:#{letter}"
  end
end

==========
=> result = ["1:a", "1:b", "1:c", "2:a", "2:b", "2:c", "3:a", "3:b", "3:c"]
```

- Example 1 with **flat_map** method:
```
result = [1,2,3].flat_map do |number|
  ['a', 'b', 'c'].map do |letter|
    "#{number}:#{letter}"
  end
end

==========
=> result = ["1:a", "1:b", "1:c", "2:a", "2:b", "2:c", "3:a", "3:b", "3:c"]
```

## select
- Override an original array containing all elements for which the given block returns a true value.
```
result = [1, 2, 3, 4].select do |number|
  number.even?
end

==========
=> result = [2,4]
```

## detect
- Return the first entry for which your block evaluates to true.
```
result = [1, 2, 3, 4].detect do |number|
  number.even?
end

==========
=> result = 2
```

- If block never evaluates to true, **detect** will return nil.
```
result = [1, 3, 5, 7].detect do |number|
  number.even?
end

==========
=> result = nil
```

## reject
```
result = [1, 2, 3, 4].reject do |number|
  number.even?
end

==========
=> result = [1, 3]
```
WITH:
```
result = [1, 2, 3, 4].select do |number|
  number.even?
end

==========
=> result = [2,4]
```
## count
- Count the number of elements in array.
```
[1, 1, 2, 2, 3, 3].count do |number|
  number.odd?
end

==========
=> result = 4
```

- Short syntax(passing a proc) **(For single methods without argument)**:
```
[1, 1, 2, 2, 3, 3].count(&:odd?)
```
==========
=> result = 4

## partition
- Separate single array into two arrays.
```
even, odd = [1, 2, 3, 4].partition do |number|
  number.even?
end

==========
=> even = [2, 4] and odd = [1, 3]
```

## with_index

## chaining
```
result = [1, 2, 3, 4].map{|n| n + 2}.select{|n| n.even?}.reject{|n| n == 6}.map{|n| "hi #{n}"} 

==========
=> result = ["hi 4"]
```