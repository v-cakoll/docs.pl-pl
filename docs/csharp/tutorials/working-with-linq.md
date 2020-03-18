---
title: Praca z technologią LINQ
description: Ten samouczek uczy, jak generować sekwencje za pomocą LINQ, pisać metody do użycia w zapytaniach LINQ i odróżnić oceny chętnie i leniwy.
ms.date: 10/29/2018
ms.technology: csharp-linq
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: ece001e82c0aa44a91999bea78d2fd695ff9362b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240018"
---
# <a name="work-with-language-integrated-query-linq"></a><span data-ttu-id="8bd99-103">Praca z zazapytaniem zintegrowanym z językiem (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8bd99-103">Work with Language-Integrated Query (LINQ)</span></span>

## <a name="introduction"></a><span data-ttu-id="8bd99-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bd99-104">Introduction</span></span>

<span data-ttu-id="8bd99-105">W tym samouczku nauczy Cię funkcje w .NET Core i języku C#.</span><span class="sxs-lookup"><span data-stu-id="8bd99-105">This tutorial teaches you features in .NET Core and the C# language.</span></span> <span data-ttu-id="8bd99-106">Omawiane tematy:</span><span class="sxs-lookup"><span data-stu-id="8bd99-106">You’ll learn how to:</span></span>

- <span data-ttu-id="8bd99-107">Generowanie sekwencji za pomocą LINQ.</span><span class="sxs-lookup"><span data-stu-id="8bd99-107">Generate sequences with LINQ.</span></span>
- <span data-ttu-id="8bd99-108">Pisanie metod, które mogą być łatwo używane w zapytaniach LINQ.</span><span class="sxs-lookup"><span data-stu-id="8bd99-108">Write methods that can be easily used in LINQ queries.</span></span>
- <span data-ttu-id="8bd99-109">Rozróżnianie oceny chętnej i leniwej.</span><span class="sxs-lookup"><span data-stu-id="8bd99-109">Distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="8bd99-110">Nauczysz się tych technik, budując aplikację, która pokazuje jedną z podstawowych umiejętności każdego maga: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="8bd99-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="8bd99-111">Krótko mówiąc, faro shuffle to technika, w której dzielisz talię kart dokładnie na pół, a następnie tasowanie przeplata każdą kartę z każdej połowy, aby odbudować oryginalną talię.</span><span class="sxs-lookup"><span data-stu-id="8bd99-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="8bd99-112">Magowie używają tej techniki, ponieważ każda karta znajduje się w znanej lokalizacji po każdym shuffle, a kolejność jest powtarzającym się wzorem.</span><span class="sxs-lookup"><span data-stu-id="8bd99-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span>

<span data-ttu-id="8bd99-113">Dla Twoich celów jest to lekkie spojrzenie na manipulowanie sekwencjami danych.</span><span class="sxs-lookup"><span data-stu-id="8bd99-113">For your purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="8bd99-114">Aplikacja, którą zbudujesz, tworzy talię kart, a następnie wykonuje sekwencję tasowania, zapisując sekwencję za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="8bd99-114">The application you'll build constructs a card deck and then performs a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="8bd99-115">Zostanie również porównane zaktualizowane zamówienie z oryginalnym zamówieniem.</span><span class="sxs-lookup"><span data-stu-id="8bd99-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="8bd99-116">Ten samouczek ma wiele kroków.</span><span class="sxs-lookup"><span data-stu-id="8bd99-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="8bd99-117">Po każdym kroku można uruchomić aplikację i zobaczyć postęp.</span><span class="sxs-lookup"><span data-stu-id="8bd99-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="8bd99-118">Możesz również zobaczyć [ukończoną próbkę](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) w repozytorium GitHub dotnet/samples.</span><span class="sxs-lookup"><span data-stu-id="8bd99-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="8bd99-119">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="8bd99-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8bd99-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8bd99-120">Prerequisites</span></span>

