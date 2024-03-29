# Investigating the complexity of algorithms by Big(O) notation

## What is Big O notation?
There are three Greek letters for representing different execution modes (Omega, Theta and Omicron-known as Big(O)).

Assume that there is a for loop to iterate through an array from one to seven in order to find a particular number.

![image](https://user-images.githubusercontent.com/45565026/199462065-d297b963-fc3d-4995-8b4a-e7989c01a54c.png)

- If we're looking for the number one, this is our best case with the least number of iterations through the array. (best case that is represented with the Greek letter Omega)
- 4 is the average case that is represented with the Greek letter theta
- 7 is the worst case that is represented with Omicron or O. So, technically, there is no best case or average case of Be(O). Big(O) is always going to be worst case.

In conclusion, when we measure Big O, we are always measuring the worst case.

## Why we need Big O Notation?
> We use big o to describe the performance of an algorithm and this helps us to determine if a given algorithm is scalable or not which basically means is this algorithm going to scale well as the input grows really large. In other words, certain operations can be more or less costly depending on what data structure we use. For instance, accessing an array element by its index is superfast but arrays have a fixed length and if you want to constantly add or remove items from them, they have to get resized and this will get costly as the size of our input grows very large. So if that's what we need to do then we have to use another data structure called a link list these data structures can grow or shrink very quickly but accessing a link list element by its index is slow so that's why you need to learn about the big o notation first before we can talk about various data structures.

## Time complexity vs Space complexity
> Most of the time, we have to do a trade-off between saving time and saving space. There are times where we have more space so we can use that to optimize an algorithm and make it faster and more scalable. But there are also times where we have limited space like when we build an app for a small mobile device. In this situation, we have to optimize for this space because scalability is not a big factor and only one user is going to use the application at that moment. 
> In below method, there is a loop variable named (i) and this is independent of the size of the input so whether our input array has ten or one million items, this method will only allocate some additional memory for this loop variable so it takes O(1) space. 
```
public void PrintStudentNames(string[] names)
{
    for (int i = 0; i < names.Length; i++) 
    {
        System.Console.WriteLine(i + names[i]);
    }
}

// => Space: O(1) 
```
> If we declare a string array and initialize it like below, so the length of this array is equal to the length of our input array. So the space complexity of this method is O(n) , the more items we have in our input array, the more space our method is going to take and this is indirect proportion to the size of our input array. 

```
public void PrintStudentNames(string[] names)
{
    string[] copy = new string[names.Length];

    for (int i = 0; i < names.Length; i++) 
    {
        System.Console.WriteLine(i + names[i]);
    }
}

// => Space: O(n) 
```

> when we talk about space complexity, we only look at the additional space that we should relative to the size of the input. We always have the input of size n, so we don't count it. we just analyze how much extra space we need to allocate for this algorithm. 

## Types of complexity
 ![image](https://user-images.githubusercontent.com/45565026/199409882-7e2756db-07df-4617-9e8b-03db18b10130.png)

## 💡 Constant time complexity or O(1): 
 > When talking about the runtime complexity, we don't really care about the number of operations. Instead, we just want to know how much an algorithm slows down as the input grows larger. So in method below whether we have one or one million items our method runs in constant time, so we can simplify this by writing down o of one meaning constant time. In other words O(1) = O(2) = O(1,000,000)

```
 public void Log(string[] input)
 {
     System.Console.WriteLine(input[0]);
     System.Console.WriteLine(input[0]);
     System.Console.WriteLine(input[0]);
 }

 => O(1)
```

![image](https://user-images.githubusercontent.com/45565026/199474481-bbf648fe-dce2-4228-813f-da9b3f9bd715.png)

O(1) is just a flat line across the bottom, it is the most efficient Big(O), nothing is more efficient than O(1).


## 💡 Linear time complexity or O(n): 
 > When we're iterating over all the items in an array and printing each item on the console, this is where the size of the input matters. If the array has a single item, we will have one print operation. In the same way, if we have a million items, obviously we will have a million print operations. Therefor the cost of this algorithm grows linearly and in direct correlation to the size of the input. So we represent the runtime complexity of this method using the big o of n.
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

 > If our method has two extra lines of code like below:
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

 > Now the runtime complexity of this method is O(1 + n + 1) which we can simplify to  O(2 + n). But when using the big o notation, we drop this constants because they don't really matter. Because if our array has one million inputs adding two extra operations doesn't really have a significant impact on the cost of our algorithm and the cost of our algorithm still increases linearly so we can simplify this by drop constants. What matters is that the cost of this algorithm increases linearly and in
direct proportion to the size of our input.

 > If we repeat the loop over an array twice separately, as shown below:
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

 > We dropped the constant because all we need is an approximation of the cost of this algorithm relative to its input size. So n or two n still represent a linear growths. 

 > If we change the inputs of method to two array with different sizes like this:

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

// => O(n + m) => O(n) because the runtime of this method increases linearly
```

 > In order to distinguish between these two inputs we could use different name (n and m). So the runtime complexity the method is going to be O(n + m) and we can simplify this to O(n) because the runtime of this method increases linearly.

![image](https://user-images.githubusercontent.com/45565026/199467791-338b179f-9293-498c-a4d1-6d0f4f0b4684.png)

O(n) is always going to be a straight line, it is proportional to the number of operations.

## 💡 Quadratic time complexity or O(n^2): 
> Suppose that we have a nested loop like this:

```
public void Log(string[] input)
 {
     for (int i = 0; i < input.Length; i++)  // => O(n)
     {
         for (int j = 0; j < input.Length; j++)  // => O(n)
         {
             System.Console.WriteLine("Some text");
         }
     }
 }
 
 // => O(n * n) => O(n^2)
```

> When we're iterating over the outer input array, we have O(n) then in each iteration once again we're iterating over all the items in this array. therefore the runtime complexity of this method is O(n * n) or O(n^2). This algorithm runs in quadratic time that gets slower than algorithms that run in O(n). As the input grow larger and larger algorithms that run in O(n^2) get slower and slower.


 > Now if we add another loop outside the previous like this:

```
 public void Log(string[] input)
{
    for (int k = 0; k < input.Length; k++)  // => O(n)
    {
        System.Console.WriteLine("Some text");
    }

    for (int i = 0; i < input.Length; i++)  // => O(n)
    {
        for (int j = 0; j < input.Length; j++)  // => O(n)
        {
            System.Console.WriteLine("Some text");
        }
    }
}

O(n + n^2) => O(n^2)
```
 > In O(n + n^2) expression n squared always grows faster than n. So the final time complexity is O(n^2). Becuase all we need is an approximation not an exact value so here we can drop n and conclude that this method runs in O(n^2).

 > If we add another loop to previous one like this:
```
public void Log(string[] input)
{
    for (int i = 0; i < input.Length; i++)  // => O(n)
    {
        for (int j = 0; j < input.Length; j++)  // => O(n)
        {
            for (int k = 0; k < input.Length; k++)  // => O(n)
            {
                System.Console.WriteLine("Some text");
            }
        }
    }
}
 // => O(n * n * n) = O(n^3) => O(n^2)
```

 > Now the runtime complexity is O(n^3) that gets far slower than an algorithm with O(n^2).

![image](https://user-images.githubusercontent.com/45565026/199470349-ffa891da-75f3-424c-a110-2682dee1e92f.png)

 > If we had two sets of code that accomplish the same task and one was O(n^2) and the other was O(n), the O(n) code is better because it's going to complete the task in fewer operations. O(n^2) is generally considered inefficient code, if you can write your code in a way that is going to become O(n), then it is going to be much more efficient.


## 💡 Logarithmic time complexity or O(log n): 
 > An algorithm that runs in logarithmic time is more efficient and more scalable than an algorithm that runs in linear or quadratic time. Supposed that we have an array of sorted number from one to ten and we want to find the number ten. One way to find the ten is to iterate over this array using a four loop going forward until we find the ten. This is called the linear search because it runs in linear time in the worst case scenario. In other word, if the number we're looking for is at the end of our array we have to inspect every cell in this array to find the target number so the more items we have the longer this operation is going to take. So the run time of this algorithm increases linearly and in direct proportion with the size of our array. 
 > 
 > But when we use binary search, the time complexity of the algorithm becomes logarithmic, which is so faster than linear one. 
 > Assume that there is a sorted array and we're going to look for the number one
 
 ![image](https://user-images.githubusercontent.com/45565026/200105226-e1796ba4-6619-43db-aab3-f09ffd662322.png)

 > In order to search the array, cut it in half. Because we are sure the answer is not in the second half. So we don't even have to look at any of those numbers and that may not seem like a big deal when you have an array with eight items in it. But if you have an array with a million items in it, you just made it where you have a half a million items that you don't have to look at.


> Step 1:


![image](https://user-images.githubusercontent.com/45565026/200106126-d8b087f4-08bc-41a2-9be1-a98891b4ab2d.png)

> So then we do this again and again.

> Step 2:

![image](https://user-images.githubusercontent.com/45565026/200106421-b7f20786-d18a-444f-a1e4-ebb8f0c30694.png)

> Step 3:

![image](https://user-images.githubusercontent.com/45565026/200106441-3f5fcf20-d70d-4132-a421-393f01f2af77.png)

> And now we have found the number one.

![image](https://user-images.githubusercontent.com/45565026/200106469-8e4eaebf-9a90-48d5-98c3-4a8dcf8e7062.png)


 > So in every step we're essentially narrowing down our search by half with this algorithm. If we have one million items in our array we can find the target item with the maximum of 19 comparisons. This is a technique called divide and conquer. 

> We had eight items in the array and in 3 steps we find the answer. So when n is 8, O(log(n)) or log(8) means 2 to the what power is 8. or How many times would you have to cut this number in half to get down to one item?

![image](https://user-images.githubusercontent.com/45565026/200107378-0ed02391-a51e-47fa-b0d4-e29c19bc5e87.png)

> The answer of the above equation is 3, which is the number the steps we have to take to find the answer. To put it another way, if we take the number eight and we repeatedly cut it in half, we divide it by two, how many times do we have to divide it by two to get down to one item? that is three times.

> So if you had an array with a billion items in it and you were going to iterate through that array linearly to find something and say what you were looking for was the last item, you would have to look at a billion items to find it. But if you use divide and conquer, you could find any item in that array in thirty one steps.

![image](https://user-images.githubusercontent.com/45565026/200107905-17bebbe1-8359-425b-9185-2d6247482c74.png)

> O(log(n)) is very flat, not as flat as O(1) and very efficient compared to O(n) and O(n^2).

![image](https://user-images.githubusercontent.com/45565026/200108045-d4661b86-5d33-47a8-ba6e-c8a7ae975b47.png)


## 💡 Exponential time complexity or O(2^n): 
 > The exponential growth is the opposite of the logarithmic growth. The logarithmic curve slows down as the input size growth but exponential curve growths faster and faster. Therefore an algorithm that runs in exponential time is not scalable at all and it will become very slow very soon.
