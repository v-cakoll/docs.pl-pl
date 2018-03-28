---
title: Praca z LINQ
description: W tym samouczku jest przedstawienie sposobu generowania sekwencji za pomocą LINQ, zapisać metod do użycia w zapytaniach LINQ i rozróżnienia oceny wczesny i opóźnieniem.
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/28/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: c5720d5391eec327aa2f885fd65579aeb6260488
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="working-with-linq"></a><span data-ttu-id="8fc7b-104">Praca z LINQ</span><span class="sxs-lookup"><span data-stu-id="8fc7b-104">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="8fc7b-105">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8fc7b-105">Introduction</span></span>

<span data-ttu-id="8fc7b-106">Ten samouczek zawiera szereg funkcji .NET Core i języka C#.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="8fc7b-107">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-107">You’ll learn:</span></span>

*   <span data-ttu-id="8fc7b-108">Sposób generowania sekwencji za pomocą LINQ</span><span class="sxs-lookup"><span data-stu-id="8fc7b-108">How to generate sequences with LINQ</span></span>
*   <span data-ttu-id="8fc7b-109">Jak napisać metody, które mogą być łatwo używane w zapytaniach LINQ.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-109">How to write methods that can be easily used in LINQ queries.</span></span>
*   <span data-ttu-id="8fc7b-110">Jak rozróżnienia oceny wczesny i opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-110">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="8fc7b-111">Te techniki dowiesz się, tworząc aplikację prezentującą podstawowe umiejętności żadnych magician: [losowa faro](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="8fc7b-111">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="8fc7b-112">Krótko mówiąc losowa faro to technika gdzie podzielić talii karty dokładnie w połowie, a następnie losowa przeplata każdego jednej karty z każdej połowy odbudować talii oryginalnego.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-112">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="8fc7b-113">Magicians użyć tej metody, ponieważ wszystkie karty w znanej lokalizacji po każdym losowa, a kolejność jest powtarzane wzorca.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-113">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span> 