<span data-ttu-id="8bd99-121">Musisz skonfigurować komputer do uruchamiania rdzenia .NET.</span><span class="sxs-lookup"><span data-stu-id="8bd99-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="8bd99-122">Instrukcje instalacji można znaleźć na stronie [pobierania .NET Core.](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="8bd99-122">You can find the installation instructions on the [.NET Core Download](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="8bd99-123">Możesz uruchomić tę aplikację w systemie Windows, Ubuntu Linux lub OS X lub w kontenerze Platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="8bd99-123">You can run this application on Windows, Ubuntu Linux, or OS X, or in a Docker container.</span></span> <span data-ttu-id="8bd99-124">Musisz zainstalować swój ulubiony edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="8bd99-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="8bd99-125">Poniższe opisy używają [kodu Programu Visual Studio,](https://code.visualstudio.com/) który jest edytorem open source, między platformami.</span><span class="sxs-lookup"><span data-stu-id="8bd99-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross-platform editor.</span></span> <span data-ttu-id="8bd99-126">Możesz jednak użyć dowolnych narzędzi, które Ci się podobają.</span><span class="sxs-lookup"><span data-stu-id="8bd99-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="8bd99-127">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bd99-127">Create the Application</span></span>

<span data-ttu-id="8bd99-128">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bd99-128">The first step is to create a new application.</span></span> <span data-ttu-id="8bd99-129">Otwórz wiersz polecenia i utwórz nowy katalog dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bd99-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="8bd99-130">Upewnij się, że bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="8bd99-130">Make that the current directory.</span></span> <span data-ttu-id="8bd99-131">Wpisz `dotnet new console` polecenie w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="8bd99-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="8bd99-132">Spowoduje to utworzenie plików startowych dla podstawowej aplikacji "Hello World".</span><span class="sxs-lookup"><span data-stu-id="8bd99-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="8bd99-133">Jeśli nigdy wcześniej nie używano języka C#, [w tym samouczku](console-teleprompter.md) wyjaśniono strukturę programu C#.</span><span class="sxs-lookup"><span data-stu-id="8bd99-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="8bd99-134">Możesz przeczytać, że a następnie wrócić tutaj, aby dowiedzieć się więcej o LINQ.</span><span class="sxs-lookup"><span data-stu-id="8bd99-134">You can read that and then return here to learn more about LINQ.</span></span>

## <a name="create-the-data-set"></a><span data-ttu-id="8bd99-135">Tworzenie zestawu danych</span><span class="sxs-lookup"><span data-stu-id="8bd99-135">Create the Data Set</span></span>

<span data-ttu-id="8bd99-136">Przed rozpoczęciem upewnij się, że w górnej `Program.cs` części pliku `dotnet new console`generowanego przez:</span><span class="sxs-lookup"><span data-stu-id="8bd99-136">Before you begin, make sure that the following lines are at the top of the `Program.cs` file generated by `dotnet new console`:</span></span>

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="8bd99-137">Jeśli te trzy`using` wiersze (instrukcje) nie są w górnej części pliku, nasz program nie będzie kompilować.</span><span class="sxs-lookup"><span data-stu-id="8bd99-137">If these three lines (`using` statements) aren't at the top of the file, our program will not compile.</span></span>

<span data-ttu-id="8bd99-138">Teraz, gdy masz wszystkie odniesienia, które będą potrzebne, zastanów się, co stanowi talię kart.</span><span class="sxs-lookup"><span data-stu-id="8bd99-138">Now that you have all of the references that you'll need, consider what constitutes a deck of cards.</span></span> <span data-ttu-id="8bd99-139">Często talia kart do gry ma cztery garnitury, a każdy garnitur ma trzynaście wartości.</span><span class="sxs-lookup"><span data-stu-id="8bd99-139">Commonly, a deck of playing cards has four suits, and each suit has thirteen values.</span></span> <span data-ttu-id="8bd99-140">Zwykle można rozważyć `Card` utworzenie klasy tuż nietoperza i wypełnianie kolekcji `Card` obiektów ręcznie.</span><span class="sxs-lookup"><span data-stu-id="8bd99-140">Normally, you might consider creating a `Card` class right off the bat and populating a collection of `Card` objects by hand.</span></span> <span data-ttu-id="8bd99-141">Z LINQ możesz być bardziej zwięzły niż zwykły sposób radzenia sobie z tworzeniem talii kart.</span><span class="sxs-lookup"><span data-stu-id="8bd99-141">With LINQ, you can be more concise than the usual way of dealing with creating a deck of cards.</span></span> <span data-ttu-id="8bd99-142">Zamiast tworzyć `Card` klasę, można utworzyć dwie sekwencje do reprezentowania odpowiednio garnitury i rangi.</span><span class="sxs-lookup"><span data-stu-id="8bd99-142">Instead of creating a `Card` class, you can create two sequences to represent suits and ranks, respectively.</span></span> <span data-ttu-id="8bd99-143">Utworzysz naprawdę prostą parę [*metod iteratoratu, które wygenerują*](../iterators.md#enumeration-sources-with-iterator-methods) rangi i kolory jako <xref:System.Collections.Generic.IEnumerable%601>ciągi s:</span><span class="sxs-lookup"><span data-stu-id="8bd99-143">You'll create a really simple pair of [*iterator methods*](../iterators.md#enumeration-sources-with-iterator-methods) that will generate the ranks and suits as <xref:System.Collections.Generic.IEnumerable%601>s of strings:</span></span>

```csharp
// Program.cs
// The Main() method

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

<span data-ttu-id="8bd99-144">Umieść je pod `Main` metodą `Program.cs` w pliku.</span><span class="sxs-lookup"><span data-stu-id="8bd99-144">Place these underneath the `Main` method in your `Program.cs` file.</span></span> <span data-ttu-id="8bd99-145">Te dwie metody wykorzystują `yield return` składnię do tworzenia sekwencji podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="8bd99-145">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="8bd99-146">Kompilator tworzy obiekt, <xref:System.Collections.Generic.IEnumerable%601> który implementuje i generuje sekwencję ciągów, ponieważ są one wymagane.</span><span class="sxs-lookup"><span data-stu-id="8bd99-146">The compiler builds an object that implements <xref:System.Collections.Generic.IEnumerable%601> and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="8bd99-147">Teraz użyj tych metod iteratorem, aby stworzyć talię kart.</span><span class="sxs-lookup"><span data-stu-id="8bd99-147">Now, use these iterator methods to create the deck of cards.</span></span> <span data-ttu-id="8bd99-148">W naszej `Main` metodzie umieścisz zapytanie LINQ.</span><span class="sxs-lookup"><span data-stu-id="8bd99-148">You'll place the LINQ query in our `Main` method.</span></span> <span data-ttu-id="8bd99-149">Oto spojrzenie na to:</span><span class="sxs-lookup"><span data-stu-id="8bd99-149">Here's a look at it:</span></span>

```csharp
// Program.cs
static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    // Display each card that we've generated and placed in startingDeck in the console
    foreach (var card in startingDeck)
    {
        Console.WriteLine(card);
    }
}
```

<span data-ttu-id="8bd99-150">Wiele `from` klauzul tworzy <xref:System.Linq.Enumerable.SelectMany%2A>, który tworzy pojedynczą sekwencję z łączenia każdego elementu w pierwszej sekwencji z każdym elementem w drugiej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="8bd99-150">The multiple `from` clauses produce a <xref:System.Linq.Enumerable.SelectMany%2A>, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="8bd99-151">Zamówienie jest ważne dla naszych celów.</span><span class="sxs-lookup"><span data-stu-id="8bd99-151">The order is important for our purposes.</span></span> <span data-ttu-id="8bd99-152">Pierwszy element w pierwszej sekwencji źródłowej (Suits) jest połączony z każdym elementem w drugiej sekwencji (Rangi).</span><span class="sxs-lookup"><span data-stu-id="8bd99-152">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Ranks).</span></span> <span data-ttu-id="8bd99-153">Daje to wszystkie trzynaście kart pierwszego koloru.</span><span class="sxs-lookup"><span data-stu-id="8bd99-153">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="8bd99-154">Proces ten jest powtarzany z każdym elementem w pierwszej sekwencji (Suits).</span><span class="sxs-lookup"><span data-stu-id="8bd99-154">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="8bd99-155">Efektem końcowym jest talia kart zamówionych przez garnitury, a następnie wartości.</span><span class="sxs-lookup"><span data-stu-id="8bd99-155">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="8bd99-156">Należy pamiętać, że niezależnie od tego, czy zdecydujesz się zapisać linq w składni kwerendy używanej powyżej, czy zamiast tego użyć składni metody, zawsze można przejść z jednej formy składni do drugiej.</span><span class="sxs-lookup"><span data-stu-id="8bd99-156">It's important to keep in mind that whether you choose to write your LINQ in the query syntax used above or use method syntax instead, it's always possible to go from one form of syntax to the other.</span></span> <span data-ttu-id="8bd99-157">Powyższe zapytanie zapisane w składni kwerendy można zapisać w składni metody jako:</span><span class="sxs-lookup"><span data-stu-id="8bd99-157">The above query written in query syntax can be written in method syntax as:</span></span>

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

<span data-ttu-id="8bd99-158">Kompilator tłumaczy instrukcje LINQ napisane składnią kwerendy na składnię wywołania równoważnej metody.</span><span class="sxs-lookup"><span data-stu-id="8bd99-158">The compiler translates LINQ statements written with query syntax into the equivalent method call syntax.</span></span> <span data-ttu-id="8bd99-159">W związku z tym niezależnie od wyboru składni dwie wersje kwerendy dają ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="8bd99-159">Therefore, regardless of your syntax choice, the two versions of the query produce the same result.</span></span> <span data-ttu-id="8bd99-160">Wybierz, która składnia działa najlepiej dla Twojej sytuacji: na przykład, jeśli pracujesz w zespole, w którym niektóre elementy członkowskie mają trudności ze składnią metody, spróbuj preferować używanie składni zapytania.</span><span class="sxs-lookup"><span data-stu-id="8bd99-160">Choose which syntax works best for your situation: for instance, if you're working in a team where some of the members have difficulty with method syntax, try to prefer using query syntax.</span></span>

<span data-ttu-id="8bd99-161">Śmiało i uruchomić przykład utworzony w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="8bd99-161">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="8bd99-162">Wyświetli wszystkie 52 karty w talii.</span><span class="sxs-lookup"><span data-stu-id="8bd99-162">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="8bd99-163">Może się okazać, że bardzo pomocne jest uruchomienie tego `Suits()` przykładu w obszarze debugera, aby obserwować, jak i `Ranks()` metody wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8bd99-163">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Ranks()` methods execute.</span></span> <span data-ttu-id="8bd99-164">Wyraźnie widać, że każdy ciąg w każdej sekwencji jest generowany tylko wtedy, gdy jest potrzebny.</span><span class="sxs-lookup"><span data-stu-id="8bd99-164">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Okno konsoli z wypisaniem przez aplikację 52 kart.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulate-the-order"></a><span data-ttu-id="8bd99-166">Manipulowanie zamówieniem</span><span class="sxs-lookup"><span data-stu-id="8bd99-166">Manipulate the Order</span></span>

<span data-ttu-id="8bd99-167">Następnie skoncentruj się na tym, jak będziesz tasować karty w talii.</span><span class="sxs-lookup"><span data-stu-id="8bd99-167">Next, focus on how you're going to shuffle the cards in the deck.</span></span> <span data-ttu-id="8bd99-168">Pierwszym krokiem w każdym dobrym shuffle jest podzielenie talii na dwie części.</span><span class="sxs-lookup"><span data-stu-id="8bd99-168">The first step in any good shuffle is to split the deck in two.</span></span> <span data-ttu-id="8bd99-169">I <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A> metody, które są częścią linq interfejsów API zapewniają tę funkcję dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="8bd99-169">The <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods that are part of the LINQ APIs provide that feature for you.</span></span> <span data-ttu-id="8bd99-170">Umieść je pod `foreach` pętlą:</span><span class="sxs-lookup"><span data-stu-id="8bd99-170">Place them underneath the `foreach` loop:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    // 52 cards in a deck, so 52 / 2 = 26
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
}
```

<span data-ttu-id="8bd99-171">Jednak nie ma metody shuffle, aby skorzystać z w standardowej bibliotece, więc będziesz musiał napisać własne.</span><span class="sxs-lookup"><span data-stu-id="8bd99-171">However, there's no shuffle method to take advantage of in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="8bd99-172">Metoda shuffle, którą będziesz tworzyć, ilustruje kilka technik, których będziesz używać z programami opartymi na LINQ, więc każda część tego procesu zostanie wyjaśniona w krokach.</span><span class="sxs-lookup"><span data-stu-id="8bd99-172">The shuffle method you'll be creating illustrates several techniques that you'll use with LINQ-based programs, so each part of this process will be explained in steps.</span></span>

<span data-ttu-id="8bd99-173">Aby dodać niektóre funkcje do interakcji z <xref:System.Collections.Generic.IEnumerable%601> tobą będzie można uzyskać z zapytania LINQ, należy napisać kilka specjalnych rodzajów metod [zwanych metodami rozszerzenia](../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="8bd99-173">In order to add some functionality to how you interact with the <xref:System.Collections.Generic.IEnumerable%601> you'll get back from LINQ queries, you'll need to write some special kinds of methods called [extension methods](../programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="8bd99-174">Krótko mówiąc, metoda rozszerzenia jest *metodą statyczną* specjalnego przeznaczenia, która dodaje nowe funkcje do już istniejącego typu bez konieczności modyfikowania oryginalnego typu, do którego chcesz dodać funkcje.</span><span class="sxs-lookup"><span data-stu-id="8bd99-174">Briefly, an extension method is a special purpose *static method* that adds new functionality to an already-existing type without having to modify the original type you want to add functionality to.</span></span>

<span data-ttu-id="8bd99-175">Nadaj metodom rozszerzenia nowy dom, dodając nowy plik `Extensions.cs`klasy *statycznej* do programu o nazwie , a następnie zacznij budować pierwszą metodę rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="8bd99-175">Give your extension methods a new home by adding a new *static* class file to your program called `Extensions.cs`, and then start building out the first extension method:</span></span>

```csharp
// Extensions.cs
using System;
using System.Collections.Generic;
using System.Linq;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>(this IEnumerable<T> first, IEnumerable<T> second)
        {
            // Your implementation will go here soon enough
        }
    }
}
```

<span data-ttu-id="8bd99-176">Spójrz na podpis metody na chwilę, w szczególności parametry:</span><span class="sxs-lookup"><span data-stu-id="8bd99-176">Look at the method signature for a moment, specifically the parameters:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="8bd99-177">Możesz zobaczyć dodanie modyfikatora `this` na pierwszy argument do metody.</span><span class="sxs-lookup"><span data-stu-id="8bd99-177">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="8bd99-178">Oznacza to, że można wywołać metodę tak, jakby była to metoda członkowski typu pierwszego argumentu.</span><span class="sxs-lookup"><span data-stu-id="8bd99-178">That means you call the method as though it were a member method of the type of the first argument.</span></span> <span data-ttu-id="8bd99-179">Ta deklaracja metody jest również zgodna ze standardowym `IEnumerable<T>`idiomem, w którym są typy danych wejściowych i wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="8bd99-179">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="8bd99-180">Ta praktyka umożliwia linq metody, które mają być połączone ze sobą w celu wykonywania bardziej złożonych zapytań.</span><span class="sxs-lookup"><span data-stu-id="8bd99-180">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

<span data-ttu-id="8bd99-181">Oczywiście, ponieważ dzielisz talię na połówki, musisz połączyć te połówki razem.</span><span class="sxs-lookup"><span data-stu-id="8bd99-181">Naturally, since you split the deck into halves, you'll need to join those halves together.</span></span> <span data-ttu-id="8bd99-182">W kodzie oznacza to, że będziesz wyliczać obie <xref:System.Linq.Enumerable.Take%2A> sekwencje, które zostały nabyte za pośrednictwem i <xref:System.Linq.Enumerable.Skip%2A> od razu, *`interleaving`* elementy i tworzenie jednej sekwencji: teraz tasowane talii kart.</span><span class="sxs-lookup"><span data-stu-id="8bd99-182">In code, this means you'll be enumerating both of the sequences you acquired through <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> at once, *`interleaving`* the elements, and creating one sequence: your now-shuffled deck of cards.</span></span> <span data-ttu-id="8bd99-183">Pisanie metody LINQ, która działa z dwiema <xref:System.Collections.Generic.IEnumerable%601> sekwencjami wymaga, aby zrozumieć, jak działa.</span><span class="sxs-lookup"><span data-stu-id="8bd99-183">Writing a LINQ method that works with two sequences requires that you understand how <xref:System.Collections.Generic.IEnumerable%601> works.</span></span>

<span data-ttu-id="8bd99-184">Interfejs <xref:System.Collections.Generic.IEnumerable%601> ma jedną <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>metodę: .</span><span class="sxs-lookup"><span data-stu-id="8bd99-184">The <xref:System.Collections.Generic.IEnumerable%601> interface has one method: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span></span> <span data-ttu-id="8bd99-185">Obiekt zwracany <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> przez ma metodę, aby przejść do następnego elementu i właściwość, która pobiera bieżący element w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="8bd99-185">The object returned by <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="8bd99-186">Użyjesz tych dwóch elementów członkowskich, aby wyliczyć kolekcję i zwrócić elementy.</span><span class="sxs-lookup"><span data-stu-id="8bd99-186">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="8bd99-187">Ta metoda przeplotu będzie metoda iterator, więc zamiast tworzenia kolekcji i zwracanie `yield return` kolekcji, należy użyć składni pokazano powyżej.</span><span class="sxs-lookup"><span data-stu-id="8bd99-187">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span>

<span data-ttu-id="8bd99-188">Oto implementacja tej metody:</span><span class="sxs-lookup"><span data-stu-id="8bd99-188">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="8bd99-189">Teraz, gdy już napisałeś tę metodę, wróć do `Main` metody i shuffle pokładu raz:</span><span class="sxs-lookup"><span data-stu-id="8bd99-189">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

```csharp
// Program.cs
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

