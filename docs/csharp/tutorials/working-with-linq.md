---
title: Praca z technologią LINQ
description: Ten samouczek omawia sposób generowania sekwencji za pomocą LINQ, pisanie metody używane w kwerendach LINQ i rozróżnienie między eager i leniwa ocena.
ms.date: 03/28/2017
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: dc5f6cc4fd38b32f54a576a3947187cbed4e70e8
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086755"
---
# <a name="working-with-linq"></a><span data-ttu-id="dc1cf-103">Praca z technologią LINQ</span><span class="sxs-lookup"><span data-stu-id="dc1cf-103">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="dc1cf-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="dc1cf-104">Introduction</span></span>

<span data-ttu-id="dc1cf-105">W tym samouczku pokazano pewną liczbę funkcji platformy .NET Core i języka C#.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="dc1cf-106">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-106">You’ll learn:</span></span>

*   <span data-ttu-id="dc1cf-107">Sposób generowania sekwencji za pomocą LINQ</span><span class="sxs-lookup"><span data-stu-id="dc1cf-107">How to generate sequences with LINQ</span></span>
*   <span data-ttu-id="dc1cf-108">Jak napisać metody, które mogą być łatwo używane w kwerendach LINQ.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-108">How to write methods that can be easily used in LINQ queries.</span></span>
*   <span data-ttu-id="dc1cf-109">Jak rozróżnianie między eager i leniwa ocena.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-109">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="dc1cf-110">Te techniki dowiesz się, tworząc aplikację, która przedstawia jedną z podstawowych umiejętności wszelkie magician: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="dc1cf-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="dc1cf-111">Krótko mówiąc faro shuffle jest techniką, gdzie możesz podzielić talii kart dokładnie w połowie, a następnie shuffle przeplatają każdego jedną kartę, z każda część odbudować oryginalnego slajdów.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="dc1cf-112">Magicians Użyj tej techniki, ponieważ wszystkie karty w znanej lokalizacji po każdym losowa, a kolejność jest wzorzec powtarzające się.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span> 

<span data-ttu-id="dc1cf-113">Dla naszych potrzeb jest światła hearted przyjrzeć manipulowanie sekwencji danych.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-113">For our purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="dc1cf-114">Aplikację, którą utworzysz konstruowania talii kart, a następnie wykonać sekwencję przesuwa, zapisywanie sekwencji zawsze wtedy.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-114">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="dc1cf-115">Zostanie również porównać zaktualizowane kolejność oryginalnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="dc1cf-116">W tym samouczku składa się z wielu kroków.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="dc1cf-117">Po każdym kroku możesz uruchomić aplikację i wyświetlić postęp.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="dc1cf-118">Można również wyświetlić [ukończone przykładowe](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) w repozytorium dotnet/samples w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="dc1cf-119">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="dc1cf-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc1cf-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="dc1cf-120">Prerequisites</span></span>