<span data-ttu-id="8fc7b-114">W celach naszych jest światła hearted przyjrzeć się manipulowanie sekwencji danych.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-114">For our purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="8fc7b-115">Aplikację, która będzie kompilacji zostanie skonstruować talii kart, a następnie wykonaj sekwencję przesuwa zapisywania sekwencji zawsze wtedy.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-115">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="8fc7b-116">Będzie także porównać zaktualizowane kolejności do oryginalnego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-116">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="8fc7b-117">Ten samouczek ma wiele kroków.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-117">This tutorial has multiple steps.</span></span> <span data-ttu-id="8fc7b-118">Po każdym kroku możesz uruchomić aplikację i wyświetlany jest postęp.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-118">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="8fc7b-119">Możesz również sprawdzić [ukończone próbki](https://github.com/dotnet/docs/blob/master/samples/csharp/getting-started/console-linq) w repozytorium GitHub dotnet/docs.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-119">You can also see the [completed sample](https://github.com/dotnet/docs/blob/master/samples/csharp/getting-started/console-linq) in the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="8fc7b-120">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="8fc7b-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8fc7b-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8fc7b-121">Prerequisites</span></span>

<span data-ttu-id="8fc7b-122">Należy skonfigurować komputer, aby uruchomić oprogramowanie .NET core.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-122">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="8fc7b-123">Instrukcje instalacji można znaleźć na [.NET Core](https://www.microsoft.com/net/core) strony.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-123">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="8fc7b-124">Można uruchomić tej aplikacji, w systemie Windows, Ubuntu Linux, OS X lub w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-124">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="8fc7b-125">Należy zainstalować w edytorze kodu dotyczącego elementów ulubionych.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-125">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="8fc7b-126">Opisy poniżej użyj [Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-126">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="8fc7b-127">Można jednak użyć dowolnego narzędzia potrafisz.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-127">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="8fc7b-128">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="8fc7b-128">Create the Application</span></span>

<span data-ttu-id="8fc7b-129">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-129">The first step is to create a new application.</span></span> <span data-ttu-id="8fc7b-130">Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-130">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="8fc7b-131">Upewnij się, że sposób bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-131">Make that the current directory.</span></span> <span data-ttu-id="8fc7b-132">Wpisz polecenie `dotnet new console` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-132">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="8fc7b-133">Spowoduje to utworzenie plików starter podstawowe aplikacji "Hello World".</span><span class="sxs-lookup"><span data-stu-id="8fc7b-133">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="8fc7b-134">Jeśli nie znasz języka C#, [w tym samouczku](console-teleprompter.md) wyjaśnienie struktury programu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-134">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="8fc7b-135">Może odczytywać, który i następnie wróć tutaj, aby dowiedzieć się więcej na temat LINQ.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-135">You can read that and then return here to learn more about LINQ.</span></span> 

## <a name="creating-the-data-set"></a><span data-ttu-id="8fc7b-136">Tworzenie zestawu danych</span><span class="sxs-lookup"><span data-stu-id="8fc7b-136">Creating the Data Set</span></span>

<span data-ttu-id="8fc7b-137">Zacznijmy od utworzenia zbiór kart.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-137">Let's start by creating a deck of cards.</span></span> <span data-ttu-id="8fc7b-138">Należy to zrobić to przy użyciu zapytania LINQ, która ma dwa źródła (po jednej dla czterech kolorów, jeden dla trzynaście wartości).</span><span class="sxs-lookup"><span data-stu-id="8fc7b-138">You'll do this using a LINQ query that has two sources (one for the four suits, one for the thirteen values).</span></span> <span data-ttu-id="8fc7b-139">Tych źródeł będzie łączyć w talii 52 karty.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-139">You'll combine those sources into a 52 card deck.</span></span> <span data-ttu-id="8fc7b-140">A `Console.WriteLine` instrukcja wewnątrz `foreach` pętli Wyświetla karty.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-140">A `Console.WriteLine` statement inside a `foreach` loop displays the cards.</span></span>

<span data-ttu-id="8fc7b-141">Oto zapytania:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-141">Here's the query:</span></span>

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

<span data-ttu-id="8fc7b-142">Wielokrotność `from` utworzyć klauzule `SelectMany`, co powoduje pojedynczego ciągu z łączenie każdego elementu w pierwszej kolejności z każdego elementu w drugim sekwencji.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-142">The multiple `from` clauses produce a `SelectMany`, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="8fc7b-143">Kolejność jest ważna dla naszych celów.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-143">The order is important for our purposes.</span></span> <span data-ttu-id="8fc7b-144">Pierwszym elementem w pierwszym sekwencji źródłowej (mechanizmy) jest połączona z każdym elementem w drugim sekwencji (wartości).</span><span class="sxs-lookup"><span data-stu-id="8fc7b-144">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Values).</span></span> <span data-ttu-id="8fc7b-145">Daje to wszystkich kart trzynaście koloru pierwszego.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-145">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="8fc7b-146">Ten proces jest powtarzany z każdego elementu w pierwszym sekwencji (mechanizmy).</span><span class="sxs-lookup"><span data-stu-id="8fc7b-146">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="8fc7b-147">W rezultacie jest talii kart uporządkowanych według kolorów, a następnie według wartości.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-147">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="8fc7b-148">Następnie należy utworzyć metody Suits() i Ranks().</span><span class="sxs-lookup"><span data-stu-id="8fc7b-148">Next, you'll need to build the Suits() and Ranks() methods.</span></span> <span data-ttu-id="8fc7b-149">Zacznijmy od naprawdę proste zbiór *metody iteracyjne* który Generowanie sekwencji jako element wyliczalny z ciągami:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-149">Let's start with a really simple set of *iterator methods* that generate the sequence as an enumerable of strings:</span></span>

```csharp
static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

<span data-ttu-id="8fc7b-150">Korzystanie z tych dwóch metod zarówno `yield return` składnię, aby utworzyć sekwencję podczas ich działania.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-150">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="8fc7b-151">Kompilator tworzy obiekt, który implementuje `IEnumerable<T>` i generuje sekwencję ciągów, ponieważ są one wymagane.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-151">The compiler builds an object that implements `IEnumerable<T>` and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="8fc7b-152">Przejdź dalej i uruchom na tym etapie konstruowania próbki.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-152">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="8fc7b-153">Będzie ono wszystkie 52 karty w talii.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-153">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="8fc7b-154">Może być bardzo przydatne do uruchomienia tego przykładu w debugerze, aby przyjrzeć się jak `Suits()` i `Values()` wykonania metody.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-154">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Values()` methods execute.</span></span> <span data-ttu-id="8fc7b-155">Wyraźnie widać, że każdy ciąg każdej sekwencji jest generowany tylko wtedy, gdy jest to potrzebne.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-155">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Okno konsoli aplikacji wypisywanie 52 kart](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="8fc7b-157">Manipulowanie kolejności</span><span class="sxs-lookup"><span data-stu-id="8fc7b-157">Manipulating the Order</span></span>

<span data-ttu-id="8fc7b-158">Następnie utworzymy metody narzędzia, która może przeprowadzać losowa.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-158">Next, let's build a utility method that can perform the shuffle.</span></span> <span data-ttu-id="8fc7b-159">Pierwszym krokiem jest podzielenie talii w dwóch.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-159">The first step is to split the deck in two.</span></span> <span data-ttu-id="8fc7b-160">`Take()` i `Skip()` metod, które są częścią interfejsów API LINQ zapewnienia tej funkcji nam:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-160">The `Take()` and `Skip()` methods that are part of the LINQ APIs provide that feature for us:</span></span>

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

<span data-ttu-id="8fc7b-161">Metoda losowa nie istnieje w biblioteki standardowej, będzie trzeba napisać własne.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-161">The shuffle method doesn't exist in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="8fc7b-162">Ta nowa metoda przedstawiono kilka technik, które będą używane z programów opartych na LINQ, więc warto wyjaśnić, każdego częścią metody w krokach.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-162">This new method illustrates several techniques that you'll use with LINQ-based programs, so let's explain each part of the method in steps.</span></span>

<span data-ttu-id="8fc7b-163">Podpis metody tworzy *— metoda rozszerzenia*:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-163">The signature for the method creates an *extension method*:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="8fc7b-164">Metody rozszerzenia jest specjalnego przeznaczenia *metody statycznej.*</span><span class="sxs-lookup"><span data-stu-id="8fc7b-164">An extension method is a special purpose *static method.*</span></span> <span data-ttu-id="8fc7b-165">Zostanie wyświetlony dodanie `this` modyfikator na pierwszy argument do metody.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-165">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="8fc7b-166">Oznacza to, że należy wywołać metodę tak, jakby była metody elementu członkowskiego typu pierwszy argument.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-166">That means you call the method as though it were a member method of the type of the first argument.</span></span>

<span data-ttu-id="8fc7b-167">Metody rozszerzenia mogą być deklarowane tylko wewnątrz `static` klas, więc warto utworzyć nowe klasy statycznej o nazwie `extensions` dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-167">Extension methods can be declared only inside `static` classes, so let's create a new static class called `extensions` for this functionality.</span></span> <span data-ttu-id="8fc7b-168">Dodasz więcej metod rozszerzenia nadal w tym samouczku, a te zostaną umieszczone w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-168">You'll add more extension methods as you continue this tutorial, and those will be placed in the same class.</span></span>

<span data-ttu-id="8fc7b-169">Ta deklaracja metody również następuje standardowe idiom gdzie typy wejściowe i wyjściowe są `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-169">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="8fc7b-170">Czy rozwiązanie umożliwia tworzenie łańcucha metody LINQ ze sobą w celu wykonywania bardziej złożonych zapytań.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-170">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

```csharp
using System.Collections.Generic;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>
            (this IEnumerable<T> first, IEnumerable<T> second)
        {
            // implementation coming.
        }
    }
}
```

<span data-ttu-id="8fc7b-171">Będzie można wyliczania sekwencji obu na raz, naprzemiennego wykonywania elementów i tworzenie jeden obiekt.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-171">You will be enumerating both sequences at once, interleaving the elements, and creating one object.</span></span>  <span data-ttu-id="8fc7b-172">Pisanie zapytań LINQ metodę, która współdziała z dwóch sekwencji wymaga, że rozumiesz, jak `IEnumerable` działa.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-172">Writing a LINQ method that works with two sequences requires that you understand how `IEnumerable` works.</span></span>

<span data-ttu-id="8fc7b-173">`IEnumerable` Interfejs ma jedną metodę: `GetEnumerator()`.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-173">The `IEnumerable` interface has one method: `GetEnumerator()`.</span></span> <span data-ttu-id="8fc7b-174">Obiekt zwrócony przez `GetEnumerator()` ma metodę, aby przejść do następnego elementu i właściwości, która pobiera bieżący element w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-174">The object returned by `GetEnumerator()` has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="8fc7b-175">Użyjesz tych dwóch członków wyliczyć kolekcji, a następnie wróć elementów.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-175">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="8fc7b-176">Ta metoda przeplotu będzie metodę iteratora, zamiast tworzenia kolekcji i zwracanie kolekcji, użyjesz `yield return` składni przedstawionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-176">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span> 

<span data-ttu-id="8fc7b-177">Oto implementacja tej metody:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-177">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="8fc7b-178">Teraz, gdy napisanych tej metody, wróć do `Main` — metoda i losowa talii raz:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-178">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

```csharp
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a><span data-ttu-id="8fc7b-179">Porównania</span><span class="sxs-lookup"><span data-stu-id="8fc7b-179">Comparisons</span></span>

