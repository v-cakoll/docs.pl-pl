---
title: Iteratory
description: Dowiedz się, jak używać wbudowanych iteratorów języka C# i jak tworzyć własne, niestandardowe metody iteratora.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: efa755c2243c18fb51b653abccb2bfc702bbc055
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507380"
---
# <a name="iterators"></a><span data-ttu-id="38af4-103">Iteratory</span><span class="sxs-lookup"><span data-stu-id="38af4-103">Iterators</span></span>

<span data-ttu-id="38af4-104">Prawie każdy napisany program będzie musiał wykonać iterację w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="38af4-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="38af4-105">Napiszesz kod, który analizuje każdy element w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="38af4-105">You'll write code that examines every item in a collection.</span></span>

<span data-ttu-id="38af4-106">Utworzysz również metody iteratorów, które są metodami, które tworzą iterator (który jest obiektem, który przechodzi kontener, szczególnie list) dla elementów tej klasy.</span><span class="sxs-lookup"><span data-stu-id="38af4-106">You'll also create iterator methods which are methods that produces an iterator (which is an object that traverses a container, particularly lists) for the elements of that class.</span></span> <span data-ttu-id="38af4-107">Można ich używać w programie:</span><span class="sxs-lookup"><span data-stu-id="38af4-107">These can be used for:</span></span>

+ <span data-ttu-id="38af4-108">Wykonywanie akcji dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="38af4-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="38af4-109">Wyliczanie kolekcji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="38af4-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="38af4-110">Rozszerzanie [LINQ](linq/index.md) lub innych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="38af4-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="38af4-111">Tworzenie potoku danych, w którym dane są efektywnie przesyłane za pomocą metod iteratora.</span><span class="sxs-lookup"><span data-stu-id="38af4-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="38af4-112">Język C# zawiera funkcje dla obu tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="38af4-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="38af4-113">Ten artykuł zawiera omówienie tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="38af4-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="38af4-114">Ten samouczek zawiera wiele kroków.</span><span class="sxs-lookup"><span data-stu-id="38af4-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="38af4-115">Po każdym kroku można uruchomić aplikację i postępować według postępu.</span><span class="sxs-lookup"><span data-stu-id="38af4-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="38af4-116">Możesz również [wyświetlić lub pobrać ukończony przykład](https://github.com/dotnet/samples/blob/master/csharp/iterators) dla tego tematu.</span><span class="sxs-lookup"><span data-stu-id="38af4-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/master/csharp/iterators) for this topic.</span></span> <span data-ttu-id="38af4-117">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="38af4-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="38af4-118">Iteracja przy użyciu instrukcji foreach</span><span class="sxs-lookup"><span data-stu-id="38af4-118">Iterating with foreach</span></span>

<span data-ttu-id="38af4-119">Wyliczanie kolekcji jest proste: `foreach` słowo kluczowe wylicza kolekcję, wykonując osadzoną instrukcję dla każdego elementu w kolekcji:</span><span class="sxs-lookup"><span data-stu-id="38af4-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="38af4-120">To już wszystko.</span><span class="sxs-lookup"><span data-stu-id="38af4-120">That's all there is to it.</span></span> <span data-ttu-id="38af4-121">Aby wykonać iterację całej zawartości kolekcji, jest to wszystko `foreach` , co jest potrzebne.</span><span class="sxs-lookup"><span data-stu-id="38af4-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="38af4-122">`foreach` Instrukcja nie jest magiczna, chociaż.</span><span class="sxs-lookup"><span data-stu-id="38af4-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="38af4-123">Opiera się on na dwóch ogólnych interfejsach zdefiniowanych w bibliotece .NET Core w celu wygenerowania kodu niezbędnego do iteracji kolekcji: `IEnumerable<T>` i. `IEnumerator<T>`</span><span class="sxs-lookup"><span data-stu-id="38af4-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="38af4-124">Ten mechanizm został wyjaśniony bardziej szczegółowo poniżej.</span><span class="sxs-lookup"><span data-stu-id="38af4-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="38af4-125">Oba te interfejsy mają również nieogólne odpowiedniki: `IEnumerable` i. `IEnumerator`</span><span class="sxs-lookup"><span data-stu-id="38af4-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="38af4-126">Wersje [Ogólne](programming-guide/generics/index.md) są preferowane w przypadku nowoczesnych kodów.</span><span class="sxs-lookup"><span data-stu-id="38af4-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="38af4-127">Źródła wyliczenia z metodami iteratora</span><span class="sxs-lookup"><span data-stu-id="38af4-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="38af4-128">Kolejną doskonałą cechą języka C# jest możliwość tworzenia metod, które tworzą Źródło dla wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="38af4-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="38af4-129">Są one nazywane *metodami iteratora*.</span><span class="sxs-lookup"><span data-stu-id="38af4-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="38af4-130">Metoda iteratora definiuje sposób generowania obiektów w sekwencji, gdy jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="38af4-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="38af4-131">`yield return` Kontekstowe słowa kluczowe służą do definiowania metody iteratora.</span><span class="sxs-lookup"><span data-stu-id="38af4-131">You use the `yield return` contextual keywords to define an iterator method.</span></span>