<span data-ttu-id="dc1cf-121">Należy skonfigurować maszynę w taki sposób, aby uruchomić platformy .NET core.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-121">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="dc1cf-122">Instrukcje dotyczące instalacji można znaleźć na [platformy .NET Core](https://www.microsoft.com/net/core) strony.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="dc1cf-123">Mogą uruchamiać tę aplikację w systemie Windows, Ubuntu Linux, OS X lub w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-123">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="dc1cf-124">Musisz zainstalować wybrany edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="dc1cf-125">Opisy poniżej użycia [programu Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="dc1cf-126">Można jednak użyć dowolnego narzędzia potrafisz.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="dc1cf-127">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="dc1cf-127">Create the Application</span></span>

<span data-ttu-id="dc1cf-128">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-128">The first step is to create a new application.</span></span> <span data-ttu-id="dc1cf-129">Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="dc1cf-130">Upewnij się, że sposób bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-130">Make that the current directory.</span></span> <span data-ttu-id="dc1cf-131">Wpisz polecenie `dotnet new console` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="dc1cf-132">Spowoduje to utworzenie plikach startowych dla podstawowych aplikacji "Hello World".</span><span class="sxs-lookup"><span data-stu-id="dc1cf-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="dc1cf-133">Jeśli nie znasz języka C#, [w tym samouczku](console-teleprompter.md) wyjaśnienie struktury programu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="dc1cf-134">Może odczytywać, który i następnie wróć tutaj, aby dowiedzieć się więcej na temat LINQ.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-134">You can read that and then return here to learn more about LINQ.</span></span> 

## <a name="creating-the-data-set"></a><span data-ttu-id="dc1cf-135">Tworzenie zestawu danych</span><span class="sxs-lookup"><span data-stu-id="dc1cf-135">Creating the Data Set</span></span>

<span data-ttu-id="dc1cf-136">Zacznijmy od utworzenia talii kart.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-136">Let's start by creating a deck of cards.</span></span> <span data-ttu-id="dc1cf-137">Należy to zrobić tego przy użyciu zapytania LINQ, która ma dwa źródła (jedną dla czterech odpowiada, jeden dla trzynaście wartości).</span><span class="sxs-lookup"><span data-stu-id="dc1cf-137">You'll do this using a LINQ query that has two sources (one for the four suits, one for the thirteen values).</span></span> <span data-ttu-id="dc1cf-138">Tych źródeł będzie łączyć w talii kart 52.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-138">You'll combine those sources into a 52 card deck.</span></span> <span data-ttu-id="dc1cf-139">A `Console.WriteLine` instrukcji wewnątrz `foreach` pętli Wyświetla karty.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-139">A `Console.WriteLine` statement inside a `foreach` loop displays the cards.</span></span>

<span data-ttu-id="dc1cf-140">Oto zapytanie:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-140">Here's the query:</span></span>

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

<span data-ttu-id="dc1cf-141">Wielokrotność `from` generuje klauzule `SelectMany`, co powoduje utworzenie pojedynczego ciągu z łączenia każdego elementu w pierwszej kolejności, przy czym każdy element w drugiej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-141">The multiple `from` clauses produce a `SelectMany`, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="dc1cf-142">Kolejność jest ważna dla naszych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-142">The order is important for our purposes.</span></span> <span data-ttu-id="dc1cf-143">Pierwszy element w pierwszej sekwencji źródłowej (kolory) w połączeniu z każdego elementu w drugiej sekwencji (wartości).</span><span class="sxs-lookup"><span data-stu-id="dc1cf-143">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Values).</span></span> <span data-ttu-id="dc1cf-144">To zapewnia wszystkie karty trzynaście pierwszy koloru.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-144">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="dc1cf-145">Ten proces jest powtarzany, przy czym każdy element w pierwszej kolejności (kolory).</span><span class="sxs-lookup"><span data-stu-id="dc1cf-145">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="dc1cf-146">Wynik końcowy jest talii kart uporządkowane według kolory, a następnie według wartości.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-146">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="dc1cf-147">Następnie należy tworzyć metody Suits() i Ranks().</span><span class="sxs-lookup"><span data-stu-id="dc1cf-147">Next, you'll need to build the Suits() and Ranks() methods.</span></span> <span data-ttu-id="dc1cf-148">Zacznijmy od bardzo prosty zestaw *metody iteracyjne* , którzy generują sekwencja jako wyliczalny element z ciągami:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-148">Let's start with a really simple set of *iterator methods* that generate the sequence as an enumerable of strings:</span></span>

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

