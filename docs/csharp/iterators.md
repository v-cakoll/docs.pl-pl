---
title: Iteratory
description: Dowiedz się, jak używać wbudowanych C# Iteratory oraz jak tworzyć swoje własne metody iteratora niestandardowych.
ms.date: 06/20/2016
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 37ed45fc563eacf0c6bf412dcfb28dbc6db2bb17
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58126048"
---
# <a name="iterators"></a><span data-ttu-id="2fb5f-103">Iteratory</span><span class="sxs-lookup"><span data-stu-id="2fb5f-103">Iterators</span></span>

<span data-ttu-id="2fb5f-104">Prawie każdy program, który napiszesz będzie miał pewne konieczność iteracji po kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="2fb5f-105">Napiszesz kod, który sprawdza, czy każdy element w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-105">You'll write code that examines every item in a collection.</span></span> 

<span data-ttu-id="2fb5f-106">Utworzysz też metody iteratora, które są metodami, które tworzy iterator dla elementów tej klasy.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-106">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="2fb5f-107">Mogą one być używane dla:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-107">These can be used for:</span></span>

+ <span data-ttu-id="2fb5f-108">Wykonując akcję dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="2fb5f-109">Wyliczanie kolekcji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="2fb5f-110">Rozszerzanie [LINQ](linq/index.md) lub inne biblioteki.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="2fb5f-111">Tworzenie potoku danych, gdzie dane przepływają efektywnie za pośrednictwem metody iteratora.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="2fb5f-112">C# Język oferuje funkcje dla obu tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="2fb5f-113">Ten artykuł zawiera omówienie tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="2fb5f-114">W tym samouczku składa się z wielu kroków.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="2fb5f-115">Po każdym kroku możesz uruchomić aplikację i wyświetlić postęp.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="2fb5f-116">Możesz również [wyświetlanie lub Pobieranie ukończone przykładowe](https://github.com/dotnet/samples/blob/master/csharp/iterators) w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/master/csharp/iterators) for this topic.</span></span> <span data-ttu-id="2fb5f-117">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="2fb5f-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="2fb5f-118">Iterowanie za pomocą instrukcji foreach</span><span class="sxs-lookup"><span data-stu-id="2fb5f-118">Iterating with foreach</span></span>

<span data-ttu-id="2fb5f-119">Wyliczanie kolekcji jest prosty: `foreach` — Słowo kluczowe wylicza kolekcji, wykonywania osadzona instrukcja jeden raz dla każdego elementu w kolekcji:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="2fb5f-120">To wszystko jest do niego.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-120">That's all there is to it.</span></span> <span data-ttu-id="2fb5f-121">Iterowanie cała zawartość kolekcji, `foreach` instrukcja to wszystko, czego potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="2fb5f-122">`foreach` Instrukcja nie jest magic, mimo że.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="2fb5f-123">Opiera się na dwóch interfejsach ogólnych zdefiniowane w bibliotece programu .NET core w celu wygenerowania kodu niezbędne do iteracji kolekcji: `IEnumerable<T>` i `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="2fb5f-124">Ten mechanizm jest opisano szczegółowo poniżej.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="2fb5f-125">Oba te interfejsy mają również odpowiedniki nieogólnego: `IEnumerable` i `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="2fb5f-126">[Ogólny](programming-guide/generics/index.md) wersje są preferowane dla nowoczesnego kodu.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="2fb5f-127">Wyliczenie źródeł za pomocą metody iteratora</span><span class="sxs-lookup"><span data-stu-id="2fb5f-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="2fb5f-128">Kolejną atrakcyjną funkcją C# języka umożliwia tworzenie metody tworzące źródła dla wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="2fb5f-129">Są one określane jako *metody iteracyjne*.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="2fb5f-130">Metoda iteratora jest definiuje sposób generowania obiekty w kolejności, w przypadku żądania.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="2fb5f-131">Możesz użyć `yield return` kontekstowymi słowami kluczowymi, aby zdefiniować metodę iteratora.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-131">You use the `yield return` contextual keywords to define an iterator method.</span></span> 

<span data-ttu-id="2fb5f-132">Można zapisać tę metodę, aby utworzyć sekwencję liczb całkowitych z zakresu od 0 do 9:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

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

<span data-ttu-id="2fb5f-133">Powyższy kod przedstawia różne `yield return` instrukcji, aby wyróżnić faktów, których można używać wielu dyskretnych `yield return` instrukcji w metodzie iteratora.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="2fb5f-134">Można (i często tak robią) korzystanie z innych konstrukcji językowych w celu uproszczenia kodu metody iteratora.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="2fb5f-135">Poniżej definicję metody generuje dokładnie tej samej sekwencji liczb:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

<span data-ttu-id="2fb5f-136">Nie trzeba zdecydować z jednej z nich.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="2fb5f-137">Masz tyle `yield return` instrukcji, co jest niezbędne do potrzeb Twojej formy:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

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

