---
title: Iteratory
description: Dowiedz się, jak używać wbudowanych iteratorów języka C# i jak tworzyć własne niestandardowe metody iteratorem.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 1933ecf83e9fa234f9b88c815d8ab527997c97f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399617"
---
# <a name="iterators"></a><span data-ttu-id="f2128-103">Iteratory</span><span class="sxs-lookup"><span data-stu-id="f2128-103">Iterators</span></span>

<span data-ttu-id="f2128-104">Prawie każdy program, który piszesz, będzie musiał iterować nad kolekcją.</span><span class="sxs-lookup"><span data-stu-id="f2128-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="f2128-105">Napiszesz kod, który sprawdza każdy element w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f2128-105">You'll write code that examines every item in a collection.</span></span>

<span data-ttu-id="f2128-106">Utworzysz również metody iteratorem, które są metodami, które tworzą iterator dla elementów tej klasy.</span><span class="sxs-lookup"><span data-stu-id="f2128-106">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="f2128-107">Mogą być używane do:</span><span class="sxs-lookup"><span data-stu-id="f2128-107">These can be used for:</span></span>

+ <span data-ttu-id="f2128-108">Wykonywanie akcji na każdym elemencie w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f2128-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="f2128-109">Wyliczanie kolekcji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="f2128-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="f2128-110">Rozszerzanie [LINQ](linq/index.md) lub innych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="f2128-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="f2128-111">Tworzenie potoku danych, w którym dane są przepływać wydajnie za pomocą metod iteratorem.</span><span class="sxs-lookup"><span data-stu-id="f2128-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="f2128-112">Język Języka C# zawiera funkcje dla obu tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="f2128-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="f2128-113">Ten artykuł zawiera omówienie tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="f2128-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="f2128-114">Ten samouczek ma wiele kroków.</span><span class="sxs-lookup"><span data-stu-id="f2128-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="f2128-115">Po każdym kroku można uruchomić aplikację i zobaczyć postęp.</span><span class="sxs-lookup"><span data-stu-id="f2128-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="f2128-116">Możesz również [wyświetlić lub pobrać wypełniony przykład](https://github.com/dotnet/samples/blob/master/csharp/iterators) dla tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f2128-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/master/csharp/iterators) for this topic.</span></span> <span data-ttu-id="f2128-117">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="f2128-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="f2128-118">Iteracji z foreach</span><span class="sxs-lookup"><span data-stu-id="f2128-118">Iterating with foreach</span></span>

<span data-ttu-id="f2128-119">Wyliczanie kolekcji jest `foreach` proste: słowo kluczowe wylicza kolekcję, wykonując osadzoną instrukcję raz dla każdego elementu w kolekcji:</span><span class="sxs-lookup"><span data-stu-id="f2128-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="f2128-120">To już wszystko.</span><span class="sxs-lookup"><span data-stu-id="f2128-120">That's all there is to it.</span></span> <span data-ttu-id="f2128-121">Aby iterate całej zawartości kolekcji, instrukcja `foreach` jest wszystko, czego potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="f2128-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="f2128-122">Stwierdzenie `foreach` to nie jest jednak magiczne.</span><span class="sxs-lookup"><span data-stu-id="f2128-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="f2128-123">Opiera się na dwóch ogólnych interfejsach zdefiniowanych w bibliotece rdzenia .NET `IEnumerable<T>` w `IEnumerator<T>`celu wygenerowania kodu niezbędnego do iterate kolekcji: i .</span><span class="sxs-lookup"><span data-stu-id="f2128-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="f2128-124">Mechanizm ten wyjaśniono bardziej szczegółowo poniżej.</span><span class="sxs-lookup"><span data-stu-id="f2128-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="f2128-125">Oba te interfejsy mają również odpowiedniki `IEnumerable` `IEnumerator`nierodzajowe: i .</span><span class="sxs-lookup"><span data-stu-id="f2128-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="f2128-126">Wersje [ogólne](programming-guide/generics/index.md) są preferowane dla nowoczesnego kodu.</span><span class="sxs-lookup"><span data-stu-id="f2128-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="f2128-127">Źródła wyliczania z metodami iteratorem</span><span class="sxs-lookup"><span data-stu-id="f2128-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="f2128-128">Inną wspaniałą funkcją języka C# umożliwia tworzenie metod, które tworzą źródło wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f2128-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="f2128-129">Są one określane jako *metody iterator .*</span><span class="sxs-lookup"><span data-stu-id="f2128-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="f2128-130">Metoda iteratora definiuje sposób generowania obiektów w sekwencji na żądanie.</span><span class="sxs-lookup"><span data-stu-id="f2128-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="f2128-131">`yield return` Kontekstowe słowa kluczowe służy do definiowania metody iteratorego.</span><span class="sxs-lookup"><span data-stu-id="f2128-131">You use the `yield return` contextual keywords to define an iterator method.</span></span>