<span data-ttu-id="dc1cf-149">Korzystanie z tych dwóch metod zarówno `yield return` składni, aby utworzyć sekwencję podczas ich działania.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-149">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="dc1cf-150">Kompilator tworzy obiekt, który implementuje `IEnumerable<T>` i generuje sekwencję ciągów, ponieważ są one wymagane.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-150">The compiler builds an object that implements `IEnumerable<T>` and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="dc1cf-151">W tym można skompilować należy dodać następujące dwa wiersze na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-151">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="dc1cf-152">Przejdź dalej i uruchom aplikację przykładową na tym etapie konstruowania.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-152">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="dc1cf-153">Wszystkie karty 52 będzie wyświetlany w talii kart.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-153">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="dc1cf-154">Może okazać się bardzo pomocne uruchomić ten przykład w debugerze, aby obserwować sposób, w jaki `Suits()` i `Values()` wykonywania metody.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-154">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Values()` methods execute.</span></span> <span data-ttu-id="dc1cf-155">Wyraźnie widać, że każdego ciągu w każdej sekwencji jest generowany tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-155">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Okno konsoli aplikacji wypisywanie 52 kart](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="dc1cf-157">Manipulowanie kolejności</span><span class="sxs-lookup"><span data-stu-id="dc1cf-157">Manipulating the Order</span></span>

<span data-ttu-id="dc1cf-158">Następnie utworzymy metody narzędzie, które może wykonywać losowa.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-158">Next, let's build a utility method that can perform the shuffle.</span></span> <span data-ttu-id="dc1cf-159">Pierwszym krokiem jest podzielenie slajdów w dwóch.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-159">The first step is to split the deck in two.</span></span> <span data-ttu-id="dc1cf-160">`Take()` i `Skip()` metody, które są częścią interfejsów API LINQ zapewnia tę funkcję dla nas:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-160">The `Take()` and `Skip()` methods that are part of the LINQ APIs provide that feature for us:</span></span>

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

<span data-ttu-id="dc1cf-161">Metoda shuffle nie istnieje w standardowej bibliotece, dzięki czemu będzie trzeba napisać własny.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-161">The shuffle method doesn't exist in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="dc1cf-162">Ta nowa metoda przedstawiono kilka technik, które ma być używany do programów opartych na LINQ, więc opisano każdej części metody w krokach.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-162">This new method illustrates several techniques that you'll use with LINQ-based programs, so let's explain each part of the method in steps.</span></span>

<span data-ttu-id="dc1cf-163">Podpis metody tworzy *— metoda rozszerzenia*:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-163">The signature for the method creates an *extension method*:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="dc1cf-164">Metoda rozszerzenia jest specjalnego przeznaczenia *metody statycznej.*</span><span class="sxs-lookup"><span data-stu-id="dc1cf-164">An extension method is a special purpose *static method.*</span></span> <span data-ttu-id="dc1cf-165">Możesz zobaczyć dodanie `this` modyfikator na pierwszy argument do metody.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-165">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="dc1cf-166">Oznacza to, że należy wywołać metodę, tak jakby był metodą elementu członkowskiego typu pierwszego argumentu.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-166">That means you call the method as though it were a member method of the type of the first argument.</span></span>

<span data-ttu-id="dc1cf-167">Metody rozszerzenia mogą być deklarowane tylko w `static` klasy, więc Utwórz nową klasę statycznego o nazwie `extensions` dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-167">Extension methods can be declared only inside `static` classes, so let's create a new static class called `extensions` for this functionality.</span></span> <span data-ttu-id="dc1cf-168">Kontynuuj w tym samouczku, a te zostaną umieszczone w tej samej klasy należy dodać więcej metod rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-168">You'll add more extension methods as you continue this tutorial, and those will be placed in the same class.</span></span>

<span data-ttu-id="dc1cf-169">Tej deklaracji metody również następujące standardowe idiom gdzie typy wejściowe i wyjściowe są `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-169">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="dc1cf-170">Czy rozwiązanie umożliwia metody LINQ zezwalającym ze sobą, aby wykonywać bardziej złożone zapytania.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-170">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

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

<span data-ttu-id="dc1cf-171">Będziesz wyliczanie zarówno sekwencje jednocześnie, z przeplotem elementy i utworzenie jednego obiektu.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-171">You will be enumerating both sequences at once, interleaving the elements, and creating one object.</span></span>  <span data-ttu-id="dc1cf-172">Zapisywanie LINQ metodę, która współdziała z dwóch sekwencji wymaga zrozumienia sposobu `IEnumerable` działa.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-172">Writing a LINQ method that works with two sequences requires that you understand how `IEnumerable` works.</span></span>

<span data-ttu-id="dc1cf-173">`IEnumerable` Interfejs ma jedną z metod: `GetEnumerator()`.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-173">The `IEnumerable` interface has one method: `GetEnumerator()`.</span></span> <span data-ttu-id="dc1cf-174">Obiekt zwrócony przez `GetEnumerator()` ma metodę, aby przejść do następnego elementu i właściwości, która pobiera bieżącego elementu w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-174">The object returned by `GetEnumerator()` has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="dc1cf-175">Te dwa elementy członkowskie użyje do wyliczania kolekcji i zwracają elementy.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-175">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="dc1cf-176">Ta metoda przeplotu będzie metody iteratora, więc zamiast tworzenia kolekcji i zwraca kolekcję, użyjesz `yield return` składni pokazanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-176">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span> 