<span data-ttu-id="38af4-132">Można napisać tę metodę, aby utworzyć sekwencję liczb całkowitych z zakresu od 0 do 9:</span><span class="sxs-lookup"><span data-stu-id="38af4-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

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

<span data-ttu-id="38af4-133">W powyższym kodzie `yield return` przedstawiono różne instrukcje, aby wyróżnić fakt, że w `yield return` metodzie iteratora można użyć wielu instrukcji dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="38af4-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="38af4-134">Można (i często) używać innych konstrukcji językowych, aby uprościć kod metody iterator.</span><span class="sxs-lookup"><span data-stu-id="38af4-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="38af4-135">Poniższa definicja metody daje dokładną sekwencję liczb:</span><span class="sxs-lookup"><span data-stu-id="38af4-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

<span data-ttu-id="38af4-136">Nie musisz decydować o sobie.</span><span class="sxs-lookup"><span data-stu-id="38af4-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="38af4-137">W razie potrzeby można mieć `yield return` dowolną liczbę instrukcji, aby spełnić wymagania metody:</span><span class="sxs-lookup"><span data-stu-id="38af4-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

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

<span data-ttu-id="38af4-138">Jest to podstawowa składnia.</span><span class="sxs-lookup"><span data-stu-id="38af4-138">That's the basic syntax.</span></span> <span data-ttu-id="38af4-139">Rozważmy przykład Real świecie, w którym można napisać metodę iteratora.</span><span class="sxs-lookup"><span data-stu-id="38af4-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="38af4-140">Wyobraź sobie, że jesteś w projekcie IoT, a czujniki urządzeń generują bardzo duży strumień danych.</span><span class="sxs-lookup"><span data-stu-id="38af4-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="38af4-141">Aby uzyskać działanie dla danych, można napisać metodę, która próbuje pobrać każdy n-ty element danych.</span><span class="sxs-lookup"><span data-stu-id="38af4-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="38af4-142">Ta mała Metoda iteratora jest jedną z lew:</span><span class="sxs-lookup"><span data-stu-id="38af4-142">This small iterator method does the trick:</span></span>

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

<span data-ttu-id="38af4-143">Istnieje jedno ważne ograniczenie metod iteratora: nie można mieć `return` instrukcji i `yield return` instrukcji w tej samej metodzie.</span><span class="sxs-lookup"><span data-stu-id="38af4-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="38af4-144">Następujące elementy nie zostaną skompilowane:</span><span class="sxs-lookup"><span data-stu-id="38af4-144">The following will not compile:</span></span>

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

<span data-ttu-id="38af4-145">To ograniczenie zwykle nie jest problemem.</span><span class="sxs-lookup"><span data-stu-id="38af4-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="38af4-146">Możesz użyć `yield return` metody lub oddzielić oryginalną metodę na wiele metod, niektóre przy `return`użyciu i niektóre z `yield return`nich.</span><span class="sxs-lookup"><span data-stu-id="38af4-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="38af4-147">Ostatnią metodę można zmodyfikować nieco do użycia `yield return` wszędzie:</span><span class="sxs-lookup"><span data-stu-id="38af4-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

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

<span data-ttu-id="38af4-148">Czasami odpowiednia odpowiedź polega na podzieleniu metody iteratora na dwie różne metody.</span><span class="sxs-lookup"><span data-stu-id="38af4-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="38af4-149">Jeden z nich `return`korzysta i drugi, który używa `yield return`.</span><span class="sxs-lookup"><span data-stu-id="38af4-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="38af4-150">Rozważ sytuację, w której możesz chcieć zwrócić pustą kolekcję lub 5 pierwszych liczb nieparzystych na podstawie argumentu logicznego.</span><span class="sxs-lookup"><span data-stu-id="38af4-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="38af4-151">Można napisać te dwie metody:</span><span class="sxs-lookup"><span data-stu-id="38af4-151">You could write that as these two methods:</span></span>

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