<span data-ttu-id="f2128-132">Można napisać tę metodę do produkcji sekwencji liczb całkowitych od 0 do 9:</span><span class="sxs-lookup"><span data-stu-id="f2128-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    yield return 0;
    yield return 1;
    yield return 2;
    yield return 3;
    yield return 4;
    yield return 5;
    yield return 6;
    yield return 7;
    yield return 8;
    yield return 9;
}
```

<span data-ttu-id="f2128-133">Powyższy kod `yield return` przedstawia różne instrukcje, aby wyróżnić fakt, że można użyć wielu dyskretnych `yield return` instrukcji w metodzie sterytora.</span><span class="sxs-lookup"><span data-stu-id="f2128-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="f2128-134">Można (i często zrobić) używać innych konstrukcji języka, aby uprościć kod metody iteratora.</span><span class="sxs-lookup"><span data-stu-id="f2128-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="f2128-135">Poniższa definicja metody daje dokładnie taką samą sekwencję liczb:</span><span class="sxs-lookup"><span data-stu-id="f2128-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

<span data-ttu-id="f2128-136">Nie musisz decydować o jednym czy drugim.</span><span class="sxs-lookup"><span data-stu-id="f2128-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="f2128-137">Możesz mieć tyle `yield return` instrukcji, ile jest to konieczne, aby zaspokoić potrzeby metody:</span><span class="sxs-lookup"><span data-stu-id="f2128-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    index = 100;
    while (index < 110)
        yield return index++;
}
```

<span data-ttu-id="f2128-138">To jest podstawowa składnia.</span><span class="sxs-lookup"><span data-stu-id="f2128-138">That's the basic syntax.</span></span> <span data-ttu-id="f2128-139">Rozważmy przykład świata rzeczywistego, w którym można napisać metodę iterator.</span><span class="sxs-lookup"><span data-stu-id="f2128-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="f2128-140">Wyobraź sobie, że korzystasz z projektu IoT, a czujniki urządzeń generują bardzo duży strumień danych.</span><span class="sxs-lookup"><span data-stu-id="f2128-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="f2128-141">Aby uzyskać wrażenie danych, można napisać metodę, która pobiera próbki co n-ty element danych.</span><span class="sxs-lookup"><span data-stu-id="f2128-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="f2128-142">Ta mała metoda iterator robi sztuczkę:</span><span class="sxs-lookup"><span data-stu-id="f2128-142">This small iterator method does the trick:</span></span>

```csharp
public static IEnumerable<T> Sample(this IEnumerable<T> sourceSequence, int interval)
{
    int index = 0;
    foreach (T item in sourceSequence)
    {
        if (index++ % interval == 0)
            yield return item;
    }
}
```

<span data-ttu-id="f2128-143">Istnieje jedno ważne ograniczenie metod iteratorem: nie można `return` mieć `yield return` zarówno instrukcji, jak i instrukcji w tej samej metodzie.</span><span class="sxs-lookup"><span data-stu-id="f2128-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="f2128-144">Następujące nie skompiluje:</span><span class="sxs-lookup"><span data-stu-id="f2128-144">The following will not compile:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    // generates a compile time error:
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;
}
```

<span data-ttu-id="f2128-145">To ograniczenie zwykle nie stanowi problemu.</span><span class="sxs-lookup"><span data-stu-id="f2128-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="f2128-146">Masz do wyboru użycie `yield return` całej metody lub oddzielenie oryginalnej metody na `return`wiele metod, `yield return`niektóre przy użyciu , a niektóre przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="f2128-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="f2128-147">Możesz nieco zmodyfikować ostatnią `yield return` metodę, aby użyć wszędzie:</span><span class="sxs-lookup"><span data-stu-id="f2128-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```

<span data-ttu-id="f2128-148">Czasami właściwą odpowiedzią jest podzielenie metody iteratorego na dwie różne metody.</span><span class="sxs-lookup"><span data-stu-id="f2128-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="f2128-149">Taki, `return`który używa , `yield return`a drugi, który używa .</span><span class="sxs-lookup"><span data-stu-id="f2128-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="f2128-150">Rozważmy sytuację, w której można zwrócić pustą kolekcję lub pierwszych 5 liczb nieparzystych na podstawie argumentu logicznego.</span><span class="sxs-lookup"><span data-stu-id="f2128-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="f2128-151">Można napisać, że jak te dwie metody:</span><span class="sxs-lookup"><span data-stu-id="f2128-151">You could write that as these two methods:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitOddNumbers(bool getCollection)
{
    if (getCollection == false)
        return new int[0];
    else
        return IteratorMethod();
}