<span data-ttu-id="8fc7b-180">Zobaczmy, ile przesuwa zajmuje można ustawić talii z powrotem do jej oryginalnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-180">Let's see how many shuffles it takes to set the deck back to its original order.</span></span> <span data-ttu-id="8fc7b-181">Będzie konieczne napisanie metody, która określa, czy dwie sekwencje mają takie same.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-181">You'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="8fc7b-182">Po utworzeniu tej metody należy umieścić kod, który shuffles talii w pętli i sprawdź, gdy jest talii w kolejności.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-182">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="8fc7b-183">Pisanie metodę, aby ustalić, czy dwie sekwencje są równe powinna być prosta.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-183">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="8fc7b-184">Jest strukturze podobnej metody, którą zapisano losowo talii.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-184">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="8fc7b-185">Teraz, zamiast yield zwracanie każdego elementu, można będzie porównywać tylko zgodnych elementów w każdej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-185">Only this time, instead of yield returning each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="8fc7b-186">Sekwencje całą sekwencję wyliczeniu, jeśli pasuje do każdego elementu, są takie same:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-186">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="8fc7b-187">Oznacza to, drugi idiom Linq: metody terminala.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-187">This shows a second Linq idiom: terminal methods.</span></span> <span data-ttu-id="8fc7b-188">Podejmij sekwencji jako dane wejściowe (lub w tym przypadku dwóch sekwencji) i zwraca pojedynczą wartość skalarną.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-188">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="8fc7b-189">Te metody, gdy są one używane są zawsze metodę końcową zapytania.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-189">These methods, when they are used, are always the final method of a query.</span></span> <span data-ttu-id="8fc7b-190">(Stąd nazwa).</span><span class="sxs-lookup"><span data-stu-id="8fc7b-190">(Hence the name).</span></span> 

