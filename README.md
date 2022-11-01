# Investigating the complexity of algorithms by Big(O) notation
What is big o notation?
> We use big o to describe the performance of an algorithm and this helps us to determine if a given algorithm is scalable or not which basically means is this algorithm going to scale well as the input grows really large. In other words, certain operations can be more or less costly depending on what data structure we use. For instance, accessing an array element by its index is superfast but arrays have a fixed length and if you want to constantly add or remove items from them, they have to get resized and this will get costly as the size of our input grows very large. So if that's what we need to do then we have to use another data structure called a link list these data structures can grow or shrink very quickly but accessing a link list element by its index is slow so that's why you need to learn about the big o notation first before we can talk about various data structures.

## 💡 linear time complexity or O(1): 
 > When talking about the runtime complexity, we don't really care about the number of operations. Instead, we just want to know how much an algorithm slows down as the input grows larger. So in method below whether we have one or one million items our method runs in constant time, so we can simplify this by writing down o of one meaning constant time. In other words O(1) = O(2) = O(1,000,000)

```
 public void Log(string[] input)
 {
     System.Console.WriteLine(input[0]);
     System.Console.WriteLine(input[0]);
     System.Console.WriteLine(input[0]);
 }
       
```