## <a name="comparisons"></a><span data-ttu-id="8bd99-190">Porównania</span><span class="sxs-lookup"><span data-stu-id="8bd99-190">Comparisons</span></span>

<span data-ttu-id="8bd99-191">Ile przetasowań potrzeba, aby przywrócić talię do pierwotnego porządku?</span><span class="sxs-lookup"><span data-stu-id="8bd99-191">How many shuffles it takes to set the deck back to its original order?</span></span> <span data-ttu-id="8bd99-192">Aby się tego dowiedzieć, musisz napisać metodę, która określa, czy dwie sekwencje są równe.</span><span class="sxs-lookup"><span data-stu-id="8bd99-192">To find out, you'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="8bd99-193">Po tej metodzie musisz umieścić kod, który tasuje talię w pętli, i sprawdzić, kiedy talia jest z powrotem w kolejności.</span><span class="sxs-lookup"><span data-stu-id="8bd99-193">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="8bd99-194">Pisanie metody w celu ustalenia, czy dwie sekwencje są równe powinno być proste.</span><span class="sxs-lookup"><span data-stu-id="8bd99-194">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="8bd99-195">Jest to podobna struktura do metody, którą napisałeś, aby przetasować talię.</span><span class="sxs-lookup"><span data-stu-id="8bd99-195">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="8bd99-196">Tylko tym razem, `yield return`zamiast każdego elementu, porównasz pasujące elementy każdej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="8bd99-196">Only this time, instead of `yield return`ing each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="8bd99-197">Gdy cała sekwencja została wyliczona, jeśli każdy element pasuje, sekwencje są takie same:</span><span class="sxs-lookup"><span data-stu-id="8bd99-197">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="8bd99-198">Pokazuje to drugi idiom LINQ: metody terminala.</span><span class="sxs-lookup"><span data-stu-id="8bd99-198">This shows a second LINQ idiom: terminal methods.</span></span> <span data-ttu-id="8bd99-199">Przyjmują sekwencję jako dane wejściowe (lub w tym przypadku dwie sekwencje) i zwracają pojedynczą wartość skalarną.</span><span class="sxs-lookup"><span data-stu-id="8bd99-199">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="8bd99-200">Podczas korzystania z metod terminalowych, są one zawsze ostateczną metodą w łańcuchu metod dla kwerendy LINQ, stąd nazwa "terminal".</span><span class="sxs-lookup"><span data-stu-id="8bd99-200">When using terminal methods, they are always the final method in a chain of methods for a LINQ query, hence the name "terminal".</span></span>