<span data-ttu-id="dc1cf-177">Oto implementacja tej metody:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-177">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="dc1cf-178">Teraz, gdy ta metoda jest napisanych, wróć do `Main` metody i shuffle slajdów, gdy:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-178">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

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

## <a name="comparisons"></a><span data-ttu-id="dc1cf-179">Porównania</span><span class="sxs-lookup"><span data-stu-id="dc1cf-179">Comparisons</span></span>

<span data-ttu-id="dc1cf-180">Zobaczmy, ile przesuwa zajmuje można ustawić na pokład z powrotem do jego oryginalnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-180">Let's see how many shuffles it takes to set the deck back to its original order.</span></span> <span data-ttu-id="dc1cf-181">Będzie konieczne napisanie metody, która określa, czy dwie sekwencje mają taki sam.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-181">You'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="dc1cf-182">Po utworzeniu tej metody, należy umieścić kod, który rozmieszcza slajdów w pętli i sprawdź, gdy jest użyta w kolejności.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-182">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="dc1cf-183">Zapisywanie metodę, aby określić, czy dwie sekwencje są równe powinno być proste.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-183">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="dc1cf-184">Jest podobną strukturę z metodą, którą zapisano mieszania slajdów.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-184">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="dc1cf-185">Tylko tym razem zamiast wydajności zwracanie każdego elementu, można będzie porównywać zgodnych elementów w każdej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-185">Only this time, instead of yield returning each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="dc1cf-186">Sekwencje całą sekwencję zostać wyliczone, jeśli pasuje do każdego elementu, są takie same:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-186">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="dc1cf-187">Spowoduje to pokazanie drugi idiom Linq: metody terminala.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-187">This shows a second Linq idiom: terminal methods.</span></span> <span data-ttu-id="dc1cf-188">Wykonaj sekwencję jako dane wejściowe (lub w tym przypadku dwie sekwencje) i zwraca pojedynczą wartość skalarną.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-188">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="dc1cf-189">Te metody, gdy są one używane, są zawsze ostatnią metodę zapytania.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-189">These methods, when they are used, are always the final method of a query.</span></span> <span data-ttu-id="dc1cf-190">(Stąd nazwa).</span><span class="sxs-lookup"><span data-stu-id="dc1cf-190">(Hence the name).</span></span> 

<span data-ttu-id="dc1cf-191">Można to zobaczyć w działaniu używanej do określania, kiedy talii jest w jego oryginalnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-191">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="dc1cf-192">Umieść kod shuffle wewnątrz pętli, a następnie Zatrzymaj, gdy sekwencja jest ponownie w jego oryginalnej kolejności, stosując `SequenceEquals()` metody.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-192">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="dc1cf-193">Widać, że zawsze będzie ostatnią metodę w każdym zapytaniu, ponieważ zwraca pojedynczą wartość zamiast sekwencji:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-193">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

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

<span data-ttu-id="dc1cf-194">Uruchamianie aplikacji przykładowej i zobacz, jak talii Reorganizuje na każdym shuffle aż powraca do oryginalnej konfiguracji po 8 iteracjach.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-194">Run the sample, and see how the deck rearranges on each shuffle, until it returns to its original configuration after 8 iterations.</span></span>

## <a name="optimizations"></a><span data-ttu-id="dc1cf-195">Optymalizacje</span><span class="sxs-lookup"><span data-stu-id="dc1cf-195">Optimizations</span></span>

