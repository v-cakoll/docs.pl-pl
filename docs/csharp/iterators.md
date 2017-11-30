---
title: Iteratory
description: "Dowiedz się, jak za pomocą wbudowanych Iteratory C# oraz tworzenie własnych metody iteracyjne niestandardowych."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 18a5819402c752f32aecd0cd4c3bd5a490292ebf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iterators"></a><span data-ttu-id="76ab8-104">Iteratory</span><span class="sxs-lookup"><span data-stu-id="76ab8-104">Iterators</span></span>

<span data-ttu-id="76ab8-105">Niemal wszystkie programy, jaki ma niektóre trzeba Iterowanie przez kolekcję.</span><span class="sxs-lookup"><span data-stu-id="76ab8-105">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="76ab8-106">Będzie pisania kodu, który sprawdza, czy każdy element w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="76ab8-106">You'll write code that examines every item in a collection.</span></span> 

<span data-ttu-id="76ab8-107">Utworzysz także metody iteracyjne, które metod, które tworzy iteratora dla elementów tej klasy.</span><span class="sxs-lookup"><span data-stu-id="76ab8-107">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="76ab8-108">Te mogą służyć do:</span><span class="sxs-lookup"><span data-stu-id="76ab8-108">These can be used for:</span></span>

+ <span data-ttu-id="76ab8-109">Wykonuje akcję na każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="76ab8-109">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="76ab8-110">Wyliczanie kolekcji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="76ab8-110">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="76ab8-111">Rozszerzanie [LINQ](linq/index.md) lub innych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="76ab8-111">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="76ab8-112">Tworzenie potoku danych, w którym dane przepływają wydajnie za pośrednictwem metody iteracyjne.</span><span class="sxs-lookup"><span data-stu-id="76ab8-112">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="76ab8-113">W języku C# udostępnia funkcje dla obu tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="76ab8-113">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="76ab8-114">Ten artykuł zawiera omówienie tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="76ab8-114">This article provides an overview of those features.</span></span>