<span data-ttu-id="8bd99-201">Można to zobaczyć w akcji, gdy używasz go do określenia, kiedy pokład jest z powrotem w oryginalnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="8bd99-201">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="8bd99-202">Umieść kod shuffle wewnątrz pętli i zatrzymaj się, gdy sekwencja `SequenceEquals()` jest z powrotem w oryginalnej kolejności, stosując metodę.</span><span class="sxs-lookup"><span data-stu-id="8bd99-202">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="8bd99-203">Widać, że zawsze będzie to metoda ostateczna w dowolnej kwerendzie, ponieważ zwraca pojedynczą wartość zamiast sekwencji:</span><span class="sxs-lookup"><span data-stu-id="8bd99-203">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

```csharp
// Program.cs
static void Main(string[] args)
{
    // Query for building the deck

    // Shuffling using InterleaveSequenceWith<T>();

    var times = 0;
    // We can re-use the shuffle variable from earlier, or you can make a new one
    shuffle = startingDeck;
    do
    {
        shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

        foreach (var card in shuffle)
        {
            Console.WriteLine(card);
        }
        Console.WriteLine();
        times++;

    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="8bd99-204">Uruchom kod, który masz do tej pory i zanotuj, jak talia zmienia układ na każdym shuffle.</span><span class="sxs-lookup"><span data-stu-id="8bd99-204">Run the code you've got so far and take note of how the deck rearranges on each shuffle.</span></span> <span data-ttu-id="8bd99-205">Po 8 tasowania (iteracje pętli do-while), deck powraca do oryginalnej konfiguracji, w której był podczas tworzenia go po raz pierwszy z początkowej kwerendy LINQ.</span><span class="sxs-lookup"><span data-stu-id="8bd99-205">After 8 shuffles (iterations of the do-while loop), the deck returns to the original configuration it was in when you first created it from the starting LINQ query.</span></span>

## <a name="optimizations"></a><span data-ttu-id="8bd99-206">Optymalizacje</span><span class="sxs-lookup"><span data-stu-id="8bd99-206">Optimizations</span></span>

<span data-ttu-id="8bd99-207">Przykład, który do tej pory został zbudowany, wykonuje *shuffle out,* gdzie górna i dolna karta pozostają takie same przy każdym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="8bd99-207">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="8bd99-208">Wytoczmy jedną zmianę: zamiast tego użyjemy *shuffle,* gdzie wszystkie 52 karty zmienią pozycję.</span><span class="sxs-lookup"><span data-stu-id="8bd99-208">Let's make one change: we'll use an *in shuffle* instead, where all 52 cards change position.</span></span> <span data-ttu-id="8bd99-209">W przypadku przetasowania przeplatasz talię, aby pierwsza karta w dolnej połowie stała się pierwszą kartą w talii.</span><span class="sxs-lookup"><span data-stu-id="8bd99-209">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="8bd99-210">Oznacza to, że ostatnia karta w górnej połowie staje się dolną kartą.</span><span class="sxs-lookup"><span data-stu-id="8bd99-210">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="8bd99-211">Jest to prosta zmiana w liczbie pojedynczej linii kodu.</span><span class="sxs-lookup"><span data-stu-id="8bd99-211">This is a simple change to a singular line of code.</span></span> <span data-ttu-id="8bd99-212">Zaktualizuj bieżącą kwerendę shuffle, <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A>przełączając pozycje i .</span><span class="sxs-lookup"><span data-stu-id="8bd99-212">Update the current shuffle query by switching the positions of <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span> <span data-ttu-id="8bd99-213">Spowoduje to zmianę kolejności górnych i dolnych połówek talii:</span><span class="sxs-lookup"><span data-stu-id="8bd99-213">This will change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="8bd99-214">Uruchom program ponownie, a zobaczysz, że potrzeba 52 iteracji, aby talia sama się uporządkowała.</span><span class="sxs-lookup"><span data-stu-id="8bd99-214">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="8bd99-215">Zaczniesz również zauważać poważne pogorszenie wydajności, gdy program będzie nadal działał.</span><span class="sxs-lookup"><span data-stu-id="8bd99-215">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="8bd99-216">Istnieje wiele powodów.</span><span class="sxs-lookup"><span data-stu-id="8bd99-216">There are a number of reasons for this.</span></span> <span data-ttu-id="8bd99-217">Można rozwiązać jedną z głównych przyczyn tego spadku wydajności: nieefektywne wykorzystanie [*leniwej oceny*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8bd99-217">You can tackle one of the major causes of this performance drop: inefficient use of [*lazy evaluation*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="8bd99-218">Krótko mówiąc, ocena z opóźnieniem stwierdza, że ocena instrukcji nie jest wykonywana, dopóki nie jest potrzebna jej wartość.</span><span class="sxs-lookup"><span data-stu-id="8bd99-218">Briefly, lazy evaluation states that the evaluation of a statement is not performed until its value is needed.</span></span> <span data-ttu-id="8bd99-219">Zapytania LINQ są instrukcje, które są oceniane leniwie.</span><span class="sxs-lookup"><span data-stu-id="8bd99-219">LINQ queries are statements that are evaluated lazily.</span></span> <span data-ttu-id="8bd99-220">Sekwencje są generowane tylko wtedy, gdy są wymagane elementy.</span><span class="sxs-lookup"><span data-stu-id="8bd99-220">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="8bd99-221">Zazwyczaj jest to duża zaleta LINQ.</span><span class="sxs-lookup"><span data-stu-id="8bd99-221">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="8bd99-222">Jednak w użyciu, takich jak ten program, powoduje to wykładniczy wzrost czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8bd99-222">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="8bd99-223">Pamiętaj, że wygenerowaliśmy oryginalną talię za pomocą zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="8bd99-223">Remember that we generated the original deck using a LINQ query.</span></span> <span data-ttu-id="8bd99-224">Każde shuffle jest generowany przez wykonanie trzech zapytań LINQ w poprzedniej talii.</span><span class="sxs-lookup"><span data-stu-id="8bd99-224">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="8bd99-225">Wszystkie te są wykonywane leniwie.</span><span class="sxs-lookup"><span data-stu-id="8bd99-225">All these are performed lazily.</span></span> <span data-ttu-id="8bd99-226">Oznacza to również, że są one wykonywane ponownie za każdym razem, gdy żądana jest sekwencja.</span><span class="sxs-lookup"><span data-stu-id="8bd99-226">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="8bd99-227">Do czasu dojście do 52 iteracji, jesteś regeneracji oryginalnej talii wiele, wiele razy.</span><span class="sxs-lookup"><span data-stu-id="8bd99-227">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="8bd99-228">Napiszmy dziennik, aby zademonstrować to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8bd99-228">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="8bd99-229">Następnie naprawisz to.</span><span class="sxs-lookup"><span data-stu-id="8bd99-229">Then, you'll fix it.</span></span>

<span data-ttu-id="8bd99-230">W `Extensions.cs` pliku wpisz lub skopiuj poniższą metodę.</span><span class="sxs-lookup"><span data-stu-id="8bd99-230">In your `Extensions.cs` file, type in or copy the method below.</span></span> <span data-ttu-id="8bd99-231">Ta metoda rozszerzenia tworzy `debug.log` nowy plik wywoływany w katalogu projektu i rejestruje, jakie zapytanie jest obecnie wykonywane do pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="8bd99-231">This extension method creates a new file called `debug.log` within your project directory and records what query is currently being executed to the log file.</span></span> <span data-ttu-id="8bd99-232">Tę metodę rozszerzenia można dołączać do dowolnej kwerendy, aby oznaczyć wykonaną kwerendę.</span><span class="sxs-lookup"><span data-stu-id="8bd99-232">This extension method can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="8bd99-233">Zobaczysz czerwoną fałszon pod `File`, co oznacza, że nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="8bd99-233">You will see a red squiggle under `File`, meaning it doesn't exist.</span></span> <span data-ttu-id="8bd99-234">Nie będzie kompilować, ponieważ kompilator nie `File` wie, co to jest.</span><span class="sxs-lookup"><span data-stu-id="8bd99-234">It won't compile, since the compiler doesn't know what `File` is.</span></span> <span data-ttu-id="8bd99-235">Aby rozwiązać ten problem, upewnij się, aby dodać następujący `Extensions.cs`wiersz kodu w pierwszym wierszu w:</span><span class="sxs-lookup"><span data-stu-id="8bd99-235">To solve this problem, make sure to add the following line of code under the very first line in `Extensions.cs`:</span></span>

```csharp
using System.IO;
```

<span data-ttu-id="8bd99-236">Powinno to rozwiązać problem i czerwony błąd znika.</span><span class="sxs-lookup"><span data-stu-id="8bd99-236">This should solve the issue and the red error disappears.</span></span>

<span data-ttu-id="8bd99-237">Następnie instrument definicji każdego zapytania z komunikatem dziennika:</span><span class="sxs-lookup"><span data-stu-id="8bd99-237">Next, instrument the definition of each query with a log message:</span></span>

```csharp
// Program.cs
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
        // Out shuffle
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        // In shuffle
        shuffle = shuffle.Skip(26).LogQuery("Bottom Half")
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

