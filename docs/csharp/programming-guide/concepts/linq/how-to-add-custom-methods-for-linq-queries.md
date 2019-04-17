---
title: 'Instrukcje: Dodawanie metod niestandardowych do kwerend LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: 5aca346c182d63967f02a7f5444c5fd6d86ae3d1
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610902"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="5fcdf-102">Instrukcje: Dodawanie metod niestandardowych do kwerend LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="5fcdf-102">How to: Add Custom Methods for LINQ Queries (C#)</span></span>

<span data-ttu-id="5fcdf-103">Można rozszerzyć zbiór metod, które służy do zapytań LINQ, dodając metody rozszerzenia umożliwiające <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="5fcdf-104">Na przykład oprócz standardowych średnia lub maksymalna operacje, możesz utworzyć niestandardowe metody agregacji do obliczenia pojedynczej wartości z sekwencji wartości.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="5fcdf-105">Można również utworzyć metodę, która działa jako filtr niestandardowy lub przekształcenia danych określonego dla sekwencji wartości i zwraca nową sekwencję.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="5fcdf-106">Przykłady takich metod <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, i <xref:System.Linq.Enumerable.Reverse%2A>.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="5fcdf-107">Po rozszerzeniu <xref:System.Collections.Generic.IEnumerable%601> interfejsu swoje niestandardowe metody można zastosować do kolekcji wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="5fcdf-108">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="5fcdf-108">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="5fcdf-109">Dodawanie metody agregacji</span><span class="sxs-lookup"><span data-stu-id="5fcdf-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="5fcdf-110">Metoda agregacji oblicza pojedynczej wartości z zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="5fcdf-111">LINQ zapewnia kilka metod agregacji, takich jak <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="5fcdf-112">Metoda agregacji można utworzyć, dodając metodę rozszerzenia, aby <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="5fcdf-113">Poniższy przykład kodu pokazuje, jak utworzyć metodę rozszerzenia o nazwie `Median` można obliczyć mediany sekwencji liczb typu `double`.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```csharp
public static class LINQExtension
{
    public static double Median(this IEnumerable<double> source)
    {
        if (source.Count() == 0)
        {
            throw new InvalidOperationException("Cannot compute median for an empty set.");
        }

        var sortedList = from number in source
                         orderby number
                         select number;

        int itemIndex = (int)sortedList.Count() / 2;

        if (sortedList.Count() % 2 == 0)
        {
            // Even number of items.
            return (sortedList.ElementAt(itemIndex) + sortedList.ElementAt(itemIndex - 1)) / 2;
        }
        else
        {
            // Odd number of items.
            return sortedList.ElementAt(itemIndex);
        }
    }
}
```

<span data-ttu-id="5fcdf-114">Chcesz wywołać tę metodę rozszerzenia dla dowolnej kolekcji wyliczalny tak samo jak inne metody agregacji z <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="5fcdf-115">Poniższy przykład kodu pokazuje sposób użycia `Median` metodę dla tablicy typu `double`.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-115">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
*/
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="5fcdf-116">Przeciążenie to metoda agregacji do akceptowania różnych typów</span><span class="sxs-lookup"><span data-stu-id="5fcdf-116">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="5fcdf-117">Metoda agregacji można przeciążać tak, aby go akceptuje sekwencje różnych typów.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-117">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="5fcdf-118">Jest standardowego podejścia do tworzenia przeciążenia dla każdego typu.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-118">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="5fcdf-119">Innym rozwiązaniem jest tworzenie przeciążenia, które będą typu ogólnego i przekonwertować go do określonego typu za pomocą delegata.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-119">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="5fcdf-120">Można także połączyć oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-120">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="5fcdf-121">Aby utworzyć przeciążenia dla każdego typu</span><span class="sxs-lookup"><span data-stu-id="5fcdf-121">To create an overload for each type</span></span>

<span data-ttu-id="5fcdf-122">Można utworzyć określonego przeciążenia dla każdego typu, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-122">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="5fcdf-123">Poniższy przykład kodu pokazuje przeciążenie `Median` metodę `integer` typu.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-123">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="5fcdf-124">Teraz można wywołać `Median` przeciążenia dla obu `integer` i `double` typów, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="5fcdf-124">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
int[] numbers2 = { 1, 2, 3, 4, 5 };

var query2 = numbers2.Median();

Console.WriteLine("int: Median = " + query2);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
 Integer: Median = 3
*/
```

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="5fcdf-125">Aby utworzyć przeciążenie ogólne</span><span class="sxs-lookup"><span data-stu-id="5fcdf-125">To create a generic overload</span></span>

