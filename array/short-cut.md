# Ruby array shortcuts - "&:" and "&method"

## Call a method on every items with &:

```
[:foo, :bar].each do |item|
  item.to_s
end
```

**CAN BE REDUCED TO:**

```
[:foo, :bar].each(&:to_s)
```

## What if we want to call a method for each item in an array, and this item should be a parameter for this method?

```
[:foo, :bar].each do |item|
  puts(item)
end
```

**CAN BE REDUCED TO:**

```
[:foo, :bar].each(&method(:puts))
```