<span data-ttu-id="8fc7b-191">Widać to w akcji używanej do określania, kiedy talii jest w jej oryginalnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-191">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="8fc7b-192">Umieść kod losowa wewnątrz pętli i Zatrzymaj, gdy sekwencja jest w jej oryginalnej kolejności, stosując `SequenceEquals()` metody.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-192">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="8fc7b-193">Można zauważyć, że zawsze powinien być ostatnią metodą każde zapytanie operacji, ponieważ zwraca pojedynczą wartość zamiast sekwencji:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-193">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

```csharp
var times = 0;
var shuffle = startingDeck;

do
{
    shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    times++;
} while (!startingDeck.SequenceEquals(shuffle));

Console.WriteLine(times);
```

<span data-ttu-id="8fc7b-194">Uruchom próbkę i zobacz, jak talii Reorganizuje na każdym losowa, dopóki zwróci oryginalnej konfiguracji po 8 iteracji.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-194">Run the sample, and see how the deck rearranges on each shuffle, until it returns to its original configuration after 8 iterations.</span></span>

## <a name="optimizations"></a><span data-ttu-id="8fc7b-195">Optymalizacje</span><span class="sxs-lookup"><span data-stu-id="8fc7b-195">Optimizations</span></span>

<span data-ttu-id="8fc7b-196">Wykonuje próbki zostały już utworzone w do tej pory *w losowo*, gdzie kart górny i dolny nie zmieniają się przy każdym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-196">The sample you've built so far executes an *in shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="8fc7b-197">Można wprowadzić zmiany, i uruchom *limit losowa*, w którym wszystkie karty 52 zmienić położenie.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-197">Let's make one change, and run an *out shuffle*, where all 52 cards change position.</span></span> <span data-ttu-id="8fc7b-198">Dla poza losowa, możesz interleave talii tak, aby pierwszy karty w dolnej połowie staje się pierwszym karty w talii.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-198">For an out shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="8fc7b-199">Oznacza to, że ostatni karty w górnej połowie staje się karty dolnej.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-199">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="8fc7b-200">To jest tylko jeden wiersz zmiany.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-200">That's just a one line change.</span></span> <span data-ttu-id="8fc7b-201">Aktualizacja wywołanie losowo, aby zmienić kolejność górny i dolny połowy talii:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-201">Update the call to shuffle to change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="8fc7b-202">Ponownie uruchom program, i zobaczysz trwa 52 iteracji w celu talii zmienić kolejność samej siebie.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-202">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="8fc7b-203">Będzie również uruchomić należy zauważyć niektórych degradations obniżyć wydajność, ponieważ program będzie kontynuował działanie.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-203">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="8fc7b-204">Istnieje wiele przyczyn tej.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-204">There are a number of reasons for this.</span></span> <span data-ttu-id="8fc7b-205">Umożliwia spełnienia jednego z głównych powodów: nieefektywne użycie *obliczanie leniwe*.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-205">Let's tackle one of the major causes: inefficient use of *lazy evaluation*.</span></span>