<span data-ttu-id="2fb5f-138">To podstawowa składnia.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-138">That's the basic syntax.</span></span> <span data-ttu-id="2fb5f-139">Rozważmy przykład rzeczywistych, w którym należy napisać metodę iteratora.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="2fb5f-140">Wyobraź sobie, możesz teraz projektu IoT i czujników urządzenia generować bardzo duże strumienia danych.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="2fb5f-141">Aby można było uzyskać pewne pojęcie dla danych, można napisać metodę, która pobiera próbki każdy element danych n-ty.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="2fb5f-142">Ta metoda iteratora małych wykonuje lewy:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-142">This small iterator method does the trick:</span></span>

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

<span data-ttu-id="2fb5f-143">Istnieje jeden ważne ograniczenia metody iteracyjne: nie może posiadać równocześnie `return` instrukcji i `yield return` instrukcji w tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="2fb5f-144">Następujące nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-144">The following will not compile:</span></span>

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

<span data-ttu-id="2fb5f-145">To ograniczenie jest zwykle problemem.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="2fb5f-146">Masz do wyboru przy użyciu `yield return` w całej metody lub rozdzielając oryginalnej metody na wiele sposobów, za pomocą niektórych `return`, a niektóre przy użyciu `yield return`.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="2fb5f-147">Możesz zmodyfikować ostatnie metoda nieco `yield return` wszędzie:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

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
 
<span data-ttu-id="2fb5f-148">Czasami prawidłowej odpowiedzi jest podzielić metodę iteratora na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="2fb5f-149">Jedną, która używa `return`oraz drugiego, który używa `yield return`.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="2fb5f-150">Rozważmy sytuację, w których warto zwrócić pustą kolekcję lub 5 pierwszych liczby nieparzyste, w oparciu o argument logiczny.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="2fb5f-151">Można napisać, jako tych dwóch metod:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-151">You could write that as these two methods:</span></span>

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
 
<span data-ttu-id="2fb5f-152">Spójrz na powyższych metod.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-152">Look at the methods above.</span></span> <span data-ttu-id="2fb5f-153">Pierwszy używa standardowych `return` instrukcji, aby zwrócić pustą kolekcję lub iteratora, tworzone przez metodę drugiego.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="2fb5f-154">W drugiej metodzie `yield return` instrukcję, aby utworzyć żądany sekwencji.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="2fb5f-155">Bardziej zgłębić temat do `foreach`</span><span class="sxs-lookup"><span data-stu-id="2fb5f-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="2fb5f-156">`foreach` Instrukcji rozwija się na standardowych idiom, który używa `IEnumerable<T>` i `IEnumerator<T>` interfejsy do iteracji dla wszystkich elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="2fb5f-157">Minimalizuje błędy, które deweloperzy mogą stosować przez nie został poprawnie zarządzanie zasobami.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-157">It also  minimizes errors developers make by not properly managing resources.</span></span> 

<span data-ttu-id="2fb5f-158">Kompilator tłumaczy `foreach` pętli wyświetlane w pierwszym przykładzie w sposób podobny do tej konstrukcji:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="2fb5f-159">Konstrukcja powyżej reprezentuje kod wygenerowany przez C# kompilatora, począwszy od wersji 5 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="2fb5f-160">Przed wersją 5 `item` zmienna ma inny zakres:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-160">Prior to version 5, the `item` variable had a different scope:</span></span>

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

<span data-ttu-id="2fb5f-161">Ta zmiana została wprowadzona, ponieważ wcześniej zachowanie może prowadzić do subtelnym, trudno Diagnozuj błędy dotyczące wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="2fb5f-162">Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2fb5f-162">For more information about lambda expressions, see [Lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="2fb5f-163">Dokładne kod wygenerowany przez kompilator jest nieco bardziej skomplikowane i obsługuje sytuacje, gdy obiekt jest zwracany przez `GetEnumerator()` implementuje `IDisposable` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="2fb5f-164">Pełnym rozszerzeniu generuje kod więcej następująco:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-164">The full expansion generates code more like this:</span></span>

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

<span data-ttu-id="2fb5f-165">Sposób, w którym moduł wyliczający jest usunięty zależy cechy typu `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="2fb5f-166">W przypadku ogólnych `finally` klauzula jest rozszerzany, aby:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

<span data-ttu-id="2fb5f-167">Jednak jeśli typ `enumerator` jest typie zapieczętowanym i istnieje niejawna konwersja z typu `enumerator` do `IDisposable`, `finally` klauzuli rozwija do pustego bloku:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>
```csharp
finally 
{
} 
```

<span data-ttu-id="2fb5f-168">Jeśli istnieje niejawna konwersja z typu `enumerator` do `IDisposable`, i `enumerator` jest typem wartości niedopuszczającym wartości `finally` klauzula jest rozszerzany, aby:</span><span class="sxs-lookup"><span data-stu-id="2fb5f-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

<span data-ttu-id="2fb5f-169">Szczęście nie trzeba pamiętać te szczegóły.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="2fb5f-170">`foreach` Instrukcja obsługuje te szczegóły skutecznego dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="2fb5f-171">Kompilator wygeneruje poprawny kod dla każdej z tych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="2fb5f-171">The compiler will generate the correct code for any of these constructs.</span></span> 