<span data-ttu-id="38af4-152">Zapoznaj się z powyższymi metodami.</span><span class="sxs-lookup"><span data-stu-id="38af4-152">Look at the methods above.</span></span> <span data-ttu-id="38af4-153">Pierwszy używa instrukcji standardowej `return` do zwrócenia pustej kolekcji lub iteratora utworzonego przez drugą metodę.</span><span class="sxs-lookup"><span data-stu-id="38af4-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="38af4-154">Druga metoda używa `yield return` instrukcji, aby utworzyć żądaną sekwencję.</span><span class="sxs-lookup"><span data-stu-id="38af4-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="38af4-155">Dokładniejsze szczegółowe`foreach`</span><span class="sxs-lookup"><span data-stu-id="38af4-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="38af4-156">`foreach` Instrukcja rozszerza się do standardowego idiom, który używa interfejsów `IEnumerable<T>` i `IEnumerator<T>` do iteracji dla wszystkich elementów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="38af4-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="38af4-157">Minimalizuje ona także błędy deweloperów, aby nie zarządzać zasobami.</span><span class="sxs-lookup"><span data-stu-id="38af4-157">It also  minimizes errors developers make by not properly managing resources.</span></span>

<span data-ttu-id="38af4-158">Kompilator tłumaczy `foreach` pętlę pokazaną w pierwszym przykładzie na coś podobnego do tej konstrukcji:</span><span class="sxs-lookup"><span data-stu-id="38af4-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="38af4-159">Powyższa konstrukcja reprezentuje kod wygenerowany przez kompilator języka C# w wersji 5 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="38af4-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="38af4-160">Przed wersjami 5 `item` zmienna miała inny zakres:</span><span class="sxs-lookup"><span data-stu-id="38af4-160">Prior to version 5, the `item` variable had a different scope:</span></span>

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

<span data-ttu-id="38af4-161">Ta zmiana została zmieniona, ponieważ wcześniejsze zachowanie może prowadzić do delikatnej i trudnej diagnostyki błędów obejmujących wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="38af4-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="38af4-162">Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="38af4-162">For more information about lambda expressions, see [Lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="38af4-163">Dokładny kod generowany przez kompilator jest nieco bardziej skomplikowany i obsługuje sytuacje, w których obiekt zwrócony przez `GetEnumerator()` implementację `IDisposable` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="38af4-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="38af4-164">Pełne rozszerzenie generuje kod bardziej podobny do tego:</span><span class="sxs-lookup"><span data-stu-id="38af4-164">The full expansion generates code more like this:</span></span>

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

<span data-ttu-id="38af4-165">Sposób, w jaki moduł wyliczający jest usuwany, zależy od właściwości typu `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="38af4-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="38af4-166">W ogólnym przypadku `finally` klauzula rozszerza się do:</span><span class="sxs-lookup"><span data-stu-id="38af4-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

<span data-ttu-id="38af4-167">Jeśli `enumerator` jednak typ jest typem zapieczętowanym i nie istnieje niejawna konwersja z `enumerator` typu do `IDisposable`, `finally` klauzula rozszerza do pustego bloku:</span><span class="sxs-lookup"><span data-stu-id="38af4-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>

```csharp
finally
{
}
```

<span data-ttu-id="38af4-168">Jeśli istnieje niejawna konwersja z `enumerator` typu do `IDisposable`, i `enumerator` jest typem wartości niedopuszczających wartości null, `finally` klauzula rozszerza się do:</span><span class="sxs-lookup"><span data-stu-id="38af4-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

<span data-ttu-id="38af4-169">Thankfully nie musisz zapamiętać wszystkich tych szczegółów.</span><span class="sxs-lookup"><span data-stu-id="38af4-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="38af4-170">`foreach` Instrukcja obsługuje wszystkie te wszystkie szczegóły.</span><span class="sxs-lookup"><span data-stu-id="38af4-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="38af4-171">Kompilator wygeneruje poprawny kod dla dowolnego z tych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="38af4-171">The compiler will generate the correct code for any of these constructs.</span></span>