<span data-ttu-id="8fc7b-206">Zapytania LINQ są oceniane w trybie opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-206">LINQ queries are evaluated lazily.</span></span> <span data-ttu-id="8fc7b-207">Sekwencje są generowane tylko wtedy, gdy elementy są wymagane.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-207">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="8fc7b-208">Zwykle, który jest główną zaletą LINQ.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-208">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="8fc7b-209">Jednak użycie takich jak ten program, powoduje wykładniczym wzrostem czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-209">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="8fc7b-210">Oryginalny talii został wygenerowany za pomocą zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-210">The original deck was generated using a LINQ query.</span></span> <span data-ttu-id="8fc7b-211">Każdy losowa jest generowany przez wykonywanie zapytań LINQ trzy na poprzedniej talii.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-211">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="8fc7b-212">Wszystkie te są wykonywane w trybie opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-212">All these are performed lazily.</span></span> <span data-ttu-id="8fc7b-213">Oznacza to również, że są wykonywane ponownie każdym razem, gdy wymagany jest sekwencja.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-213">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="8fc7b-214">W czasie, uzyskasz 52nd iteracji możesz jest ponownie wygenerować oryginalnego talii wiele, wiele razy.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-214">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="8fc7b-215">Napisz dziennika, aby pokazać to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-215">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="8fc7b-216">Następnie będzie napraw go.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-216">Then, you'll fix it.</span></span>

<span data-ttu-id="8fc7b-217">Oto metoda dziennika, który można dołączyć do dowolnej kwerendy do oznaczenia, że zapytanie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-217">Here's a log method that can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="8fc7b-218">Następnie Instrumentacja definicji każdego zapytania o komunikat dziennika:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-218">Next, instrument the definition of each query with a log message:</span></span>