<span data-ttu-id="76ab8-115">Ten samouczek ma wiele kroków.</span><span class="sxs-lookup"><span data-stu-id="76ab8-115">This tutorial has multiple steps.</span></span> <span data-ttu-id="76ab8-116">Po każdym kroku możesz uruchomić aplikację i wyświetlany jest postęp.</span><span class="sxs-lookup"><span data-stu-id="76ab8-116">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="76ab8-117">Możesz również [wyświetlić lub pobrać przykład wypełnionego](https://github.com/dotnet/docs/blob/master/samples/csharp/iterators) dla tego tematu.</span><span class="sxs-lookup"><span data-stu-id="76ab8-117">You can also [view or download the completed sample](https://github.com/dotnet/docs/blob/master/samples/csharp/iterators) for this topic.</span></span> <span data-ttu-id="76ab8-118">Instrukcje pobrania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="76ab8-118">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="76ab8-119">Iterowanie za pomocą instrukcji foreach</span><span class="sxs-lookup"><span data-stu-id="76ab8-119">Iterating with foreach</span></span>

<span data-ttu-id="76ab8-120">Wyliczanie kolekcji jest prosty: `foreach` — słowo kluczowe wylicza kolekcję wykonywania osadzona instrukcja raz dla każdego elementu w kolekcji:</span><span class="sxs-lookup"><span data-stu-id="76ab8-120">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="76ab8-121">To wszystko jest do niego.</span><span class="sxs-lookup"><span data-stu-id="76ab8-121">That's all there is to it.</span></span> <span data-ttu-id="76ab8-122">Aby przejść przez całą zawartość kolekcji, `foreach` instrukcja jest potrzebna.</span><span class="sxs-lookup"><span data-stu-id="76ab8-122">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="76ab8-123">`foreach` Instrukcja nie jest magic, mimo że.</span><span class="sxs-lookup"><span data-stu-id="76ab8-123">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="76ab8-124">Opiera się na dwóch interfejsach zdefiniowany w bibliotece programu .NET core w celu wygenerowania kodu niezbędne w celu wykonania iteracji w kolekcji: `IEnumerable<T>` i `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="76ab8-124">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="76ab8-125">Ten mechanizm jest co omówiono bardziej szczegółowo poniżej.</span><span class="sxs-lookup"><span data-stu-id="76ab8-125">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="76ab8-126">Z tych interfejsów również mają odpowiedniki nieogólnego: `IEnumerable` i `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="76ab8-126">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="76ab8-127">[Ogólnego](programming-guide/generics/index.md) wersje są preferowane dla nowoczesnego kodu.</span><span class="sxs-lookup"><span data-stu-id="76ab8-127">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="76ab8-128">Wyliczenie źródeł za pomocą metody iteracyjne</span><span class="sxs-lookup"><span data-stu-id="76ab8-128">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="76ab8-129">Inny wspaniałych funkcji języka C# umożliwia tworzenie metody, które utworzyć źródło wyliczania.</span><span class="sxs-lookup"><span data-stu-id="76ab8-129">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="76ab8-130">Są one określane jako *metody iteracyjne*.</span><span class="sxs-lookup"><span data-stu-id="76ab8-130">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="76ab8-131">Iterator — metoda definiuje sposób generowania obiektów w sekwencji na żądanie.</span><span class="sxs-lookup"><span data-stu-id="76ab8-131">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="76ab8-132">Możesz użyć `yield return` kontekstowe słowa kluczowe, aby określić metodę iteratora.</span><span class="sxs-lookup"><span data-stu-id="76ab8-132">You use the `yield return` contextual keywords to define an iterator method.</span></span> 

<span data-ttu-id="76ab8-133">Można zapisać tę metodę w celu utworzenia sekwencji liczb całkowitych od 0 do 9:</span><span class="sxs-lookup"><span data-stu-id="76ab8-133">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

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

<span data-ttu-id="76ab8-134">Powyższy kod przedstawia różne `yield return` instrukcje, aby wyróżnić fakt, że można używać wielu odrębny `yield return` instrukcje w metodzie iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="76ab8-134">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="76ab8-135">Można (i często nie) użyć innych konstrukcji językowych, aby uprościć kod metody iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="76ab8-135">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="76ab8-136">Definicja metody poniżej tworzy dokładnie tej samej sekwencji liczb:</span><span class="sxs-lookup"><span data-stu-id="76ab8-136">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

<span data-ttu-id="76ab8-137">Nie trzeba określić jednego lub drugiego.</span><span class="sxs-lookup"><span data-stu-id="76ab8-137">You don't have to decide one or the other.</span></span> <span data-ttu-id="76ab8-138">Może mieć tyle `yield return` instrukcje odpowiednio do potrzeb metodę:</span><span class="sxs-lookup"><span data-stu-id="76ab8-138">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
    
    index = 100;
    while (index++ < 110)
        yield return index;
}
```

<span data-ttu-id="76ab8-139">To jest podstawowa składnia.</span><span class="sxs-lookup"><span data-stu-id="76ab8-139">That's the basic syntax.</span></span> <span data-ttu-id="76ab8-140">Zastanówmy się przykład rzeczywistych, w którym możesz zapisać metodę iteratora.</span><span class="sxs-lookup"><span data-stu-id="76ab8-140">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="76ab8-141">Wyobraź sobie w projekcie IoT i czujników urządzenia generować bardzo duże strumienia danych.</span><span class="sxs-lookup"><span data-stu-id="76ab8-141">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="76ab8-142">Aby uzyskać pewne pojęcie o danych, może być napisanie metody, która przykłady każdego elementu danych w n-ty.</span><span class="sxs-lookup"><span data-stu-id="76ab8-142">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="76ab8-143">Ta metoda małych iteratora wykonuje lewy:</span><span class="sxs-lookup"><span data-stu-id="76ab8-143">This small iterator method does the trick:</span></span>

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

<span data-ttu-id="76ab8-144">Istnieje jeden ważne ograniczenia metody iteracyjne: nie może zawierać zarówno `return` instrukcji i `yield return` instrukcji w tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="76ab8-144">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="76ab8-145">Następujące nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="76ab8-145">The following will not compile:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
   
    // generates a compile time error: 
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;  
}
```

<span data-ttu-id="76ab8-146">To ograniczenie jest zazwyczaj problem.</span><span class="sxs-lookup"><span data-stu-id="76ab8-146">This restriction normally isn't a problem.</span></span> <span data-ttu-id="76ab8-147">Masz do wyboru przy użyciu `yield return` w metodzie lub rozdzielić wiele metod oryginalnej metody, przy użyciu niektóre `return`, a niektóre przy użyciu `yield return`.</span><span class="sxs-lookup"><span data-stu-id="76ab8-147">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="76ab8-148">Można zmodyfikować ostatniego metodę używaną do nieco `yield return` wszędzie:</span><span class="sxs-lookup"><span data-stu-id="76ab8-148">You can modify the last method slightly to use `yield return` everywhere:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
   
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```
 
<span data-ttu-id="76ab8-149">Czasami prawidłowa odpowiedź jest podzielić metodę iteratora na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="76ab8-149">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="76ab8-150">Taki, który używa `return`i drugie, która używa `yield return`.</span><span class="sxs-lookup"><span data-stu-id="76ab8-150">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="76ab8-151">Rozważmy sytuację, w których warto zwrócić pustą kolekcję lub pierwszych 5 liczb nieparzysta, oparte na logiczną argumentu.</span><span class="sxs-lookup"><span data-stu-id="76ab8-151">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="76ab8-152">Można zapisać który jako tych dwóch metod:</span><span class="sxs-lookup"><span data-stu-id="76ab8-152">You could write that as these two methods:</span></span>

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
    while (index++ < 10)
        if (index % 2 == 1)
            yield return index;
}
```
 