private IEnumerable<int> IteratorMethod()
{
    int index = 0;
    while (index < 10)
    {
        if (index % 2 == 1)
            yield return index;
        index++;
    }
}
```

<span data-ttu-id="f2128-152">Spójrz na powyższe metody.</span><span class="sxs-lookup"><span data-stu-id="f2128-152">Look at the methods above.</span></span> <span data-ttu-id="f2128-153">Pierwszy używa standardowej `return` instrukcji, aby zwrócić puste kolekcji lub iterator utworzony przez drugą metodę.</span><span class="sxs-lookup"><span data-stu-id="f2128-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="f2128-154">Druga metoda używa `yield return` instrukcji do tworzenia żądanesekwencji.</span><span class="sxs-lookup"><span data-stu-id="f2128-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="f2128-155">Głębiej zanurz się w`foreach`</span><span class="sxs-lookup"><span data-stu-id="f2128-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="f2128-156">Instrukcja `foreach` rozszerza się na idiom `IEnumerable<T>` standardowy, który używa i `IEnumerator<T>` interfejsów do itetencji we wszystkich elementach kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f2128-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="f2128-157">Minimalizuje również błędy, które deweloperzy popełniają, nie właściwie zarządzając zasobami.</span><span class="sxs-lookup"><span data-stu-id="f2128-157">It also  minimizes errors developers make by not properly managing resources.</span></span>

<span data-ttu-id="f2128-158">Kompilator tłumaczy `foreach` pętlę pokazaną w pierwszym przykładzie na coś podobnego do tej konstrukcji:</span><span class="sxs-lookup"><span data-stu-id="f2128-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="f2128-159">Powyższa konstrukcja reprezentuje kod generowany przez kompilator C# w wersji 5 i powyżej.</span><span class="sxs-lookup"><span data-stu-id="f2128-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="f2128-160">Przed wersją 5 `item` zmienna miała inny zakres:</span><span class="sxs-lookup"><span data-stu-id="f2128-160">Prior to version 5, the `item` variable had a different scope:</span></span>

```csharp
// C# versions 1 through 4:
IEnumerator<int> enumerator = collection.GetEnumerator();
int item = default(int);
while (enumerator.MoveNext())
{
    item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="f2128-161">Zostało to zmienione, ponieważ wcześniejsze zachowanie może prowadzić do subtelnych i trudnych do zdiagnozowania błędów z udziałem wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="f2128-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="f2128-162">Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [Wyrażenia Lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f2128-162">For more information about lambda expressions, see [Lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="f2128-163">Dokładny kod generowany przez kompilator jest nieco bardziej skomplikowane i obsługuje `GetEnumerator()` sytuacje, `IDisposable` w których obiekt zwracany przez implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="f2128-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="f2128-164">Pełne rozszerzenie generuje kod bardziej podobny do tego:</span><span class="sxs-lookup"><span data-stu-id="f2128-164">The full expansion generates code more like this:</span></span>

```csharp
{
    var enumerator = collection.GetEnumerator();
    try
    {
        while (enumerator.MoveNext())
        {
            var item = enumerator.Current;
            Console.WriteLine(item.ToString());
        }
    } finally
    {
        // dispose of enumerator.
    }
}
```

<span data-ttu-id="f2128-165">Sposób, w jaki wyliczacz jest usuwany, zależy od `enumerator`charakterystyki typu .</span><span class="sxs-lookup"><span data-stu-id="f2128-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="f2128-166">W ogólnym przypadku `finally` klauzula rozszerza się na:</span><span class="sxs-lookup"><span data-stu-id="f2128-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

<span data-ttu-id="f2128-167">Jednakże jeśli typ `enumerator` jest typ zapieczętowany i nie ma niejawne konwersji z typu `enumerator` do `IDisposable`, klauzula `finally` rozszerza się do pustego bloku:</span><span class="sxs-lookup"><span data-stu-id="f2128-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>

```csharp
finally
{
}
```

<span data-ttu-id="f2128-168">Jeśli istnieje niejawna konwersja `enumerator` `IDisposable`z `enumerator` typu do , i jest `finally` typem wartości niepodlegających null, klauzula rozszerza się na:</span><span class="sxs-lookup"><span data-stu-id="f2128-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

<span data-ttu-id="f2128-169">Na szczęście nie musisz pamiętać o tych wszystkich szczegółach.</span><span class="sxs-lookup"><span data-stu-id="f2128-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="f2128-170">Oświadczenie `foreach` obsługuje wszystkie te niuanse dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="f2128-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="f2128-171">Kompilator wygeneruje poprawny kod dla dowolnej z tych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="f2128-171">The compiler will generate the correct code for any of these constructs.</span></span>
