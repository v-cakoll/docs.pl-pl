---
title: 'Instrukcje: Dodaj niestandardowe metody dla zapytań LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: fcf6814c8b3076a18e807a378796094a9ce2cf84
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594149"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="75005-102">Instrukcje: Dodaj niestandardowe metody dla zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="75005-102">How to: Add Custom Methods for LINQ Queries (C#)</span></span>

<span data-ttu-id="75005-103">Można rozszerzać zestaw metod, których można użyć dla zapytań LINQ przez dodanie metod rozszerzających do <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="75005-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="75005-104">Na przykład oprócz standardowej średniej lub maksymalnej operacji można utworzyć niestandardową metodę agregującą, aby obliczyć pojedynczą wartość z sekwencji wartości.</span><span class="sxs-lookup"><span data-stu-id="75005-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="75005-105">Możesz również utworzyć metodę, która działa jako filtr niestandardowy lub Przekształć dane dla sekwencji wartości i zwraca nową sekwencję.</span><span class="sxs-lookup"><span data-stu-id="75005-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="75005-106">Przykładami takich metod są <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, i <xref:System.Linq.Enumerable.Reverse%2A>.</span><span class="sxs-lookup"><span data-stu-id="75005-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="75005-107">Rozszerzając <xref:System.Collections.Generic.IEnumerable%601> interfejs, można zastosować niestandardowe metody do dowolnej wyliczalnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="75005-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="75005-108">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="75005-108">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="75005-109">Dodawanie metody agregującej</span><span class="sxs-lookup"><span data-stu-id="75005-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="75005-110">Metoda agregująca oblicza pojedynczą wartość z zestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="75005-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="75005-111">LINQ zawiera kilka metod agregujących, <xref:System.Linq.Enumerable.Average%2A>w <xref:System.Linq.Enumerable.Min%2A>tym, <xref:System.Linq.Enumerable.Max%2A>i.</span><span class="sxs-lookup"><span data-stu-id="75005-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="75005-112">Można utworzyć własną metodę agregującą, dodając metodę rozszerzenia do <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="75005-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="75005-113">Poniższy przykład kodu pokazuje, jak utworzyć metodę rozszerzenia wywołana `Median` , aby obliczyć medianę dla sekwencji liczb typu. `double`</span><span class="sxs-lookup"><span data-stu-id="75005-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

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

<span data-ttu-id="75005-114">Ta metoda rozszerzenia jest wywoływana dla każdej wyliczalnej kolekcji w taki sam sposób, w jaki wywołujemy <xref:System.Collections.Generic.IEnumerable%601> inne metody agregacji z interfejsu.</span><span class="sxs-lookup"><span data-stu-id="75005-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="75005-115">Poniższy przykład kodu pokazuje, `Median` jak używać metody dla tablicy typu. `double`</span><span class="sxs-lookup"><span data-stu-id="75005-115">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="75005-116">Przeciążanie metody agregującej w celu zaakceptowania różnych typów</span><span class="sxs-lookup"><span data-stu-id="75005-116">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="75005-117">Można przeciążyć metodę agregacji, aby akceptować sekwencje różnych typów.</span><span class="sxs-lookup"><span data-stu-id="75005-117">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="75005-118">Standardowe podejście polega na utworzeniu przeciążenia dla każdego typu.</span><span class="sxs-lookup"><span data-stu-id="75005-118">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="75005-119">Innym rozwiązaniem jest utworzenie przeciążenia, które będzie miało typ ogólny i przekonwertować go na określony typ za pomocą delegata.</span><span class="sxs-lookup"><span data-stu-id="75005-119">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="75005-120">Można również połączyć oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="75005-120">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="75005-121">Aby utworzyć Przeciążenie dla każdego typu</span><span class="sxs-lookup"><span data-stu-id="75005-121">To create an overload for each type</span></span>

<span data-ttu-id="75005-122">Można utworzyć określone Przeciążenie dla każdego typu, który ma być obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="75005-122">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="75005-123">Poniższy przykład kodu przedstawia Przeciążenie `Median` metody `integer` dla typu.</span><span class="sxs-lookup"><span data-stu-id="75005-123">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="75005-124">Teraz można wywoływać `Median` przeciążenia dla obu `integer` typów i `double` typy, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="75005-124">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

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

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="75005-125">Aby utworzyć Przeciążenie ogólne</span><span class="sxs-lookup"><span data-stu-id="75005-125">To create a generic overload</span></span>

<span data-ttu-id="75005-126">Można również utworzyć Przeciążenie, które akceptuje sekwencję obiektów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="75005-126">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="75005-127">To przeciążenie przyjmuje delegat jako parametr i używa go do konwersji sekwencji obiektów typu ogólnego do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="75005-127">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="75005-128">Poniższy kod przedstawia Przeciążenie `Median` metody, która <xref:System.Func%602> przyjmuje delegat jako parametr.</span><span class="sxs-lookup"><span data-stu-id="75005-128">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="75005-129">Ten delegat pobiera obiekt typu ogólnego T i zwraca obiekt typu `double`.</span><span class="sxs-lookup"><span data-stu-id="75005-129">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="75005-130">Teraz można wywołać `Median` metodę dla sekwencji obiektów dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="75005-130">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="75005-131">Jeśli typ nie ma własnego przeciążenia metody, należy przekazać parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="75005-131">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="75005-132">W C#programie można użyć wyrażenia lambda do tego celu.</span><span class="sxs-lookup"><span data-stu-id="75005-132">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="75005-133">Ponadto, tylko w Visual Basic, jeśli używasz `Aggregate` klauzuli or `Group By` zamiast wywołania metody, można przekazać dowolną wartość lub wyrażenie, które znajduje się w zakresie tej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="75005-133">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="75005-134">Poniższy przykładowy kod pokazuje, `Median` jak wywołać metodę dla tablicy liczb całkowitych i tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="75005-134">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="75005-135">Dla ciągów, mediany dla długości ciągów w tablicy jest obliczany.</span><span class="sxs-lookup"><span data-stu-id="75005-135">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="75005-136">W przykładzie pokazano, <xref:System.Func%602> jak przekazać parametr delegata `Median` do metody dla każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="75005-136">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

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

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="75005-137">Dodawanie metody zwracającej kolekcję</span><span class="sxs-lookup"><span data-stu-id="75005-137">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="75005-138"><xref:System.Collections.Generic.IEnumerable%601> Interfejs można rozszerzyć za pomocą niestandardowej metody zapytania, która zwraca sekwencję wartości.</span><span class="sxs-lookup"><span data-stu-id="75005-138">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="75005-139">W tym przypadku metoda musi zwracać kolekcję typu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="75005-139">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="75005-140">Takie metody mogą służyć do zastosowania filtrów lub transformacji danych do sekwencji wartości.</span><span class="sxs-lookup"><span data-stu-id="75005-140">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="75005-141">Poniższy przykład pokazuje, jak utworzyć metodę rozszerzenia o nazwie `AlternateElements` , która zwraca każdy inny element w kolekcji, rozpoczynając od pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="75005-141">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

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

<span data-ttu-id="75005-142">Można wywołać tę metodę rozszerzenia dla każdej wyliczalnej kolekcji tak samo jak w przypadku wywołania innych metod <xref:System.Collections.Generic.IEnumerable%601> z interfejsu, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="75005-142">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="75005-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75005-143">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="75005-144">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="75005-144">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
