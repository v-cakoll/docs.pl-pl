---
title: Jak dodać metody niestandardowe dla zapytań LINQ (C#)
description: Dowiedz się, jak rozszerzać zestaw metod, których można użyć dla zapytań LINQ przez dodanie metod rozszerzenia do <T> interfejsu IEnumerable w języku C#.
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: fac0eb4e14eb3bb36313232a7d7fa3060c0ac171
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103600"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="2f6b1-103">Jak dodać metody niestandardowe dla zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="2f6b1-103">How to add custom methods for LINQ queries (C#)</span></span>

<span data-ttu-id="2f6b1-104">Można rozszerzać zestaw metod, których można użyć dla zapytań LINQ przez dodanie metod rozszerzających do <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-104">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="2f6b1-105">Na przykład oprócz standardowej średniej lub maksymalnej operacji można utworzyć niestandardową metodę agregującą, aby obliczyć pojedynczą wartość z sekwencji wartości.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-105">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="2f6b1-106">Możesz również utworzyć metodę, która działa jako filtr niestandardowy lub Przekształć dane dla sekwencji wartości i zwraca nową sekwencję.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-106">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="2f6b1-107">Przykładami takich metod są <xref:System.Linq.Enumerable.Distinct%2A> , <xref:System.Linq.Enumerable.Skip%2A> , i <xref:System.Linq.Enumerable.Reverse%2A> .</span><span class="sxs-lookup"><span data-stu-id="2f6b1-107">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="2f6b1-108">Rozszerzając <xref:System.Collections.Generic.IEnumerable%601> interfejs, można zastosować niestandardowe metody do dowolnej wyliczalnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-108">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="2f6b1-109">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="2f6b1-109">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="2f6b1-110">Dodawanie metody agregującej</span><span class="sxs-lookup"><span data-stu-id="2f6b1-110">Adding an Aggregate Method</span></span>

<span data-ttu-id="2f6b1-111">Metoda agregująca oblicza pojedynczą wartość z zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-111">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="2f6b1-112">LINQ zawiera kilka metod agregujących, w tym <xref:System.Linq.Enumerable.Average%2A> , <xref:System.Linq.Enumerable.Min%2A> i <xref:System.Linq.Enumerable.Max%2A> .</span><span class="sxs-lookup"><span data-stu-id="2f6b1-112">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="2f6b1-113">Można utworzyć własną metodę agregującą, dodając metodę rozszerzenia do <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-113">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="2f6b1-114">Poniższy przykład kodu pokazuje, jak utworzyć metodę rozszerzenia wywołana, `Median` Aby obliczyć medianę dla sekwencji liczb typu `double` .</span><span class="sxs-lookup"><span data-stu-id="2f6b1-114">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```csharp
public static class LINQExtension
{
    public static double Median(this IEnumerable<double> source)
    {
        var countOfElementsInTheSet = source?.Count() ?? 0;

        if (countOfElementsInTheSet == 0)
        {
            throw new InvalidOperationException("Cannot compute median for a null or empty set.");
        }

        var sortedList = (from number in source
                         orderby number
                         select number).ToList();

        int itemIndex = countOfElementsInTheSet / 2;

        if (countOfElementsInTheSet % 2 == 0)
        {
            // Even number of items.
            return (sortedList[itemIndex] + sortedList[itemIndex - 1]) / 2;
        }
        else
        {
            // Odd number of items.
            return sortedList[itemIndex];
        }
    }
}
```

<span data-ttu-id="2f6b1-115">Ta metoda rozszerzenia jest wywoływana dla każdej wyliczalnej kolekcji w taki sam sposób, w jaki wywołujemy inne metody agregacji z <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-115">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="2f6b1-116">Poniższy przykład kodu pokazuje, jak używać `Median` metody dla tablicy typu `double` .</span><span class="sxs-lookup"><span data-stu-id="2f6b1-116">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="2f6b1-117">Przeciążanie metody agregującej w celu zaakceptowania różnych typów</span><span class="sxs-lookup"><span data-stu-id="2f6b1-117">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="2f6b1-118">Można przeciążyć metodę agregacji, aby akceptować sekwencje różnych typów.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-118">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="2f6b1-119">Standardowe podejście polega na utworzeniu przeciążenia dla każdego typu.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-119">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="2f6b1-120">Innym rozwiązaniem jest utworzenie przeciążenia, które będzie miało typ ogólny i przekonwertować go na określony typ za pomocą delegata.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-120">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="2f6b1-121">Można również połączyć oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-121">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="2f6b1-122">Aby utworzyć Przeciążenie dla każdego typu</span><span class="sxs-lookup"><span data-stu-id="2f6b1-122">To create an overload for each type</span></span>

<span data-ttu-id="2f6b1-123">Można utworzyć określone Przeciążenie dla każdego typu, który ma być obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-123">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="2f6b1-124">Poniższy przykład kodu przedstawia Przeciążenie `Median` metody dla `integer` typu.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-124">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="2f6b1-125">Teraz można wywoływać `Median` przeciążenia dla obu `integer` typów i `double` typy, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="2f6b1-125">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

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

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="2f6b1-126">Aby utworzyć Przeciążenie ogólne</span><span class="sxs-lookup"><span data-stu-id="2f6b1-126">To create a generic overload</span></span>

<span data-ttu-id="2f6b1-127">Można również utworzyć Przeciążenie, które akceptuje sekwencję obiektów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-127">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="2f6b1-128">To przeciążenie przyjmuje delegat jako parametr i używa go do konwersji sekwencji obiektów typu ogólnego do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-128">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="2f6b1-129">Poniższy kod przedstawia Przeciążenie `Median` metody, która przyjmuje <xref:System.Func%602> Delegat jako parametr.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-129">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="2f6b1-130">Ten delegat pobiera obiekt typu ogólnego T i zwraca obiekt typu `double` .</span><span class="sxs-lookup"><span data-stu-id="2f6b1-130">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="2f6b1-131">Teraz można wywołać `Median` metodę dla sekwencji obiektów dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-131">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="2f6b1-132">Jeśli typ nie ma własnego przeciążenia metody, należy przekazać parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-132">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="2f6b1-133">W języku C# można użyć wyrażenia lambda do tego celu.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-133">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="2f6b1-134">Ponadto, tylko w Visual Basic, jeśli używasz `Aggregate` `Group By` klauzuli or zamiast wywołania metody, można przekazać dowolną wartość lub wyrażenie, które znajduje się w zakresie tej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-134">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="2f6b1-135">Poniższy przykładowy kod pokazuje, jak wywołać `Median` metodę dla tablicy liczb całkowitych i tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-135">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="2f6b1-136">Dla ciągów, mediany dla długości ciągów w tablicy jest obliczany.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-136">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="2f6b1-137">W przykładzie pokazano, jak przekazać <xref:System.Func%602> parametr delegata do `Median` metody dla każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-137">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

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

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="2f6b1-138">Dodawanie metody zwracającej kolekcję</span><span class="sxs-lookup"><span data-stu-id="2f6b1-138">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="2f6b1-139">Interfejs można rozszerzyć <xref:System.Collections.Generic.IEnumerable%601> za pomocą niestandardowej metody zapytania, która zwraca sekwencję wartości.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-139">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="2f6b1-140">W tym przypadku metoda musi zwracać kolekcję typu <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="2f6b1-140">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="2f6b1-141">Takie metody mogą służyć do zastosowania filtrów lub transformacji danych do sekwencji wartości.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-141">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="2f6b1-142">Poniższy przykład pokazuje, jak utworzyć metodę rozszerzenia o nazwie `AlternateElements` , która zwraca każdy inny element w kolekcji, rozpoczynając od pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="2f6b1-142">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

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

<span data-ttu-id="2f6b1-143">Można wywołać tę metodę rozszerzenia dla każdej wyliczalnej kolekcji tak samo jak w przypadku wywołania innych metod z <xref:System.Collections.Generic.IEnumerable%601> interfejsu, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="2f6b1-143">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2f6b1-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f6b1-144">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="2f6b1-145">Metody rozszerzania</span><span class="sxs-lookup"><span data-stu-id="2f6b1-145">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
