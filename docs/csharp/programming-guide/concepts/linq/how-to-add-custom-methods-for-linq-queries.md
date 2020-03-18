---
title: Jak dodać metody niestandardowe dla zapytań LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: e16175d3332b6ce36458eaa78af093e4f8772723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141471"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="e8b5e-102">Jak dodać metody niestandardowe dla zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="e8b5e-102">How to add custom methods for LINQ queries (C#)</span></span>

<span data-ttu-id="e8b5e-103">Można rozszerzyć zestaw metod, które można użyć dla kwerend LINQ, <xref:System.Collections.Generic.IEnumerable%601> dodając metody rozszerzenia do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="e8b5e-104">Na przykład oprócz standardowych operacji średniej lub maksymalnej można utworzyć niestandardową metodę agregacji, aby obliczyć pojedynczą wartość z sekwencji wartości.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="e8b5e-105">Można również utworzyć metodę, która działa jako filtr niestandardowy lub przekształcenie określonych danych dla sekwencji wartości i zwraca nową sekwencję.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="e8b5e-106">Przykładami takich metod <xref:System.Linq.Enumerable.Distinct%2A>są <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.Reverse%2A>i .</span><span class="sxs-lookup"><span data-stu-id="e8b5e-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="e8b5e-107">Po rozszerzeniu <xref:System.Collections.Generic.IEnumerable%601> interfejsu, można zastosować metody niestandardowe do dowolnej kolekcji wyliczania.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="e8b5e-108">Aby uzyskać więcej informacji, zobacz [Metody rozszerzenia](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e8b5e-108">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="e8b5e-109">Dodawanie metody agregowanej</span><span class="sxs-lookup"><span data-stu-id="e8b5e-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="e8b5e-110">Metoda agregująca oblicza pojedynczą wartość z zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="e8b5e-111">LINQ udostępnia kilka metod <xref:System.Linq.Enumerable.Average%2A>agregacji, w tym , <xref:System.Linq.Enumerable.Min%2A>i <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="e8b5e-112">Można utworzyć własną metodę agregacji, <xref:System.Collections.Generic.IEnumerable%601> dodając metodę rozszerzenia do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="e8b5e-113">W poniższym przykładzie kodu pokazano, `Median` jak utworzyć metodę rozszerzenia o `double`nazwie obliczyć medianę dla sekwencji liczb typu .</span><span class="sxs-lookup"><span data-stu-id="e8b5e-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

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

<span data-ttu-id="e8b5e-114">Ta metoda rozszerzenia dla każdej kolekcji wyliczania w taki sam <xref:System.Collections.Generic.IEnumerable%601> sposób można wywołać inne metody agregacji z interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="e8b5e-115">W poniższym przykładzie kodu `Median` pokazano, jak `double`używać metody dla tablicy typu .</span><span class="sxs-lookup"><span data-stu-id="e8b5e-115">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="e8b5e-116">Przeciążenie metody agregacji do akceptowania różnych typów</span><span class="sxs-lookup"><span data-stu-id="e8b5e-116">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="e8b5e-117">Można przeciążać metodę agregacji, tak aby akceptuje sekwencje różnych typów.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-117">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="e8b5e-118">Standardowe podejście jest, aby utworzyć przeciążenie dla każdego typu.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-118">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="e8b5e-119">Innym podejściem jest utworzenie przeciążenia, które zajmie typ ogólny i przekonwertować go na określony typ przy użyciu pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-119">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="e8b5e-120">Można również połączyć oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-120">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="e8b5e-121">Aby utworzyć przeciążenie dla każdego typu</span><span class="sxs-lookup"><span data-stu-id="e8b5e-121">To create an overload for each type</span></span>

<span data-ttu-id="e8b5e-122">Można utworzyć określone przeciążenie dla każdego typu, który ma być obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-122">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="e8b5e-123">Poniższy przykład kodu pokazuje przeciążenie `Median` metody `integer` dla typu.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-123">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="e8b5e-124">Teraz można wywołać `Median` przeciążenia dla obu `integer` i `double` typów, jak pokazano w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e8b5e-124">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

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

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="e8b5e-125">Aby utworzyć ogólne przeciążenie</span><span class="sxs-lookup"><span data-stu-id="e8b5e-125">To create a generic overload</span></span>

<span data-ttu-id="e8b5e-126">Można również utworzyć przeciążenie, które akceptuje sekwencję obiektów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-126">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="e8b5e-127">To przeciążenie przyjmuje delegata jako parametr i używa go do konwersji sekwencji obiektów typu ogólnego do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-127">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="e8b5e-128">Poniższy kod pokazuje przeciążenie `Median` metody, <xref:System.Func%602> która przyjmuje delegata jako parametr.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-128">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="e8b5e-129">Ten pełnomocnik przyjmuje obiekt typu ogólnego T i `double`zwraca obiekt typu .</span><span class="sxs-lookup"><span data-stu-id="e8b5e-129">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="e8b5e-130">Teraz można wywołać `Median` metodę sekwencji obiektów dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-130">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="e8b5e-131">Jeśli typ nie ma własnego przeciążenia metody, należy przekazać parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-131">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="e8b5e-132">W języku C#, można użyć wyrażenia lambda w tym celu.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-132">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="e8b5e-133">Ponadto tylko w języku Visual `Aggregate` Basic, jeśli używasz lub `Group By` klauzuli zamiast wywołania metody, można przekazać dowolną wartość lub wyrażenie, które znajduje się w zakresie tej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-133">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="e8b5e-134">Poniższy przykładowy kod pokazuje, `Median` jak wywołać metodę dla tablicy liczb całkowitych i tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-134">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="e8b5e-135">W przypadku ciągów obliczana jest mediana długości ciągów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-135">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="e8b5e-136">W przykładzie pokazano, <xref:System.Func%602> jak przekazać `Median` parametr delegata do metody dla każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-136">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

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

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="e8b5e-137">Dodawanie metody, która zwraca kolekcję</span><span class="sxs-lookup"><span data-stu-id="e8b5e-137">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="e8b5e-138">Interfejs można <xref:System.Collections.Generic.IEnumerable%601> rozszerzyć za pomocą niestandardowej metody kwerendy, która zwraca sekwencję wartości.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-138">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="e8b5e-139">W takim przypadku metoda musi zwrócić <xref:System.Collections.Generic.IEnumerable%601>kolekcję typu .</span><span class="sxs-lookup"><span data-stu-id="e8b5e-139">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="e8b5e-140">Takie metody mogą służyć do stosowania filtrów lub przekształcadanych danych do sekwencji wartości.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-140">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="e8b5e-141">W poniższym przykładzie pokazano, `AlternateElements` jak utworzyć metodę rozszerzenia o nazwie, która zwraca co drugi element w kolekcji, począwszy od pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="e8b5e-141">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

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

<span data-ttu-id="e8b5e-142">Tę metodę rozszerzenia można wywołać dla dowolnej kolekcji numerowanej, tak <xref:System.Collections.Generic.IEnumerable%601> jak można wywołać inne metody z interfejsu, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e8b5e-142">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e8b5e-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8b5e-143">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="e8b5e-144">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="e8b5e-144">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
