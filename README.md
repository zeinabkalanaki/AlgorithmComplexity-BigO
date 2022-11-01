# Investigating the complexity of algorithms by Big(O) notation
What is big o notation?
> We use big o to describe the performance of an algorithm and this helps us to determine if a given algorithm is scalable or not which basically means is this algorithm going to scale well as the input grows really large. In other words, certain operations can be more or less costly depending on what data structure we use. For instance, accessing an array element by its index is superfast but arrays have a fixed length and if you want to constantly add or remove items from them, they have to get resized and this will get costly as the size of our input grows very large. So if that's what we need to do then we have to use another data structure called a link list these data structures can grow or shrink very quickly but accessing a link list element by its index is slow so that's why you need to learn about the big o notation first before we can talk about various data structures.

## 💡 Constant time complexity or O(1): 
 > When talking about the runtime complexity, we don't really care about the number of operations. Instead, we just want to know how much an algorithm slows down as the input grows larger. So in method below whether we have one or one million items our method runs in constant time, so we can simplify this by writing down o of one meaning constant time. In other words O(1) = O(2) = O(1,000,000)

```
 public void Log(string[] input)
 {
     System.Console.WriteLine(input[0]);
     System.Console.WriteLine(input[0]);
     System.Console.WriteLine(input[0]);
 }
       
```

## 💡 linear time complexity or O(n): 
 > 
When we're iterating over all the items in an array and printing each item on the console, this is where the size of the input matters. If the array has a single item, we will have one print operation. In the same way, if we have a million items, obviously we will have a million print operations. Therefor the cost of this algorithm grows linearly and in direct correlation to the size of the input. So we represent the runtime complexity of this method using the big o of n.
n represents the size of the input and as n grows the cost of this algorithm also grows linearly.

```
 public void Log(string[] input)
 {
     for (int i = 0; i < input.Length; i++)
     {
         System.Console.WriteLine(input[i]);
     }
 }
 
 => O(n)
```

If our method has two extera lines of code like below:
```
public void Log(string[] input)
{
    System.Console.WriteLine("Hello"); // => O(1)
    for (int i = 0; i < input.Length; i++)  // => O(n)
    {
        System.Console.WriteLine(input[i]);
    }
    System.Console.WriteLine("Bye");  // => O(1)
}

// =>  O(1 + n + 1) = O(2 + n) => O(n)
```

Now the runtime complexity of this method is O(1 + n + 1) which we can simplify to  O(2 + n). But when using the big o notation, we drop this constants because they don't really matter. Because if our array has one million inputs adding two extra operations doesn't really have a significant impact on the cost of our algorithm and the cost of our algorithm still increases linearly so we can simplify this by drop constants. What matters is that the cost of this algorithm increases linearly and in
direct proportion to the size of our input.

If we repeat the loop over an array twice sperately, as shown below:
```
public void Log(string[] input)
{
    for (int i = 0; i < input.Length; i++)  // => O(n)
    {
        System.Console.WriteLine(input[i]);
    }

    for (int i = 0; i < input.Length; i++)  // => O(n)
    {
        System.Console.WriteLine(input[i]);
    }
}

// =>  O(n + n) = O(2n) => O(n)
```

We dropped the constant because all we need is an approximation of the cost of this algorithm relative to its input size. So n or two n still represent a linear growths. 

If we change the inputs of method to two array with diffirent sizes like this:

```
public void Log(string[] input1, string[] input2)
{
    for (int i = 0; i < input1.Length; i++)  // => O(n)
    {
        System.Console.WriteLine(input1[i]);
    }

    for (int i = 0; i < input2.Length; i++)  // => O(m)
    {
        System.Console.WriteLine(input2[i]);
    }
}

// => O(n + m) => => O(n)
```

In order to distinguish between these two inputs we could use different name (n and m). So the runtime complexity the method is going to be O(n + m) and we can simplify this to O(n) because the runtime of this method increases linearly.