```csharp
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        shuffle = shuffle.Skip(26)
            .LogQuery("Bottom Half")
            .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
            .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="8fc7b-219">Należy zauważyć, że nie możesz zalogować się za każdym razem, gdy dostęp zapytania.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-219">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="8fc7b-220">Możesz zalogować się wyłącznie w przypadku utworzenia oryginalne zapytanie.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-220">You log only when you create the original query.</span></span> <span data-ttu-id="8fc7b-221">Program nadal trwa długo do uruchomienia, ale spowoduje to wyświetlenie dlaczego.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-221">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="8fc7b-222">Po uruchomieniu o cierpliwość systemem zewnętrznego losowo z rejestrowaniem włączona, wrócić do losowa wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-222">If you run out of patience running the outer shuffle with logging turned on, switch back to the inner shuffle.</span></span> <span data-ttu-id="8fc7b-223">Obliczanie leniwe efekty będą nadal wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-223">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="8fc7b-224">W jednym przebiegu wykonywania kwerend 2592, w tym wszystkie wartości i koloru generacji.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-224">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="8fc7b-225">Jest to prosty sposób można zaktualizować tego programu, aby uniknąć wszystkich tych wykonania.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-225">There is an easy way to update this program to avoid all those executions.</span></span> <span data-ttu-id="8fc7b-226">Brak metody LINQ `ToArray()` i `ToList()` spowodować zapytania do uruchomienia i odpowiednio zapisane wyniki w tablicy lub na liście.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-226">There are LINQ methods `ToArray()` and `ToList()` that cause the query to run, and store the results in an array or a list, respectively.</span></span> <span data-ttu-id="8fc7b-227">Te metody umożliwiają pamięci podręcznej danych wyników zapytania, zamiast ponownie wykonaj zapytanie źródła.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-227">You use these methods to cache the data results of a query rather than execute the source query again.</span></span>  <span data-ttu-id="8fc7b-228">Dołącz zapytania generujących talii kart z wywołaniem do `ToArray()` i ponownie uruchom zapytanie:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-228">Append the queries that generate the card decks with a call to `ToArray()` and run the query again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="8fc7b-229">Uruchom ponownie, a wewnętrzny losowa jest do 30 zapytania.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-229">Run again, and the inner shuffle is down to 30 queries.</span></span> <span data-ttu-id="8fc7b-230">Uruchom ponownie, nadając zewnętrzne losowa i zobaczysz ulepszenia podobne.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-230">Run again with the outer shuffle and you'll see similar improvements.</span></span> <span data-ttu-id="8fc7b-231">(Go teraz wykonuje zapytania 162).</span><span class="sxs-lookup"><span data-stu-id="8fc7b-231">(It now executes 162 queries).</span></span>

<span data-ttu-id="8fc7b-232">Nie błędnie interpretuje planowanie, który dzielenia na uruchamiać wszystkie zapytania w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-232">Don't misinterpret this example by thinking that all queries should run eagerly.</span></span> <span data-ttu-id="8fc7b-233">W tym przykładzie jest przeznaczona do Wyróżnij przypadków użycia, w którym obliczanie leniwe może spowodować problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-233">This example is designed to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="8fc7b-234">Wynika to z każdego nowego rozmieszczenie talii składa się z poprzednim rozmieszczenia.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-234">That's because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="8fc7b-235">Przy użyciu obliczanie leniwe oznacza, że każda nowa konfiguracja talii składa się z oryginalnego talii, nawet wykonywanie kodu, który skompilowany `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-235">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="8fc7b-236">Która powoduje dużą ilość dodatkowej pracy.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-236">That causes a large amount of extra work.</span></span> 

<span data-ttu-id="8fc7b-237">W praktyce niektóre algorytmy Uruchom znacznie poprawia przy użyciu wczesny oceny, a pozostałe — znacznie poprawia przy użyciu obliczanie leniwe.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-237">In practice, some algorithms run much better using eager evaluation, and others run much better using lazy evaluation.</span></span> <span data-ttu-id="8fc7b-238">(Ogólnie rzecz biorąc, obliczanie leniwe jest znacznie lepszym rozwiązaniem gdy źródłem danych jest oddzielnych procesach, takich jak aparatu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-238">(In general, lazy evaluation is a much better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="8fc7b-239">W takich przypadkach obliczanie leniwe umożliwia bardziej złożonych zapytań można wykonać tylko jeden obiegu do procesu bazy danych.) LINQ umożliwia zarówno opóźnieniem i wczesny oceny.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-239">In those cases, lazy evaluation enables more complex queries to execute only one round trip to the database process.) LINQ enables both lazy and eager evaluation.</span></span> <span data-ttu-id="8fc7b-240">Zmierz i wybierz najlepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-240">Measure, and pick the best choice.</span></span>

## <a name="preparing-for-new-features"></a><span data-ttu-id="8fc7b-241">Przygotowywanie do nowych funkcji</span><span class="sxs-lookup"><span data-stu-id="8fc7b-241">Preparing for New Features</span></span>

