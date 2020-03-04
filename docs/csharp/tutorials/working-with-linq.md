---
title: Praca z technologią LINQ
description: W tym samouczku przedstawiono sposób generowania sekwencji przy użyciu LINQ, metod zapisu do użycia w zapytaniach LINQ i rozróżniania między eager i oceną z opóźnieniem.
ms.date: 10/29/2018
ms.technology: csharp-linq
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: ece001e82c0aa44a91999bea78d2fd695ff9362b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240018"
---
# <a name="work-with-language-integrated-query-linq"></a><span data-ttu-id="853f7-103">Korzystanie z zapytań zintegrowanych z językiem (LINQ)</span><span class="sxs-lookup"><span data-stu-id="853f7-103">Work with Language-Integrated Query (LINQ)</span></span>

## <a name="introduction"></a><span data-ttu-id="853f7-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="853f7-104">Introduction</span></span>

<span data-ttu-id="853f7-105">W tym samouczku przedstawiono funkcje platformy .NET Core i C# języka.</span><span class="sxs-lookup"><span data-stu-id="853f7-105">This tutorial teaches you features in .NET Core and the C# language.</span></span> <span data-ttu-id="853f7-106">Omawiane tematy:</span><span class="sxs-lookup"><span data-stu-id="853f7-106">You’ll learn how to:</span></span>