<span data-ttu-id="8bd99-238">Należy zauważyć, że nie rejestrujesz się za każdym razem, gdy uzyskujesz dostęp do zapytania.</span><span class="sxs-lookup"><span data-stu-id="8bd99-238">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="8bd99-239">Logujesz się tylko podczas tworzenia oryginalnej kwerendy.</span><span class="sxs-lookup"><span data-stu-id="8bd99-239">You log only when you create the original query.</span></span> <span data-ttu-id="8bd99-240">Program nadal zajmuje dużo czasu, aby uruchomić, ale teraz można zobaczyć, dlaczego.</span><span class="sxs-lookup"><span data-stu-id="8bd99-240">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="8bd99-241">Jeśli zabraknie cierpliwości uruchomiony w shuffle z rejestrowania włączone, przełącz się z powrotem do out shuffle.</span><span class="sxs-lookup"><span data-stu-id="8bd99-241">If you run out of patience running the in shuffle with logging turned on, switch back to the out shuffle.</span></span> <span data-ttu-id="8bd99-242">Nadal zobaczysz efekty oceny leniwy.</span><span class="sxs-lookup"><span data-stu-id="8bd99-242">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="8bd99-243">W jednym uruchomieniu wykonuje 2592 zapytań, w tym wszystkie wartości i powszedniania koloru.</span><span class="sxs-lookup"><span data-stu-id="8bd99-243">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="8bd99-244">Można zwiększyć wydajność kodu w tym miejscu, aby zmniejszyć liczbę wykonań, które można wykonać.</span><span class="sxs-lookup"><span data-stu-id="8bd99-244">You can improve the performance of the code here to reduce the number of executions you make.</span></span> <span data-ttu-id="8bd99-245">Prostą poprawką, którą można wprowadzić, jest *buforowanie* wyników oryginalnej kwerendy LINQ, która tworzy talię kart.</span><span class="sxs-lookup"><span data-stu-id="8bd99-245">A simple fix you can make is to *cache* the results of the original LINQ query that constructs the deck of cards.</span></span> <span data-ttu-id="8bd99-246">Obecnie wykonujesz zapytania raz za każdym razem, gdy pętla do-while przechodzi przez iterację, rekonstruując talię kart i przetasowania za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="8bd99-246">Currently, you're executing the queries again and again every time the do-while loop goes through an iteration, re-constructing the deck of cards and reshuffling it every time.</span></span> <span data-ttu-id="8bd99-247">Aby buforować talię kart, możesz wykorzystać <xref:System.Linq.Enumerable.ToArray%2A> metody <xref:System.Linq.Enumerable.ToList%2A>LINQ i ; po dodaniu ich do zapytań będą one wykonywać te same akcje, które im powiesz, ale teraz będą przechowywać wyniki w tablicy lub liście, w zależności od wybranej metody.</span><span class="sxs-lookup"><span data-stu-id="8bd99-247">To cache the deck of cards, you can leverage the LINQ methods <xref:System.Linq.Enumerable.ToArray%2A> and <xref:System.Linq.Enumerable.ToList%2A>; when you append them to the queries, they'll perform the same actions you've told them to, but now they'll store the results in an array or a list, depending on which method you choose to call.</span></span> <span data-ttu-id="8bd99-248">Dołącz metodę <xref:System.Linq.Enumerable.ToArray%2A> LINQ do obu zapytań i uruchom program ponownie:</span><span class="sxs-lookup"><span data-stu-id="8bd99-248">Append the LINQ method <xref:System.Linq.Enumerable.ToArray%2A> to both queries and run the program again:</span></span>