<span data-ttu-id="5fcdf-126">Można również utworzyć przeciążenie, które akceptuje sekwencji ogólnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-126">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="5fcdf-127">Tego przeciążenia przyjmuje jako parametr delegata i używa go w celu konwersji sekwencji obiektów typu ogólnego dla określonego typu.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-127">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="5fcdf-128">Poniższy kod pokazuje przeciążenie `Median` metody, która przyjmuje <xref:System.Func%602> delegować jako parametr.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-128">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="5fcdf-129">Ten delegat przyjmuje obiekt ogólny typ T i zwraca obiekt typu `double`.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-129">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="5fcdf-130">Teraz można wywołać `Median` metodę sekwencji obiektów dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-130">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="5fcdf-131">Jeśli typ nie ma swój własny przeciążenia metody, należy przekazać parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-131">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="5fcdf-132">W języku C#, w tym celu można użyć wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-132">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="5fcdf-133">Ponadto tylko w Visual Basic Jeśli używasz `Aggregate` lub `Group By` klauzuli zamiast wywołania metody które można przekazać dowolna wartość lub wyrażenie, który znajduje się w zakresie tej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-133">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="5fcdf-134">Poniższy przykład kodu pokazuje sposób wywoływania `Median` Metoda tablicy liczb całkowitych i tablicę ciągów.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-134">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="5fcdf-135">Dla ciągów mediana dla długości ciągów w tablicy jest obliczana.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-135">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="5fcdf-136">W przykładzie pokazano sposób przekazywania <xref:System.Func%602> parametru, aby delegować `Median` metody dla każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-136">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

```csharp
int[] numbers3 = { 1, 2, 3, 4, 5 };

/*
  You can use the num=>num lambda expression as a parameter for the Median method
  so that the compiler will implicitly convert its value to double.
  If there is no implicit conversion, the compiler will display an error message.
*/

var query3 = numbers3.Median(num => num);

Console.WriteLine("int: Median = " + query3);

string[] numbers4 = { "one", "two", "three", "four", "five" };

// With the generic overload, you can also use numeric properties of objects.

var query4 = numbers4.Median(str => str.Length);

Console.WriteLine("String: Median = " + query4);

/*
 This code produces the following output:

 Integer: Median = 3
 String: Median = 4
*/
```

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="5fcdf-137">Dodawanie metody, które zwraca kolekcję</span><span class="sxs-lookup"><span data-stu-id="5fcdf-137">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="5fcdf-138">Możesz rozszerzyć <xref:System.Collections.Generic.IEnumerable%601> interfejs za pomocą metody niestandardowe zapytanie, która zwraca sekwencję wartości.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-138">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="5fcdf-139">W tym przypadku metoda musi zwracać kolekcję typu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-139">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="5fcdf-140">Takie metody może służyć do zastosowania przekształcenia danych lub filtrów do sekvence hodnot.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-140">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="5fcdf-141">Poniższy przykład pokazuje, jak utworzyć metodę rozszerzenia o nazwie `AlternateElements` zwracającego każdy inny element w kolekcji, począwszy od pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="5fcdf-141">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

```csharp
// Extension method for the IEnumerable<T> interface.
// The method returns every other element of a sequence.

public static IEnumerable<T> AlternateElements<T>(this IEnumerable<T> source)
{
    List<T> list = new List<T>();

    int i = 0;

    foreach (var element in source)
    {
        if (i % 2 == 0)
        {
            list.Add(element);
        }

        i++;
    }

    return list;
}
```

<span data-ttu-id="5fcdf-142">Chcesz wywołać tę metodę rozszerzenia dla dowolnego wyliczalny kolekcji, tak samo, jak możesz wywołać innych metod z <xref:System.Collections.Generic.IEnumerable%601> interfejsu, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="5fcdf-142">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

```csharp
string[] strings = { "a", "b", "c", "d", "e" };

var query = strings.AlternateElements();

foreach (var element in query)
{
    Console.WriteLine(element);
}
/*
 This code produces the following output:

 a
 c
 e
*/
```

## <a name="see-also"></a><span data-ttu-id="5fcdf-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fcdf-143">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="5fcdf-144">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="5fcdf-144">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