<span data-ttu-id="dc1cf-196">Wykonuje przykładowe dołączeniu do tej pory *się shuffle*, gdzie kart górny i dolny pozostają takie same, przy każdym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-196">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="dc1cf-197">Upewnijmy się zmienić, i uruchom *w losowo*, gdzie wszystkie karty 52 zmiana położenia.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-197">Let's make one change, and run an *in shuffle*, where all 52 cards change position.</span></span> <span data-ttu-id="dc1cf-198">Dla w losowo możesz przeplot slajdów, aby pierwszy karty w dolnej połowie staje się pierwszej karty w talii kart.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-198">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="dc1cf-199">Oznacza to, że ostatnią kartę w górnej połowie staje się karta dolnej.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-199">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="dc1cf-200">Który różni się tylko jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-200">That's just a one line change.</span></span> <span data-ttu-id="dc1cf-201">Zaktualizuj mieszania, aby zmienić kolejność górnej i dolnej części talii wywołanie:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-201">Update the call to shuffle to change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="dc1cf-202">Ponownie uruchom program, a zobaczysz, że zajmuje 52 iteracji dla slajdów zmienić kolejność sam.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-202">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="dc1cf-203">Będzie również uruchomić, należy zwrócić uwagę spadku wydajności niektórych obniżyć wydajność, ponieważ program kontynuuje działanie.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-203">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="dc1cf-204">Istnieje kilka przyczyn.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-204">There are a number of reasons for this.</span></span> <span data-ttu-id="dc1cf-205">Udzielmy jedną z głównych przyczyn: nieefektywne użycie *obliczanie leniwe*.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-205">Let's tackle one of the major causes: inefficient use of *lazy evaluation*.</span></span>

<span data-ttu-id="dc1cf-206">Zapytania LINQ są oceniane opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-206">LINQ queries are evaluated lazily.</span></span> <span data-ttu-id="dc1cf-207">Sekwencji są generowane tylko wtedy, gdy elementy są wymagane.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-207">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="dc1cf-208">Zazwyczaj, który jest główną zaletą LINQ.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-208">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="dc1cf-209">Jednak użycie takich jak ten program, powoduje to wykładniczy wzrost w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-209">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="dc1cf-210">Oryginalny slajdów został wygenerowany przy użyciu zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-210">The original deck was generated using a LINQ query.</span></span> <span data-ttu-id="dc1cf-211">Każdy losowa jest generowany, wykonując trzy zapytań LINQ w poprzednim slajdów.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-211">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="dc1cf-212">Wszystkie te są wykonywane opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-212">All these are performed lazily.</span></span> <span data-ttu-id="dc1cf-213">Oznacza to również, że te procedury są wykonywane ponownie każdorazowo, gdy wymagane są sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-213">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="dc1cf-214">Przez razem, gdy można uzyskać dostęp do 52nd iteracji możesz teraz trwa ponowne generowanie oryginalnego slajdów many, wiele razy.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-214">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="dc1cf-215">Napiszmy dziennika, aby zademonstrować to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-215">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="dc1cf-216">Następnie możesz go ma naprawić.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-216">Then, you'll fix it.</span></span>

<span data-ttu-id="dc1cf-217">Oto metoda dziennika, który można dołączyć do dowolnego zapytania, aby oznaczyć, że zapytanie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-217">Here's a log method that can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="dc1cf-218">Następnie przygotuj Instrumentację definicję każdego zapytania za pomocą komunikatu dziennika:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-218">Next, instrument the definition of each query with a log message:</span></span>

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

<span data-ttu-id="dc1cf-219">Należy zauważyć, że nie logujesz się za każdym razem, gdy możesz uzyskać dostęp do kwerendy.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-219">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="dc1cf-220">Zaloguj się tylko wtedy, gdy tworzysz oryginalnego zapytania.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-220">You log only when you create the original query.</span></span> <span data-ttu-id="dc1cf-221">Program nadal zajmuje dużo czasu do uruchomienia, ale spowoduje to wyświetlenie dlaczego.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-221">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="dc1cf-222">Po uruchomieniu o cierpliwość systemem wewnętrzny mieszania za pomocą funkcji rejestrowania włączona, przejdź z powrotem do zewnętrznego losowa.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-222">If you run out of patience running the inner shuffle with logging turned on, switch back to the outer shuffle.</span></span> <span data-ttu-id="dc1cf-223">Nadal zobaczysz efekty obliczanie z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-223">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="dc1cf-224">W jednym przebiegu wykonuje kwerendy 2592, w tym wszystkich wartości i sposób generowania.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-224">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="dc1cf-225">Istnieje łatwy sposób zaktualizować ten program, aby uniknąć tych operacji wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-225">There is an easy way to update this program to avoid all those executions.</span></span> <span data-ttu-id="dc1cf-226">Istnieją metody LINQ `ToArray()` i `ToList()` spowodować, że zapytanie, aby uruchomić i zapisać wyniki w tablicy lub listy, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-226">There are LINQ methods `ToArray()` and `ToList()` that cause the query to run, and store the results in an array or a list, respectively.</span></span> <span data-ttu-id="dc1cf-227">Metody te służy do danych wyników zapytania w pamięci podręcznej, zamiast ponownie wykonaj zapytanie źródła.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-227">You use these methods to cache the data results of a query rather than execute the source query again.</span></span>  <span data-ttu-id="dc1cf-228">Dołącz zapytania, które generują talii kart z wywołaniem `ToArray()` i ponownie uruchom zapytanie:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-228">Append the queries that generate the card decks with a call to `ToArray()` and run the query again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="dc1cf-229">Uruchom ponownie i zewnętrzne losowa jest poniżej 30 zapytania.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-229">Run again, and the outer shuffle is down to 30 queries.</span></span> <span data-ttu-id="dc1cf-230">Ponownie uruchom za pomocą wewnętrznego losowa i zostaną wyświetlone podobne ulepszenia.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-230">Run again with the inner shuffle and you'll see similar improvements.</span></span> <span data-ttu-id="dc1cf-231">(Obecnie wykonuje zapytania 162).</span><span class="sxs-lookup"><span data-stu-id="dc1cf-231">(It now executes 162 queries).</span></span>