<span data-ttu-id="8fc7b-242">Napisanych dla tego przykładu kodu jest przykład tworzenia prostego prototyp, który wykonuje zadanie.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-242">The code you've written for this sample is an example of creating a simple prototype that does the job.</span></span> <span data-ttu-id="8fc7b-243">Jest to doskonały sposób, aby eksplorować miejsca problem, a dla wielu funkcji, może być najlepszym rozwiązaniem trwałych.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-243">This is a great way to explore a problem space, and for many features, it may be the best permanent solution.</span></span> <span data-ttu-id="8fc7b-244">Zostały użyte *typy anonimowe* dla kart, a każda karta jest reprezentowana przez parametry.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-244">You've leveraged *anonymous types* for the cards, and each card is represented by strings.</span></span>

<span data-ttu-id="8fc7b-245">*Typy anonimowe* mają wiele zalet wydajności.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-245">*Anonymous Types* have many productivity advantages.</span></span> <span data-ttu-id="8fc7b-246">Nie trzeba zdefiniować klasę samodzielnie do reprezentowania magazynu.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-246">You don't need to define a class yourself to represent the storage.</span></span> <span data-ttu-id="8fc7b-247">Kompilator generuje typ dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-247">The compiler generates the type for you.</span></span> <span data-ttu-id="8fc7b-248">Typ wygenerowanego przez kompilator używa wielu najlepszych rozwiązań dotyczących obiektów proste danych.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-248">The compiler generated type utilizes many of the best practices for simple data objects.</span></span> <span data-ttu-id="8fc7b-249">Ma ona *niezmienialnych*, co oznacza, że żaden z jego właściwości można zmienić po ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-249">It's *immutable*, meaning that none of its properties can be changed after it has been constructed.</span></span> <span data-ttu-id="8fc7b-250">Typy anonimowe są wewnętrzne dla zestawu, więc nie są one widoczne jako część publicznego interfejsu API dla tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-250">Anonymous types are internal to an assembly, so they aren't seen as part of the public API for that assembly.</span></span> <span data-ttu-id="8fc7b-251">Typy anonimowe zawierają również zastąpienia z `ToString()` metodę, która zwraca ciąg sformatowany z każdej wartości.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-251">Anonymous types also contain an override of the `ToString()` method that returns a formatted string with each of the values.</span></span>

<span data-ttu-id="8fc7b-252">Typy anonimowe ma także wady.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-252">Anonymous types also have disadvantages.</span></span> <span data-ttu-id="8fc7b-253">Nie ma nazw dostępnych, więc nie można ich użyć jako wartości zwracane lub argumentów.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-253">They don't have accessible names, so you can't use them as return values or arguments.</span></span> <span data-ttu-id="8fc7b-254">Można zauważyć, które żadnych metod powyżej używane te typy anonimowe są metody ogólne.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-254">You'll notice that any methods above that used these anonymous types are generic methods.</span></span> <span data-ttu-id="8fc7b-255">Zastąpienie z `ToString()` nie może być mają zgodnie z większą liczbą funkcji rozwoju aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-255">The override of `ToString()` may not be what you want as the application grows more features.</span></span> 

<span data-ttu-id="8fc7b-256">Przykład również używa ciągów dla kolor a rangą każdej karty.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-256">The sample also uses strings for the suit and the rank of each card.</span></span> <span data-ttu-id="8fc7b-257">Która jest otwarta dość zakończone.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-257">That's quite open ended.</span></span> <span data-ttu-id="8fc7b-258">System typów języka C# mogą pomóc nam w ulepszaniu lepsze kodu, wykorzystując `enum` typy dla tych wartości.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-258">The C# type system can help us make better code, by leveraging `enum` types for those values.</span></span>

<span data-ttu-id="8fc7b-259">Rozpocznij od kolory.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-259">Start with the suits.</span></span> <span data-ttu-id="8fc7b-260">Jest to idealne czas na użycie `enum`:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-260">This is a perfect time to use an `enum`:</span></span>

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

<span data-ttu-id="8fc7b-261">`Suits()` Metody również zmianę typu i implementacji:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-261">The `Suits()` method also changes type and implementation:</span></span>

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

<span data-ttu-id="8fc7b-262">Następnie wykonaj te same zmiany o randze kart:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-262">Next, do the same change with the Rank of the cards:</span></span>

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

<span data-ttu-id="8fc7b-263">I metoda generuje je:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-263">And the method that generates them:</span></span>

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