- <span data-ttu-id="853f7-107">Generuj sekwencje przy użyciu LINQ.</span><span class="sxs-lookup"><span data-stu-id="853f7-107">Generate sequences with LINQ.</span></span>
- <span data-ttu-id="853f7-108">Metody zapisu, które mogą być łatwo używane w zapytaniach LINQ.</span><span class="sxs-lookup"><span data-stu-id="853f7-108">Write methods that can be easily used in LINQ queries.</span></span>
- <span data-ttu-id="853f7-109">Rozróżnianie między eager i oceną z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="853f7-109">Distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="853f7-110">Poznasz te techniki, tworząc aplikację, która pokazuje jedną z podstawowych umiejętności dowolnego czarodziej: [Faro losowo](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="853f7-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="853f7-111">Krótko Faro losowo to technika, w której można podzielić talię kart dokładnie na połowę, a następnie losowo przeplata każdą kartę z każdej połowy w celu odbudowania oryginalnego talii.</span><span class="sxs-lookup"><span data-stu-id="853f7-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="853f7-112">Magicians użyć tej techniki, ponieważ każda karta znajduje się w znanej lokalizacji po każdym rozłożeniu losowym, a kolejność jest powtarzalnym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="853f7-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span>

<span data-ttu-id="853f7-113">Na potrzeby Twoich celów jest jasne spojrzenie na manipulowanie sekwencjami danych.</span><span class="sxs-lookup"><span data-stu-id="853f7-113">For your purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="853f7-114">Aplikacja, którą utworzysz, konstruuje talię kart, a następnie wykonuje sekwencję losową, pisząc sekwencję za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="853f7-114">The application you'll build constructs a card deck and then performs a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="853f7-115">Porównano również zaktualizowaną kolejność do oryginalnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="853f7-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="853f7-116">Ten samouczek zawiera wiele kroków.</span><span class="sxs-lookup"><span data-stu-id="853f7-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="853f7-117">Po każdym kroku można uruchomić aplikację i postępować według postępu.</span><span class="sxs-lookup"><span data-stu-id="853f7-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="853f7-118">Możesz również zobaczyć [ukończony przykład](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) w repozytorium GitHub/Samples.</span><span class="sxs-lookup"><span data-stu-id="853f7-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="853f7-119">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="853f7-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="853f7-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="853f7-120">Prerequisites</span></span>

<span data-ttu-id="853f7-121">Musisz skonfigurować maszynę do uruchamiania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="853f7-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="853f7-122">Instrukcje instalacji można znaleźć na stronie [pobierania programu .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="853f7-122">You can find the installation instructions on the [.NET Core Download](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="853f7-123">Możesz uruchomić tę aplikację w systemie Windows, Ubuntu Linux lub OS X lub w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="853f7-123">You can run this application on Windows, Ubuntu Linux, or OS X, or in a Docker container.</span></span> <span data-ttu-id="853f7-124">Musisz zainstalować swój ulubiony Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="853f7-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="853f7-125">Poniższe opisy wykorzystują [Visual Studio Code](https://code.visualstudio.com/) , który jest edytorem dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="853f7-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross-platform editor.</span></span> <span data-ttu-id="853f7-126">Można jednak korzystać z dowolnych narzędzi, z którymi masz doświadczenie.</span><span class="sxs-lookup"><span data-stu-id="853f7-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="853f7-127">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="853f7-127">Create the Application</span></span>

<span data-ttu-id="853f7-128">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="853f7-128">The first step is to create a new application.</span></span> <span data-ttu-id="853f7-129">Otwórz wiersz polecenia i Utwórz nowy katalog dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="853f7-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="853f7-130">Upewnij się, że bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="853f7-130">Make that the current directory.</span></span> <span data-ttu-id="853f7-131">Wpisz `dotnet new console` polecenia w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="853f7-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="853f7-132">Spowoduje to utworzenie plików początkowych dla podstawowej aplikacji "Hello world".</span><span class="sxs-lookup"><span data-stu-id="853f7-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="853f7-133">Jeśli wcześniej nie korzystano C# z [tego samouczka, ten samouczek](console-teleprompter.md) wyjaśnia strukturę C# programu.</span><span class="sxs-lookup"><span data-stu-id="853f7-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="853f7-134">Możesz przeczytać ten element, a następnie wrócić tutaj, aby dowiedzieć się więcej na temat LINQ.</span><span class="sxs-lookup"><span data-stu-id="853f7-134">You can read that and then return here to learn more about LINQ.</span></span>

## <a name="create-the-data-set"></a><span data-ttu-id="853f7-135">Tworzenie zestawu danych</span><span class="sxs-lookup"><span data-stu-id="853f7-135">Create the Data Set</span></span>

<span data-ttu-id="853f7-136">Przed rozpoczęciem upewnij się, że następujące wiersze znajdują się na początku pliku `Program.cs` wygenerowanego przez `dotnet new console`:</span><span class="sxs-lookup"><span data-stu-id="853f7-136">Before you begin, make sure that the following lines are at the top of the `Program.cs` file generated by `dotnet new console`:</span></span>

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="853f7-137">Jeśli te trzy wiersze (instrukcje`using`) nie znajdują się na początku pliku, nasz program nie zostanie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="853f7-137">If these three lines (`using` statements) aren't at the top of the file, our program will not compile.</span></span>

<span data-ttu-id="853f7-138">Teraz, gdy masz wszystkie odwołania, których potrzebujesz, weź pod uwagę co to jest talia kart.</span><span class="sxs-lookup"><span data-stu-id="853f7-138">Now that you have all of the references that you'll need, consider what constitutes a deck of cards.</span></span> <span data-ttu-id="853f7-139">Często talia kart gry ma cztery kolory, a każdy z nich ma trzynastie wartości.</span><span class="sxs-lookup"><span data-stu-id="853f7-139">Commonly, a deck of playing cards has four suits, and each suit has thirteen values.</span></span> <span data-ttu-id="853f7-140">Zwykle warto rozważyć utworzenie klasy `Card` po prawej stronie bat i wypełnianie kolekcji obiektów `Card`.</span><span class="sxs-lookup"><span data-stu-id="853f7-140">Normally, you might consider creating a `Card` class right off the bat and populating a collection of `Card` objects by hand.</span></span> <span data-ttu-id="853f7-141">Dzięki LINQ można być bardziej zwięzłe niż zwykły sposób tworzenia talii kart.</span><span class="sxs-lookup"><span data-stu-id="853f7-141">With LINQ, you can be more concise than the usual way of dealing with creating a deck of cards.</span></span> <span data-ttu-id="853f7-142">Zamiast tworzyć klasy `Card`, można utworzyć dwie sekwencje, aby reprezentować odpowiednio kolory i Range.</span><span class="sxs-lookup"><span data-stu-id="853f7-142">Instead of creating a `Card` class, you can create two sequences to represent suits and ranks, respectively.</span></span> <span data-ttu-id="853f7-143">Utworzysz bardzo prostą parę [*metod iteratorów*](../iterators.md#enumeration-sources-with-iterator-methods) , które będą generować Range i ubrania jako <xref:System.Collections.Generic.IEnumerable%601>s ciągów:</span><span class="sxs-lookup"><span data-stu-id="853f7-143">You'll create a really simple pair of [*iterator methods*](../iterators.md#enumeration-sources-with-iterator-methods) that will generate the ranks and suits as <xref:System.Collections.Generic.IEnumerable%601>s of strings:</span></span>

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

<span data-ttu-id="853f7-144">Umieść je poniżej metody `Main` w pliku `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="853f7-144">Place these underneath the `Main` method in your `Program.cs` file.</span></span> <span data-ttu-id="853f7-145">Te dwie metody wykorzystują składnię `yield return` do tworzenia sekwencji podczas jej uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="853f7-145">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="853f7-146">Kompilator kompiluje obiekt, który implementuje <xref:System.Collections.Generic.IEnumerable%601> i generuje sekwencję ciągów w miarę ich żądania.</span><span class="sxs-lookup"><span data-stu-id="853f7-146">The compiler builds an object that implements <xref:System.Collections.Generic.IEnumerable%601> and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="853f7-147">Teraz Użyj tych metod iteratora do utworzenia talii kart.</span><span class="sxs-lookup"><span data-stu-id="853f7-147">Now, use these iterator methods to create the deck of cards.</span></span> <span data-ttu-id="853f7-148">Kwerenda LINQ zostanie umieszczona w naszej metodzie `Main`.</span><span class="sxs-lookup"><span data-stu-id="853f7-148">You'll place the LINQ query in our `Main` method.</span></span> <span data-ttu-id="853f7-149">Oto jak wygląda:</span><span class="sxs-lookup"><span data-stu-id="853f7-149">Here's a look at it:</span></span>

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

<span data-ttu-id="853f7-150">Wielo`from`owe klauzule tworzą <xref:System.Linq.Enumerable.SelectMany%2A>, który tworzy jedną sekwencję od łączenia każdego elementu w pierwszej sekwencji z każdym elementem w drugiej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="853f7-150">The multiple `from` clauses produce a <xref:System.Linq.Enumerable.SelectMany%2A>, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="853f7-151">Kolejność jest ważna dla naszych celów.</span><span class="sxs-lookup"><span data-stu-id="853f7-151">The order is important for our purposes.</span></span> <span data-ttu-id="853f7-152">Pierwszy element w pierwszej sekwencji źródłowej (kolory) jest połączony z każdym elementem w drugiej sekwencji (rangi).</span><span class="sxs-lookup"><span data-stu-id="853f7-152">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Ranks).</span></span> <span data-ttu-id="853f7-153">Spowoduje to wygenerowanie wszystkich trzynastu kart pierwszego koloru.</span><span class="sxs-lookup"><span data-stu-id="853f7-153">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="853f7-154">Ten proces jest powtarzany przy każdym elemencie w pierwszej sekwencji (kolory).</span><span class="sxs-lookup"><span data-stu-id="853f7-154">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="853f7-155">Wynik końcowy to talia kart uporządkowanych według kolorów, a następnie wartości.</span><span class="sxs-lookup"><span data-stu-id="853f7-155">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="853f7-156">Należy pamiętać, że niezależnie od tego, czy użytkownik zdecyduje się pisać składnik LINQ we wskazanej powyżej składni zapytania lub użyć składni metody zamiast tego, zawsze możliwe jest przechodzenie z jednej formy składni.</span><span class="sxs-lookup"><span data-stu-id="853f7-156">It's important to keep in mind that whether you choose to write your LINQ in the query syntax used above or use method syntax instead, it's always possible to go from one form of syntax to the other.</span></span> <span data-ttu-id="853f7-157">Powyższe zapytanie zapisywane w składni zapytania można napisać w składni metody jako:</span><span class="sxs-lookup"><span data-stu-id="853f7-157">The above query written in query syntax can be written in method syntax as:</span></span>

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

<span data-ttu-id="853f7-158">Kompilator tłumaczy instrukcje LINQ zapisywane z składnią zapytania na równoważną składnię wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="853f7-158">The compiler translates LINQ statements written with query syntax into the equivalent method call syntax.</span></span> <span data-ttu-id="853f7-159">W związku z tym, niezależnie od wyboru składni, dwie wersje zapytania dają ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="853f7-159">Therefore, regardless of your syntax choice, the two versions of the query produce the same result.</span></span> <span data-ttu-id="853f7-160">Wybierz, która składnia najlepiej sprawdza się w danej sytuacji: na przykład jeśli pracujesz w zespole, w którym niektórzy członkowie mają problemy ze składnią metody, spróbuj użyć składni zapytania.</span><span class="sxs-lookup"><span data-stu-id="853f7-160">Choose which syntax works best for your situation: for instance, if you're working in a team where some of the members have difficulty with method syntax, try to prefer using query syntax.</span></span>

<span data-ttu-id="853f7-161">Zacznij korzystać z przykładu skompilowanego w tym punkcie.</span><span class="sxs-lookup"><span data-stu-id="853f7-161">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="853f7-162">Spowoduje to wyświetlenie wszystkich kart 52 na pokładzie.</span><span class="sxs-lookup"><span data-stu-id="853f7-162">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="853f7-163">Przydatne może być uruchomienie tego przykładu w debugerze, aby obserwować sposób wykonywania `Suits()` i `Ranks()` metod.</span><span class="sxs-lookup"><span data-stu-id="853f7-163">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Ranks()` methods execute.</span></span> <span data-ttu-id="853f7-164">Można jasno zobaczyć, że każdy ciąg w każdej sekwencji jest generowany tylko w razie konieczności.</span><span class="sxs-lookup"><span data-stu-id="853f7-164">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Okno konsoli z zapisaniem aplikacji z kartami 52.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulate-the-order"></a><span data-ttu-id="853f7-166">Manipulowanie kolejnością</span><span class="sxs-lookup"><span data-stu-id="853f7-166">Manipulate the Order</span></span>

<span data-ttu-id="853f7-167">Następnie należy skoncentrować się na tym, w jaki sposób mają być losowo używane karty na pokładzie.</span><span class="sxs-lookup"><span data-stu-id="853f7-167">Next, focus on how you're going to shuffle the cards in the deck.</span></span> <span data-ttu-id="853f7-168">Pierwszym krokiem w każdym dobrym rozbiciem jest podzielenie talii na dwa.</span><span class="sxs-lookup"><span data-stu-id="853f7-168">The first step in any good shuffle is to split the deck in two.</span></span> <span data-ttu-id="853f7-169">Metody <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A>, które są częścią interfejsów API LINQ, udostępniają tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="853f7-169">The <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods that are part of the LINQ APIs provide that feature for you.</span></span> <span data-ttu-id="853f7-170">Umieść je poniżej pętli `foreach`:</span><span class="sxs-lookup"><span data-stu-id="853f7-170">Place them underneath the `foreach` loop:</span></span>

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

<span data-ttu-id="853f7-171">Jednak nie ma metody losowej, aby skorzystać z funkcji w bibliotece standardowej, więc musisz napisać własny.</span><span class="sxs-lookup"><span data-stu-id="853f7-171">However, there's no shuffle method to take advantage of in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="853f7-172">Metoda Losowa, która zostanie utworzona, ilustruje kilka technik, które będą używane z programami LINQ, więc każda część tego procesu zostanie omówiona w krokach.</span><span class="sxs-lookup"><span data-stu-id="853f7-172">The shuffle method you'll be creating illustrates several techniques that you'll use with LINQ-based programs, so each part of this process will be explained in steps.</span></span>

<span data-ttu-id="853f7-173">Aby dodać niektóre funkcje do korzystania z <xref:System.Collections.Generic.IEnumerable%601> można wrócić z zapytań LINQ, należy napisać specjalne rodzaje metod nazywanych [metodami rozszerzenia](../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="853f7-173">In order to add some functionality to how you interact with the <xref:System.Collections.Generic.IEnumerable%601> you'll get back from LINQ queries, you'll need to write some special kinds of methods called [extension methods](../programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="853f7-174">Krótko Metoda rozszerzenia to *metoda statyczna* specjalnego przeznaczenia, która dodaje nową funkcję do już istniejącego typu bez konieczności modyfikowania oryginalnego typu, do którego ma zostać dodana funkcja.</span><span class="sxs-lookup"><span data-stu-id="853f7-174">Briefly, an extension method is a special purpose *static method* that adds new functionality to an already-existing type without having to modify the original type you want to add functionality to.</span></span>

<span data-ttu-id="853f7-175">Nadaj rozszerzeniom nowe metody, dodając nowy plik *statycznej* klasy do programu o nazwie `Extensions.cs`, a następnie rozpocznij tworzenie pierwszej metody rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="853f7-175">Give your extension methods a new home by adding a new *static* class file to your program called `Extensions.cs`, and then start building out the first extension method:</span></span>

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

<span data-ttu-id="853f7-176">Zapoznaj się z chwilą podpis metody, a w tym parametry:</span><span class="sxs-lookup"><span data-stu-id="853f7-176">Look at the method signature for a moment, specifically the parameters:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="853f7-177">Możesz zobaczyć dodanie modyfikatora `this` pierwszego argumentu do metody.</span><span class="sxs-lookup"><span data-stu-id="853f7-177">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="853f7-178">Oznacza to, że wywoływana jest metoda, tak jakby była to metoda członkowska typu pierwszego argumentu.</span><span class="sxs-lookup"><span data-stu-id="853f7-178">That means you call the method as though it were a member method of the type of the first argument.</span></span> <span data-ttu-id="853f7-179">Ta deklaracja metody jest również zgodna ze standardową idiom, w którym typy wejściowe i wyjściowe są `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="853f7-179">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="853f7-180">To rozwiązanie umożliwia łączenie metod LINQ ze sobą w celu wykonywania bardziej złożonych zapytań.</span><span class="sxs-lookup"><span data-stu-id="853f7-180">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

<span data-ttu-id="853f7-181">Naturalnie, ze względu na rozdzielenie talii na połowy, należy dołączyć te połówki razem.</span><span class="sxs-lookup"><span data-stu-id="853f7-181">Naturally, since you split the deck into halves, you'll need to join those halves together.</span></span> <span data-ttu-id="853f7-182">W kodzie oznacza to, że zostaną wyliczone obie sekwencje nabyte za pośrednictwem <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> na raz, *`interleaving`* elementów i utworzenie jednej sekwencji: teraz rozjmowana talia kart.</span><span class="sxs-lookup"><span data-stu-id="853f7-182">In code, this means you'll be enumerating both of the sequences you acquired through <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> at once, *`interleaving`* the elements, and creating one sequence: your now-shuffled deck of cards.</span></span> <span data-ttu-id="853f7-183">Pisanie metody LINQ, która współpracuje z dwoma sekwencjami, wymaga zrozumienia sposobu działania <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="853f7-183">Writing a LINQ method that works with two sequences requires that you understand how <xref:System.Collections.Generic.IEnumerable%601> works.</span></span>

<span data-ttu-id="853f7-184">Interfejs <xref:System.Collections.Generic.IEnumerable%601> ma jedną metodę: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="853f7-184">The <xref:System.Collections.Generic.IEnumerable%601> interface has one method: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span></span> <span data-ttu-id="853f7-185">Obiekt zwrócony przez <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> ma metodę do przejścia do następnego elementu i właściwość, która pobiera bieżący element w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="853f7-185">The object returned by <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="853f7-186">Te dwa elementy członkowskie będą używane do wyliczenia kolekcji i zwrócenia elementów.</span><span class="sxs-lookup"><span data-stu-id="853f7-186">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="853f7-187">Ta metoda przeplotu będzie metodą iteratora, dlatego zamiast kompilowania kolekcji i zwracania kolekcji, użyj składni `yield return` pokazanej powyżej.</span><span class="sxs-lookup"><span data-stu-id="853f7-187">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span>

<span data-ttu-id="853f7-188">Oto implementacja tej metody:</span><span class="sxs-lookup"><span data-stu-id="853f7-188">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="853f7-189">Teraz, po zapisaniu tej metody, Wróć do metody `Main` i przetwórz losowo talię:</span><span class="sxs-lookup"><span data-stu-id="853f7-189">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

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

## <a name="comparisons"></a><span data-ttu-id="853f7-190">Porównania</span><span class="sxs-lookup"><span data-stu-id="853f7-190">Comparisons</span></span>

<span data-ttu-id="853f7-191">Ile trwa losowo, aby ustawić pokład z powrotem do oryginalnej kolejności?</span><span class="sxs-lookup"><span data-stu-id="853f7-191">How many shuffles it takes to set the deck back to its original order?</span></span> <span data-ttu-id="853f7-192">Aby dowiedzieć się, należy napisać metodę, która określa, czy dwie sekwencje są równe.</span><span class="sxs-lookup"><span data-stu-id="853f7-192">To find out, you'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="853f7-193">Po zastosowaniu tej metody należy umieścić kod, który wystawia talię w pętli, i sprawdzić, czy talia jest odwrócona.</span><span class="sxs-lookup"><span data-stu-id="853f7-193">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="853f7-194">Pisanie metody w celu ustalenia, czy dwie sekwencje są równe, powinny być bezpośrednie.</span><span class="sxs-lookup"><span data-stu-id="853f7-194">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="853f7-195">Jest to podobna struktura do metody, która została zapisana w celu rozdzielenia talii.</span><span class="sxs-lookup"><span data-stu-id="853f7-195">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="853f7-196">Tylko ten czas, a nie `yield return`Wykorzystaj każdego elementu, porównano pasujące elementy każdej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="853f7-196">Only this time, instead of `yield return`ing each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="853f7-197">Gdy cała sekwencja została wyliczona, jeśli każdy element jest zgodny, sekwencje są takie same:</span><span class="sxs-lookup"><span data-stu-id="853f7-197">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="853f7-198">Przedstawiono w nim drugą LINQ idiom: metody terminalowe.</span><span class="sxs-lookup"><span data-stu-id="853f7-198">This shows a second LINQ idiom: terminal methods.</span></span> <span data-ttu-id="853f7-199">Przyjmuje sekwencję jako dane wejściowe (lub w tym przypadku dwie sekwencje) i zwracają pojedynczą wartość skalarną.</span><span class="sxs-lookup"><span data-stu-id="853f7-199">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="853f7-200">W przypadku korzystania z metod terminalu są zawsze końcową metodą w łańcuchu metod dla zapytania LINQ, w związku z czym nazwa "Terminal".</span><span class="sxs-lookup"><span data-stu-id="853f7-200">When using terminal methods, they are always the final method in a chain of methods for a LINQ query, hence the name "terminal".</span></span>

<span data-ttu-id="853f7-201">Ten element można zobaczyć w działaniu, gdy jest on używany do określenia, kiedy talia zostanie przywrócona w oryginalnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="853f7-201">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="853f7-202">Umieść kod losowy wewnątrz pętli i Zatrzymaj, gdy sekwencja zostanie przywrócona w oryginalnej kolejności, stosując metodę `SequenceEquals()`.</span><span class="sxs-lookup"><span data-stu-id="853f7-202">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="853f7-203">Można zobaczyć, że zawsze będzie to Ostatnia metoda w dowolnych zapytania, ponieważ zwraca jedną wartość zamiast sekwencji:</span><span class="sxs-lookup"><span data-stu-id="853f7-203">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

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

<span data-ttu-id="853f7-204">Uruchom kod, który został już osiągnięty, i zanotuj, jak talia jest zmieniana na każdym losowo.</span><span class="sxs-lookup"><span data-stu-id="853f7-204">Run the code you've got so far and take note of how the deck rearranges on each shuffle.</span></span> <span data-ttu-id="853f7-205">Po 8 losowo (iteracji pętli "do-while") na pokładzie zostanie przywrócona oryginalna konfiguracja, która znajdowała się podczas pierwszego tworzenia go na podstawie uruchomienia zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="853f7-205">After 8 shuffles (iterations of the do-while loop), the deck returns to the original configuration it was in when you first created it from the starting LINQ query.</span></span>

## <a name="optimizations"></a><span data-ttu-id="853f7-206">Optymalizacje</span><span class="sxs-lookup"><span data-stu-id="853f7-206">Optimizations</span></span>

<span data-ttu-id="853f7-207">Utworzona przez Ciebie przykład jest wykonywana *losowo*, gdy karty górne i dolne pozostają takie same w każdym przebiegu.</span><span class="sxs-lookup"><span data-stu-id="853f7-207">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="853f7-208">Wprowadźmy jedną zmianę: zamiast tego będziemy używać *w* tym miejscu, gdzie wszystkie karty 52 zmieniają pozycję.</span><span class="sxs-lookup"><span data-stu-id="853f7-208">Let's make one change: we'll use an *in shuffle* instead, where all 52 cards change position.</span></span> <span data-ttu-id="853f7-209">W przypadku losowego odtwarzania talii należy pozostawać, aby pierwsza karta w dolnej połowie stała się pierwszą kartą na pokładzie.</span><span class="sxs-lookup"><span data-stu-id="853f7-209">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="853f7-210">Oznacza to, że ostatnia karta w górnej połowie zmieni się na najniższą kartę.</span><span class="sxs-lookup"><span data-stu-id="853f7-210">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="853f7-211">Jest to prosta zmiana w pojedynczej linii kodu.</span><span class="sxs-lookup"><span data-stu-id="853f7-211">This is a simple change to a singular line of code.</span></span> <span data-ttu-id="853f7-212">Zaktualizuj bieżące losowe zapytanie, przełączając pozycje <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="853f7-212">Update the current shuffle query by switching the positions of <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span> <span data-ttu-id="853f7-213">Spowoduje to zmianę kolejności górnej i dolnej części talii:</span><span class="sxs-lookup"><span data-stu-id="853f7-213">This will change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="853f7-214">Uruchom program ponownie, a zobaczysz, że dla talii zostanie wykonanych 52 iteracji na potrzeby zmiany kolejności.</span><span class="sxs-lookup"><span data-stu-id="853f7-214">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="853f7-215">Należy również pamiętać o poważnym obniżeniu wydajności, gdy program będzie kontynuował pracę.</span><span class="sxs-lookup"><span data-stu-id="853f7-215">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="853f7-216">Istnieje kilka przyczyn tego działania.</span><span class="sxs-lookup"><span data-stu-id="853f7-216">There are a number of reasons for this.</span></span> <span data-ttu-id="853f7-217">Możesz skorzystać z jednej z głównych przyczyn tego spadku wydajności: niewydajne użycie [*oceny z opóźnieniem*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="853f7-217">You can tackle one of the major causes of this performance drop: inefficient use of [*lazy evaluation*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="853f7-218">Krótko, z opóźnieniem, że Ocena instrukcji nie jest wykonywana, dopóki jej wartość nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="853f7-218">Briefly, lazy evaluation states that the evaluation of a statement is not performed until its value is needed.</span></span> <span data-ttu-id="853f7-219">Zapytania LINQ to instrukcje, które są oceniane opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="853f7-219">LINQ queries are statements that are evaluated lazily.</span></span> <span data-ttu-id="853f7-220">Sekwencje są generowane tylko w przypadku, gdy są żądane elementy.</span><span class="sxs-lookup"><span data-stu-id="853f7-220">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="853f7-221">Zwykle jest to główna korzyść dla LINQ.</span><span class="sxs-lookup"><span data-stu-id="853f7-221">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="853f7-222">Jednak w przypadku użycia takiego jak ten program powoduje wzrost wykładniczy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="853f7-222">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="853f7-223">Należy pamiętać, że wygenerowałeś oryginalne talie przy użyciu zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="853f7-223">Remember that we generated the original deck using a LINQ query.</span></span> <span data-ttu-id="853f7-224">Każda losowo jest generowana przez wykonywanie trzech zapytań LINQ na poprzednim talii.</span><span class="sxs-lookup"><span data-stu-id="853f7-224">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="853f7-225">Wszystkie te są wykonywane opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="853f7-225">All these are performed lazily.</span></span> <span data-ttu-id="853f7-226">Oznacza to również, że są wykonywane ponownie przy każdym żądaniu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="853f7-226">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="853f7-227">Po otrzymaniu do iteracji 52nd można ponownie wygenerować oryginalny tali wiele razy.</span><span class="sxs-lookup"><span data-stu-id="853f7-227">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="853f7-228">Napiszmy dziennik, aby zademonstrować to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="853f7-228">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="853f7-229">Następnie należy rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="853f7-229">Then, you'll fix it.</span></span>

<span data-ttu-id="853f7-230">W pliku `Extensions.cs` wpisz lub skopiuj metodę poniżej.</span><span class="sxs-lookup"><span data-stu-id="853f7-230">In your `Extensions.cs` file, type in or copy the method below.</span></span> <span data-ttu-id="853f7-231">Ta metoda rozszerzenia tworzy nowy plik o nazwie `debug.log` w katalogu projektu i rejestruje, jakie zapytanie jest aktualnie wykonywane w pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="853f7-231">This extension method creates a new file called `debug.log` within your project directory and records what query is currently being executed to the log file.</span></span> <span data-ttu-id="853f7-232">Tę metodę rozszerzenia można dołączyć do dowolnego zapytania, aby oznaczyć, że zapytanie zostało wykonane.</span><span class="sxs-lookup"><span data-stu-id="853f7-232">This extension method can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="853f7-233">Zostanie wyświetlona czerwona zygzakowata `File`, co oznacza, że nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="853f7-233">You will see a red squiggle under `File`, meaning it doesn't exist.</span></span> <span data-ttu-id="853f7-234">Nie kompiluje się, ponieważ kompilator nie wie, co `File`.</span><span class="sxs-lookup"><span data-stu-id="853f7-234">It won't compile, since the compiler doesn't know what `File` is.</span></span> <span data-ttu-id="853f7-235">Aby rozwiązać ten problem, pamiętaj, aby dodać następujący wiersz kodu poniżej pierwszego wiersza w `Extensions.cs`:</span><span class="sxs-lookup"><span data-stu-id="853f7-235">To solve this problem, make sure to add the following line of code under the very first line in `Extensions.cs`:</span></span>

```csharp
using System.IO;
```

<span data-ttu-id="853f7-236">Powinno to rozwiązać problem, a czerwony błąd znika.</span><span class="sxs-lookup"><span data-stu-id="853f7-236">This should solve the issue and the red error disappears.</span></span>

<span data-ttu-id="853f7-237">Następnie instrument definicji każdego zapytania z komunikatem dziennika:</span><span class="sxs-lookup"><span data-stu-id="853f7-237">Next, instrument the definition of each query with a log message:</span></span>

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

<span data-ttu-id="853f7-238">Należy zauważyć, że nie rejestruje się za każdym razem, gdy uzyskujesz dostęp do zapytania.</span><span class="sxs-lookup"><span data-stu-id="853f7-238">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="853f7-239">Rejestruje się tylko podczas tworzenia oryginalnego zapytania.</span><span class="sxs-lookup"><span data-stu-id="853f7-239">You log only when you create the original query.</span></span> <span data-ttu-id="853f7-240">Uruchomienie programu nadal trwa długo, ale teraz można zobaczyć dlaczego.</span><span class="sxs-lookup"><span data-stu-id="853f7-240">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="853f7-241">W przypadku wypróbowania korzystania z trybu losowania z włączonym rejestrowaniem, przełącz się z powrotem na konfigurację losową.</span><span class="sxs-lookup"><span data-stu-id="853f7-241">If you run out of patience running the in shuffle with logging turned on, switch back to the out shuffle.</span></span> <span data-ttu-id="853f7-242">Nadal zobaczysz efekty oceny z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="853f7-242">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="853f7-243">W jednym przebiegu są wykonywane zapytania 2592, w tym cała wartość i generowanie koloru.</span><span class="sxs-lookup"><span data-stu-id="853f7-243">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="853f7-244">W tym miejscu można poprawić wydajność kodu, aby zmniejszyć liczbę wykonanych wykonań.</span><span class="sxs-lookup"><span data-stu-id="853f7-244">You can improve the performance of the code here to reduce the number of executions you make.</span></span> <span data-ttu-id="853f7-245">Prosta poprawka, którą można wprowadzić, to *buforowanie* wyników oryginalnego zapytania LINQ, które konstruuje talię kart.</span><span class="sxs-lookup"><span data-stu-id="853f7-245">A simple fix you can make is to *cache* the results of the original LINQ query that constructs the deck of cards.</span></span> <span data-ttu-id="853f7-246">Obecnie wykonujesz zapytania ponownie i ponownie za każdym razem, gdy pętla do-while przechodzi przez iterację, należy ponownie skonstruować talię kart i reshuffling je za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="853f7-246">Currently, you're executing the queries again and again every time the do-while loop goes through an iteration, re-constructing the deck of cards and reshuffling it every time.</span></span> <span data-ttu-id="853f7-247">Aby buforować talię kart, można wykorzystać metody LINQ <xref:System.Linq.Enumerable.ToArray%2A> i <xref:System.Linq.Enumerable.ToList%2A>; Po dołączeniu ich do zapytań będą one wykonywały te same akcje, które zostały przez Ciebie zapamiętane, ale teraz przechowują wyniki w tablicy lub liście, w zależności od wybranej metody do wywołania.</span><span class="sxs-lookup"><span data-stu-id="853f7-247">To cache the deck of cards, you can leverage the LINQ methods <xref:System.Linq.Enumerable.ToArray%2A> and <xref:System.Linq.Enumerable.ToList%2A>; when you append them to the queries, they'll perform the same actions you've told them to, but now they'll store the results in an array or a list, depending on which method you choose to call.</span></span> <span data-ttu-id="853f7-248">Dołącz metodę LINQ <xref:System.Linq.Enumerable.ToArray%2A> do obu zapytań i ponownie uruchom program:</span><span class="sxs-lookup"><span data-stu-id="853f7-248">Append the LINQ method <xref:System.Linq.Enumerable.ToArray%2A> to both queries and run the program again:</span></span>

[!CODE-csharp[Main](../../../samples/snippets/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="853f7-249">Teraz wychodząca wartość jest wyłączana do 30 zapytań.</span><span class="sxs-lookup"><span data-stu-id="853f7-249">Now the out shuffle is down to 30 queries.</span></span> <span data-ttu-id="853f7-250">Uruchom ponownie z użyciem funkcji losowej i zobaczysz podobne udoskonalenia: teraz wykonuje zapytania 162.</span><span class="sxs-lookup"><span data-stu-id="853f7-250">Run again with the in shuffle and you'll see similar improvements: it now executes 162 queries.</span></span>

<span data-ttu-id="853f7-251">Należy pamiętać, że ten przykład został **zaprojektowany** w celu wyróżnienia przypadków użycia, gdy Ocena z opóźnieniem może spowodować problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="853f7-251">Please note that this example is **designed** to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="853f7-252">Chociaż ważne jest, aby sprawdzić, gdzie Ocena z opóźnieniem może wpłynąć na wydajność kodu, należy jednak pamiętać, że nie wszystkie zapytania powinny uruchamiać eagerly.</span><span class="sxs-lookup"><span data-stu-id="853f7-252">While it's important to see where lazy evaluation can impact code performance, it's equally important to understand that not all queries should run eagerly.</span></span> <span data-ttu-id="853f7-253">Trafienie wydajności, które pozostało bez użycia <xref:System.Linq.Enumerable.ToArray%2A> to ponieważ każde nowe rozmieszczenie kart jest zbudowane z poprzedniego rozmieszczenia.</span><span class="sxs-lookup"><span data-stu-id="853f7-253">The performance hit you incur without using <xref:System.Linq.Enumerable.ToArray%2A> is because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="853f7-254">Użycie oceny z opóźnieniem oznacza, że każda nowa konfiguracja jest tworzona na podstawie oryginalnego pokładu, nawet w przypadku wykonywania kodu, który został skompilowany `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="853f7-254">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="853f7-255">Powoduje to znaczną ilość dodatkowego nakładu pracy.</span><span class="sxs-lookup"><span data-stu-id="853f7-255">That causes a large amount of extra work.</span></span>

<span data-ttu-id="853f7-256">W przypadku niektórych algorytmów działa dobrze przy użyciu oceny eager, a inne działają dobrze przy użyciu oceny z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="853f7-256">In practice, some algorithms run well using eager evaluation, and others run well using lazy evaluation.</span></span> <span data-ttu-id="853f7-257">W przypadku codziennego użycia Ocena z opóźnieniem jest zazwyczaj lepszym wyborem, gdy źródło danych jest osobnym procesem, takim jak aparat bazy danych.</span><span class="sxs-lookup"><span data-stu-id="853f7-257">For daily usage, lazy evaluation is usually a better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="853f7-258">W przypadku baz danych Ocena z opóźnieniem umożliwia bardziej skomplikowane zapytania wykonywanie tylko jednej rundy w procesie bazy danych i powrót do reszty kodu.</span><span class="sxs-lookup"><span data-stu-id="853f7-258">For databases, lazy evaluation allows more complex queries to execute only one round trip to the database process and back to the rest of your code.</span></span> <span data-ttu-id="853f7-259">LINQ jest elastyczne, niezależnie od tego, czy zdecydujesz się na użycie oceny z opóźnieniem, czy eager, więc Zmierz procesy i wybieraj niezależny rodzaj oceny zapewnia najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="853f7-259">LINQ is flexible whether you choose to utilize lazy or eager evaluation, so measure your processes and pick whichever kind of evaluation gives you the best performance.</span></span>

## <a name="conclusion"></a><span data-ttu-id="853f7-260">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="853f7-260">Conclusion</span></span>

<span data-ttu-id="853f7-261">W tym projekcie omówiono następujące zagadnienia:</span><span class="sxs-lookup"><span data-stu-id="853f7-261">In this project, you covered:</span></span>

- <span data-ttu-id="853f7-262">Używanie zapytań LINQ do agregowania danych w zrozumiałej sekwencji</span><span class="sxs-lookup"><span data-stu-id="853f7-262">using LINQ queries to aggregate data into a meaningful sequence</span></span>
- <span data-ttu-id="853f7-263">Pisanie metod rozszerzających, aby dodać własną funkcję niestandardową do zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="853f7-263">writing Extension methods to add our own custom functionality to LINQ queries</span></span>
- <span data-ttu-id="853f7-264">Lokalizowanie obszarów w naszym kodzie, w których nasze zapytania LINQ mogą działać w przypadku problemów z wydajnością, takich jak obniżona szybkość</span><span class="sxs-lookup"><span data-stu-id="853f7-264">locating areas in our code where our LINQ queries might run into performance issues like degraded speed</span></span>
- <span data-ttu-id="853f7-265">obliczenia opóźnione i eager w odniesieniu do zapytań LINQ oraz implikacje, które mogą mieć na wydajność zapytań</span><span class="sxs-lookup"><span data-stu-id="853f7-265">lazy and eager evaluation in regards to LINQ queries and the implications they might have on query performance</span></span>

<span data-ttu-id="853f7-266">Oprócz LINQ wyuczysz się, jak korzystać z techniki Magicians na wskazówki dotyczące kart.</span><span class="sxs-lookup"><span data-stu-id="853f7-266">Aside from LINQ, you learned a bit about a technique magicians use for card tricks.</span></span> <span data-ttu-id="853f7-267">Magicians używają Faro losowo, ponieważ mogą one kontrolować, gdzie każda karta przenosi na talię.</span><span class="sxs-lookup"><span data-stu-id="853f7-267">Magicians use the Faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="853f7-268">Teraz, gdy już wiesz, nie ryzykuj go dla innych osób!</span><span class="sxs-lookup"><span data-stu-id="853f7-268">Now that you know, don't spoil it for everyone else!</span></span>

<span data-ttu-id="853f7-269">Aby uzyskać więcej informacji na temat LINQ, zobacz:</span><span class="sxs-lookup"><span data-stu-id="853f7-269">For more information on LINQ, see:</span></span>

- [<span data-ttu-id="853f7-270">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="853f7-270">Language Integrated Query (LINQ)</span></span>](../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="853f7-271">Wprowadzenie do LINQ</span><span class="sxs-lookup"><span data-stu-id="853f7-271">Introduction to LINQ</span></span>](../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="853f7-272">Podstawowe operacje zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="853f7-272">Basic LINQ Query Operations (C#)</span></span>](../programming-guide/concepts/linq/basic-linq-query-operations.md)
- [<span data-ttu-id="853f7-273">Przekształcenia danych za pomocą LINQC#()</span><span class="sxs-lookup"><span data-stu-id="853f7-273">Data Transformations With LINQ (C#)</span></span>](../programming-guide/concepts/linq/data-transformations-with-linq.md)
- [<span data-ttu-id="853f7-274">Składnia zapytania i składni metody w LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="853f7-274">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
- [<span data-ttu-id="853f7-275">Funkcje C# obsługujące LINQ</span><span class="sxs-lookup"><span data-stu-id="853f7-275">C# Features That Support LINQ</span></span>](../programming-guide/concepts/linq/features-that-support-linq.md)