<span data-ttu-id="dc1cf-232">Nie błędnie interpretuje planowanie, który eagerly uruchamiać wszystkie zapytania w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-232">Don't misinterpret this example by thinking that all queries should run eagerly.</span></span> <span data-ttu-id="dc1cf-233">W tym przykładzie jest przeznaczony do wyróżnienia przypadki użycia, w którym leniwa ocena może spowodować problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-233">This example is designed to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="dc1cf-234">Wynika to z każdej z umów nowy zbiór kart składa się z poprzednich rozmieszczenia.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-234">That's because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="dc1cf-235">Przy użyciu leniwa ocena oznacza, że każda nowa konfiguracja slajdów składa się z oryginalnego slajdów, nawet wykonywania kodu, który skompilowany `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-235">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="dc1cf-236">Dzięki któremu dużą ilość dodatkowej pracy.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-236">That causes a large amount of extra work.</span></span> 

<span data-ttu-id="dc1cf-237">W praktyce niektóre algorytmy Uruchom znacznie lepsze, za pomocą eager oceny, a pozostałe — znacznie lepsze, za pomocą obliczanie z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-237">In practice, some algorithms run much better using eager evaluation, and others run much better using lazy evaluation.</span></span> <span data-ttu-id="dc1cf-238">(Ogólnie rzecz biorąc, obliczanie z opóźnieniem jest dużo lepszym rozwiązaniem, gdy źródło danych jest oddzielnym procesie, takich jak aparat bazy danych.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-238">(In general, lazy evaluation is a much better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="dc1cf-239">W takich przypadkach opóźnieniem umożliwia bardziej złożone zapytania, które można wykonać tylko jeden komunikację dwustronną proces bazy danych.) LINQ umożliwia zarówno z opóźnieniem i chętnie Zapoznamy oceny.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-239">In those cases, lazy evaluation enables more complex queries to execute only one round trip to the database process.) LINQ enables both lazy and eager evaluation.</span></span> <span data-ttu-id="dc1cf-240">Zmierz i wybrać najlepszy wybór.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-240">Measure, and pick the best choice.</span></span>

## <a name="preparing-for-new-features"></a><span data-ttu-id="dc1cf-241">Przygotowanie do nowych funkcji</span><span class="sxs-lookup"><span data-stu-id="dc1cf-241">Preparing for New Features</span></span>

<span data-ttu-id="dc1cf-242">Kod napisany w tym przykładzie to przykład tworzenia prostego prototypu, który wykonuje zadania.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-242">The code you've written for this sample is an example of creating a simple prototype that does the job.</span></span> <span data-ttu-id="dc1cf-243">Jest to doskonały sposób eksplorowania obszar problemu, a dla wielu funkcji, może być najlepszym rozwiązaniem stałe.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-243">This is a great way to explore a problem space, and for many features, it may be the best permanent solution.</span></span> <span data-ttu-id="dc1cf-244">Już wykorzystywane *typy anonimowe* dla karty, a każda karta jest reprezentowany przez parametry.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-244">You've leveraged *anonymous types* for the cards, and each card is represented by strings.</span></span>