<span data-ttu-id="8fc7b-264">Jako jeden końcowego oczyszczania można wprowadzić typu do reprezentowania karty, zdejmując to zadanie typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-264">As one final cleanup, let's make a type to represent the card, instead of relying on an anonymous type.</span></span> <span data-ttu-id="8fc7b-265">Typy anonimowe są bardzo niewielka, lokalne typów, ale w tym przykładzie karty do gry jest jednym z głównych pojęć.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-265">Anonymous types are great for lightweight, local types, but in this example, the playing card is one of the main concepts.</span></span> <span data-ttu-id="8fc7b-266">Należy go konkretnego typu.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-266">It should be a concrete type.</span></span>

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

<span data-ttu-id="8fc7b-267">Ten typ używa *automatycznie implementowane właściwości tylko do odczytu* które są ustawiane w konstruktorze, a następnie nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-267">This type uses *auto-implemented read-only properties* which are set in the constructor, and then cannot be modified.</span></span> <span data-ttu-id="8fc7b-268">On również sprawia, że użycie [ciągu interpolacji](../language-reference/tokens/interpolated.md) funkcja, która ułatwia format ciąg w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-268">It also makes use of the [string interpolation](../language-reference/tokens/interpolated.md) feature that makes it easier to format string output.</span></span>

<span data-ttu-id="8fc7b-269">Zaktualizuj zapytanie, które generuje początkowy talii do użycia nowego typu:</span><span class="sxs-lookup"><span data-stu-id="8fc7b-269">Update the query that generates the starting deck to use the new type:</span></span>

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

<span data-ttu-id="8fc7b-270">Skompiluj i uruchom ponownie.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-270">Compile and run again.</span></span> <span data-ttu-id="8fc7b-271">Dane wyjściowe są nieco bardziej przejrzyste i kod jest bardziej wyczyść i można ją rozszerzyć, co ułatwia.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-271">The output is a little cleaner, and the code is a bit more clear and can be extended more easily.</span></span>

## <a name="conclusion"></a><span data-ttu-id="8fc7b-272">Wniosek</span><span class="sxs-lookup"><span data-stu-id="8fc7b-272">Conclusion</span></span>

<span data-ttu-id="8fc7b-273">W tym przykładzie pokazano, możesz niektórych metod LINQ, jak utworzyć własne metody, które będą używane łatwo za pomocą LINQ włączone kodu.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-273">This sample showed you some of the methods used in LINQ, how to create your own methods that will be easily used with LINQ enabled code.</span></span> <span data-ttu-id="8fc7b-274">On również wyświetlał różnice między opóźnieniem i wczesny ocena oraz wpływ, jaki decyzji może mieć na wydajność.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-274">It also showed you the differences between lazy and eager evaluation, and the effect that decision can have on performance.</span></span>

<span data-ttu-id="8fc7b-275">Poznanie nieco technika magician jeden.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-275">You learned a bit about one magician's technique.</span></span> <span data-ttu-id="8fc7b-276">Magicians Użyj losowa faro, ponieważ można kontrolować, którym przechodzi wszystkie karty w talii.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-276">Magicians use the faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="8fc7b-277">W niektórych lewy magician ma umieść karty u góry talii członka grupy odbiorców i przesuwa kilka razy, wiedząc, gdzie przejdzie do tej karty.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-277">In some tricks, the magician has an audience member place a card on top of the deck, and shuffles a few times, knowing where that card goes.</span></span> <span data-ttu-id="8fc7b-278">Inne Iluzje wymagają talii ustawić określony sposób.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-278">Other illusions require the deck set a certain way.</span></span> <span data-ttu-id="8fc7b-279">Magician ustawi talii przed wykonaniem lewy.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-279">A magician will set the deck prior to performing the trick.</span></span> <span data-ttu-id="8fc7b-280">Następnie użytkownik będzie losowo talii 5 razy przy użyciu losowego wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-280">Then she will shuffle the deck 5 times using an inner shuffle.</span></span> <span data-ttu-id="8fc7b-281">Na etapie klika Pokaż wygląd losowe talii, losowo go 3 razy więcej i talii ustawić dokładnie tak jak chce mieć.</span><span class="sxs-lookup"><span data-stu-id="8fc7b-281">On stage, she can show what looks like a random deck, shuffle it 3 more times, and have the deck set exactly how she wants.</span></span>