[!CODE-csharp[Main](../../../samples/snippets/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="8bd99-249">Teraz obecnie shuffle jest w dół do 30 zapytań.</span><span class="sxs-lookup"><span data-stu-id="8bd99-249">Now the out shuffle is down to 30 queries.</span></span> <span data-ttu-id="8bd99-250">Uruchom ponownie z in shuffle, a zobaczysz podobne ulepszenia: teraz wykonuje 162 zapytań.</span><span class="sxs-lookup"><span data-stu-id="8bd99-250">Run again with the in shuffle and you'll see similar improvements: it now executes 162 queries.</span></span>

<span data-ttu-id="8bd99-251">Należy pamiętać, że w tym przykładzie jest **przeznaczony** do podkreślenia przypadków użycia, gdzie leniwy oceny może powodować trudności w wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bd99-251">Please note that this example is **designed** to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="8bd99-252">Chociaż ważne jest, aby zobaczyć, gdzie ocena z opóźnieniem może mieć wpływ na wydajność kodu, równie ważne jest, aby zrozumieć, że nie wszystkie zapytania powinny działać z niecierpliwością.</span><span class="sxs-lookup"><span data-stu-id="8bd99-252">While it's important to see where lazy evaluation can impact code performance, it's equally important to understand that not all queries should run eagerly.</span></span> <span data-ttu-id="8bd99-253">Wydajność, którą poniesiesz bez użycia, <xref:System.Linq.Enumerable.ToArray%2A> wynika z tego, że każdy nowy układ talii kart jest zbudowany z poprzedniego układu.</span><span class="sxs-lookup"><span data-stu-id="8bd99-253">The performance hit you incur without using <xref:System.Linq.Enumerable.ToArray%2A> is because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="8bd99-254">Korzystanie z leniwej oceny oznacza, że każda nowa konfiguracja pokładu jest zbudowana z oryginalnej talii, nawet wykonując kod, który zbudował `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="8bd99-254">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="8bd99-255">To powoduje dużą ilość dodatkowej pracy.</span><span class="sxs-lookup"><span data-stu-id="8bd99-255">That causes a large amount of extra work.</span></span>

<span data-ttu-id="8bd99-256">W praktyce niektóre algorytmy działają dobrze przy użyciu chętnie oceny, a inne działają dobrze przy użyciu oceny leniwy.</span><span class="sxs-lookup"><span data-stu-id="8bd99-256">In practice, some algorithms run well using eager evaluation, and others run well using lazy evaluation.</span></span> <span data-ttu-id="8bd99-257">W przypadku codziennego użycia oceny z opóźnieniem jest zwykle lepszym wyborem, gdy źródło danych jest oddzielnyproces, jak aparat bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8bd99-257">For daily usage, lazy evaluation is usually a better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="8bd99-258">W przypadku baz danych oceny z opóźnieniem umożliwia bardziej złożonych zapytań do wykonania tylko jedną podróż w obie strony do procesu bazy danych i z powrotem do reszty kodu.</span><span class="sxs-lookup"><span data-stu-id="8bd99-258">For databases, lazy evaluation allows more complex queries to execute only one round trip to the database process and back to the rest of your code.</span></span> <span data-ttu-id="8bd99-259">LINQ jest elastyczny, niezależnie od tego, czy zdecydujesz się wykorzystać leniwą lub chętną ocenę, więc mierz procesy i wybieraj niezależnie od rodzaju oceny, która zapewnia najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="8bd99-259">LINQ is flexible whether you choose to utilize lazy or eager evaluation, so measure your processes and pick whichever kind of evaluation gives you the best performance.</span></span>

## <a name="conclusion"></a><span data-ttu-id="8bd99-260">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="8bd99-260">Conclusion</span></span>

<span data-ttu-id="8bd99-261">W tym projekcie omówiłeś:</span><span class="sxs-lookup"><span data-stu-id="8bd99-261">In this project, you covered:</span></span>

- <span data-ttu-id="8bd99-262">używanie zapytań LINQ do agregowania danych w sensowną sekwencję</span><span class="sxs-lookup"><span data-stu-id="8bd99-262">using LINQ queries to aggregate data into a meaningful sequence</span></span>
- <span data-ttu-id="8bd99-263">pisanie metod rozszerzenia w celu dodania własnych funkcji niestandardowych do zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="8bd99-263">writing Extension methods to add our own custom functionality to LINQ queries</span></span>
- <span data-ttu-id="8bd99-264">lokalizowanie obszarów w naszym kodzie, w których nasze zapytania LINQ mogą napotkać problemy z wydajnością, takie jak obniżona prędkość</span><span class="sxs-lookup"><span data-stu-id="8bd99-264">locating areas in our code where our LINQ queries might run into performance issues like degraded speed</span></span>
- <span data-ttu-id="8bd99-265">leniwy i chętnie oceny w odniesieniu do zapytań LINQ i implikacje mogą mieć na wydajność zapytań</span><span class="sxs-lookup"><span data-stu-id="8bd99-265">lazy and eager evaluation in regards to LINQ queries and the implications they might have on query performance</span></span>

<span data-ttu-id="8bd99-266">Oprócz LINQ, dowiedziałeś się trochę o technice magików używać do sztuczek karty.</span><span class="sxs-lookup"><span data-stu-id="8bd99-266">Aside from LINQ, you learned a bit about a technique magicians use for card tricks.</span></span> <span data-ttu-id="8bd99-267">Magowie używają losu Faro, ponieważ mogą kontrolować, gdzie każda karta porusza się w talii.</span><span class="sxs-lookup"><span data-stu-id="8bd99-267">Magicians use the Faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="8bd99-268">Teraz, gdy już wiesz, nie psuj go wszystkim innym!</span><span class="sxs-lookup"><span data-stu-id="8bd99-268">Now that you know, don't spoil it for everyone else!</span></span>

<span data-ttu-id="8bd99-269">Aby uzyskać więcej informacji na temat LINQ, zobacz:</span><span class="sxs-lookup"><span data-stu-id="8bd99-269">For more information on LINQ, see:</span></span>

- [<span data-ttu-id="8bd99-270">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8bd99-270">Language Integrated Query (LINQ)</span></span>](../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="8bd99-271">Wprowadzenie do LINQ</span><span class="sxs-lookup"><span data-stu-id="8bd99-271">Introduction to LINQ</span></span>](../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="8bd99-272">Podstawowe operacje zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="8bd99-272">Basic LINQ Query Operations (C#)</span></span>](../programming-guide/concepts/linq/basic-linq-query-operations.md)
- [<span data-ttu-id="8bd99-273">Transformacje danych z LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="8bd99-273">Data Transformations With LINQ (C#)</span></span>](../programming-guide/concepts/linq/data-transformations-with-linq.md)
- [<span data-ttu-id="8bd99-274">Składnia zapytania i metody w technologii LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="8bd99-274">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
- [<span data-ttu-id="8bd99-275">Funkcje C# obsługujące LINQ</span><span class="sxs-lookup"><span data-stu-id="8bd99-275">C# Features That Support LINQ</span></span>](../programming-guide/concepts/linq/features-that-support-linq.md)