<span data-ttu-id="dc1cf-245">*Typy anonimowe* mają wiele zalet produktywności.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-245">*Anonymous Types* have many productivity advantages.</span></span> <span data-ttu-id="dc1cf-246">Nie trzeba zdefiniować klasę sobie, aby reprezentować pamięć masową.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-246">You don't need to define a class yourself to represent the storage.</span></span> <span data-ttu-id="dc1cf-247">Kompilator generuje typ dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-247">The compiler generates the type for you.</span></span> <span data-ttu-id="dc1cf-248">Typ wygenerowanego przez kompilator korzysta z wielu najlepszych rozwiązań dla obiektów danych proste.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-248">The compiler generated type utilizes many of the best practices for simple data objects.</span></span> <span data-ttu-id="dc1cf-249">Ma ona *niezmienne*, co oznacza, że żaden z jej właściwości można zmienić po został skonstruowany.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-249">It's *immutable*, meaning that none of its properties can be changed after it has been constructed.</span></span> <span data-ttu-id="dc1cf-250">Typy anonimowe są wewnętrzne dla zestawu, więc nie są widoczne jako część publicznego interfejsu API dla tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-250">Anonymous types are internal to an assembly, so they aren't seen as part of the public API for that assembly.</span></span> <span data-ttu-id="dc1cf-251">Typy anonimowe zawierają również przesłonięcia z `ToString()` metodę, która zwraca sformatowany ciąg z każdej wartości.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-251">Anonymous types also contain an override of the `ToString()` method that returns a formatted string with each of the values.</span></span>

<span data-ttu-id="dc1cf-252">Typy anonimowe ma również wady.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-252">Anonymous types also have disadvantages.</span></span> <span data-ttu-id="dc1cf-253">Nie mają nazw dostępnych, więc nie można go użyć jako wartości zwracane lub argumentów</span><span class="sxs-lookup"><span data-stu-id="dc1cf-253">They don't have accessible names, so you can't use them as return values or arguments.</span></span> <span data-ttu-id="dc1cf-254">Można zauważyć, że używanym żadnych metod powyżej w te typy anonimowe są metody rodzajowe.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-254">You'll notice that any methods above that used these anonymous types are generic methods.</span></span> <span data-ttu-id="dc1cf-255">Zastępowania metody `ToString()` może nie być ma więcej funkcji wzrostem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-255">The override of `ToString()` may not be what you want as the application grows more features.</span></span> 

<span data-ttu-id="dc1cf-256">W przykładzie użyto również ciągi, kolor i rangi każdej karty.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-256">The sample also uses strings for the suit and the rank of each card.</span></span> <span data-ttu-id="dc1cf-257">Który jest dość Otwórz zakończone.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-257">That's quite open ended.</span></span> <span data-ttu-id="dc1cf-258">System typów języka C# mogą pomóc nam w ulepszaniu lepszego kodu, wykorzystując `enum` typów w przypadku tych wartości.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-258">The C# type system can help us make better code, by leveraging `enum` types for those values.</span></span>

<span data-ttu-id="dc1cf-259">Zacznij od kolory.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-259">Start with the suits.</span></span> <span data-ttu-id="dc1cf-260">Jest to idealny moment, aby użyć `enum`:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-260">This is a perfect time to use an `enum`:</span></span>

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

<span data-ttu-id="dc1cf-261">`Suits()` Metoda zmienia się również typ i implementację:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-261">The `Suits()` method also changes type and implementation:</span></span>

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

<span data-ttu-id="dc1cf-262">Następnie wykonaj tę samą zmianę o randze kart:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-262">Next, do the same change with the Rank of the cards:</span></span>

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

<span data-ttu-id="dc1cf-263">I metoda, która generuje je:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-263">And the method that generates them:</span></span>

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