<span data-ttu-id="76ab8-153">Przyjrzyj się powyżej metod.</span><span class="sxs-lookup"><span data-stu-id="76ab8-153">Look at the methods above.</span></span> <span data-ttu-id="76ab8-154">Pierwszy korzysta ze standardu `return` instrukcji, aby zwrócić pustą kolekcję lub iteratora tworzone przez metodę drugiego.</span><span class="sxs-lookup"><span data-stu-id="76ab8-154">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="76ab8-155">W drugiej metodzie `yield return` instrukcji można utworzyć żądanego sekwencji.</span><span class="sxs-lookup"><span data-stu-id="76ab8-155">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="76ab8-156">Bardziej zgłębić temat do`foreach`</span><span class="sxs-lookup"><span data-stu-id="76ab8-156">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="76ab8-157">`foreach` Instrukcji rozwija na standardowe idiom, która używa `IEnumable<T>` i `IEnumerator<T>` interfejsów w celu iteracji przez wszystkie elementy kolekcji.</span><span class="sxs-lookup"><span data-stu-id="76ab8-157">The `foreach` statement expands into a standard idiom that uses the `IEnumable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="76ab8-158">Zmniejsza on również błędów, które deweloperzy tworzą przez nie zostało prawidłowo zarządzania zasobami.</span><span class="sxs-lookup"><span data-stu-id="76ab8-158">It also  minimizes errors developers make by not properly managing resources.</span></span> 

<span data-ttu-id="76ab8-159">Kompilator tłumaczy `foreach` pokazano w przykładzie pierwszy na podobny do tej konstrukcji pętli:</span><span class="sxs-lookup"><span data-stu-id="76ab8-159">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="76ab8-160">Konstrukcja powyżej reprezentuje kod wygenerowany przez kompilator języka C# lub nowszym w wersji 5 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="76ab8-160">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="76ab8-161">Przed w wersji 5 `item` zmienna ma inny zakres:</span><span class="sxs-lookup"><span data-stu-id="76ab8-161">Prior to version 5, the `item` variable had a different scope:</span></span>

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

<span data-ttu-id="76ab8-162">Ta zmiana została wprowadzona, ponieważ wcześniej zachowanie może prowadzić do delikatny i trudne do diagnozowanie błędów dotyczących wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="76ab8-162">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="76ab8-163">Zobacz sekcję dotyczącą [wyrażenia lambda](lambda-expressions.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="76ab8-163">See the section on [lambda expressions](lambda-expressions.md) for more information.</span></span> 

<span data-ttu-id="76ab8-164">Dokładny kod wygenerowany przez kompilator jest nieco bardziej skomplikowane i obsługuje sytuacje, gdy obiekt jest zwracany przez `GetEnumerator()` implementuje `IDisposable` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="76ab8-164">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="76ab8-165">Pełnym rozszerzeniu generuje kod więcej następująco:</span><span class="sxs-lookup"><span data-stu-id="76ab8-165">The full expansion generates code more like this:</span></span>

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

<span data-ttu-id="76ab8-166">Sposób, w której moduł wyliczający jest usuwane jest zależna od właściwości typu `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="76ab8-166">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="76ab8-167">W przypadku ogólnych `finally` klauzuli rozwijany do:</span><span class="sxs-lookup"><span data-stu-id="76ab8-167">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

<span data-ttu-id="76ab8-168">Jednak jeśli typ `enumerator` jest zapieczętowanego typu i nie jest niejawna konwersja z typu `enumerator` do `IDisposable`, `finally` klauzuli rozwijany do bloku pusta:</span><span class="sxs-lookup"><span data-stu-id="76ab8-168">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>
```csharp
finally 
{
} 
```

<span data-ttu-id="76ab8-169">Jeśli istnieje niejawna konwersja z typu `enumerator` do `IDisposable`, i `enumerator` jest typem wartości niedopuszczającym `finally` klauzuli rozwijany do:</span><span class="sxs-lookup"><span data-stu-id="76ab8-169">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

<span data-ttu-id="76ab8-170">Thankfully nie trzeba pamiętać te szczegóły.</span><span class="sxs-lookup"><span data-stu-id="76ab8-170">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="76ab8-171">`foreach` Instrukcji obsługuje te wszystkie szczegóły dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="76ab8-171">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="76ab8-172">Kompilator wygeneruje prawidłowego kodu dla każdego z tych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="76ab8-172">The compiler will generate the correct code for any of these constructs.</span></span> 