<span data-ttu-id="dc1cf-264">Jako jeden końcowy oczyszczania stwórzmy typu reprezentującego karty, zamiast polegania na typ anonimowy.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-264">As one final cleanup, let's make a type to represent the card, instead of relying on an anonymous type.</span></span> <span data-ttu-id="dc1cf-265">Typy anonimowe to idealne rozwiązanie dla typów lokalna, lekki, ale w tym przykładzie karty gry jest jednym z głównych pojęć.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-265">Anonymous types are great for lightweight, local types, but in this example, the playing card is one of the main concepts.</span></span> <span data-ttu-id="dc1cf-266">Powinna ona konkretnego typu.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-266">It should be a concrete type.</span></span>

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

<span data-ttu-id="dc1cf-267">Ten typ korzysta *automatycznie implementowane właściwości tylko do odczytu* które są ustawiane w konstruktorze, a następnie nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-267">This type uses *auto-implemented read-only properties* which are set in the constructor, and then cannot be modified.</span></span> <span data-ttu-id="dc1cf-268">On również sprawia, że użycie [Interpolacja ciągów](../language-reference/tokens/interpolated.md) funkcja, która ułatwia formatowanie ciągów w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-268">It also makes use of the [string interpolation](../language-reference/tokens/interpolated.md) feature that makes it easier to format string output.</span></span>

<span data-ttu-id="dc1cf-269">Zaktualizuj zapytanie, które generuje początkowy slajdów, aby użyć nowego typu:</span><span class="sxs-lookup"><span data-stu-id="dc1cf-269">Update the query that generates the starting deck to use the new type:</span></span>

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

<span data-ttu-id="dc1cf-270">Skompiluj i uruchom ponownie.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-270">Compile and run again.</span></span> <span data-ttu-id="dc1cf-271">Dane wyjściowe są nieco bardziej przejrzyste i kod jest nieco bardziej oczywiste i można rozszerzyć, aby łatwiej.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-271">The output is a little cleaner, and the code is a bit more clear and can be extended more easily.</span></span>

## <a name="conclusion"></a><span data-ttu-id="dc1cf-272">Wniosek</span><span class="sxs-lookup"><span data-stu-id="dc1cf-272">Conclusion</span></span>

<span data-ttu-id="dc1cf-273">Ten przykład pokazuje niektórych metod LINQ, jak utworzyć swoje własne metody, które będą używane łatwo za pomocą LINQ włączone kodu.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-273">This sample showed you some of the methods used in LINQ, how to create your own methods that will be easily used with LINQ enabled code.</span></span> <span data-ttu-id="dc1cf-274">On również pokazuje różnice między obliczanie z opóźnieniem i chętnie Zapoznamy oraz wpływ, jaki decyzja może mieć na wydajność.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-274">It also showed you the differences between lazy and eager evaluation, and the effect that decision can have on performance.</span></span>

<span data-ttu-id="dc1cf-275">Omówiono nieco jeden magician techniki.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-275">You learned a bit about one magician's technique.</span></span> <span data-ttu-id="dc1cf-276">Magicians Użyj faro shuffle, ponieważ może kontrolować, gdzie wszystkie karty przemieszcza się w talii kart.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-276">Magicians use the faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="dc1cf-277">W niektórych wskazówki magician ma zachować karty na pokład członka grupy odbiorców i rozmieszcza kilka razy, wiedząc, gdzie przejdzie tej karty.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-277">In some tricks, the magician has an audience member place a card on top of the deck, and shuffles a few times, knowing where that card goes.</span></span> <span data-ttu-id="dc1cf-278">Inne Iluzje wymagają talii ustawić w określony sposób.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-278">Other illusions require the deck set a certain way.</span></span> <span data-ttu-id="dc1cf-279">Magician ustawi slajdów, przed wykonaniem lewy.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-279">A magician will set the deck prior to performing the trick.</span></span> <span data-ttu-id="dc1cf-280">Następnie zostanie ona mieszania slajdów 5 razy przy użyciu zewnętrznego losowa.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-280">Then she will shuffle the deck 5 times using an outer shuffle.</span></span> <span data-ttu-id="dc1cf-281">Na etapie ona pokazują, jak wygląda losowe slajdów, mieszania go 3 razy więcej i slajdów, ustaw dokładnie tak jak chce mieć.</span><span class="sxs-lookup"><span data-stu-id="dc1cf-281">On stage, she can show what looks like a random deck, shuffle it 3 more times, and have the deck set exactly how she wants.</span></span>
