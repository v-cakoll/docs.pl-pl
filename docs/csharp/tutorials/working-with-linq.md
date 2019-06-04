---
title: Praca z technologią LINQ
description: Ten samouczek omawia sposób generowania sekwencji za pomocą LINQ, pisanie metody używane w kwerendach LINQ i rozróżnienie między eager i leniwa ocena.
ms.date: 10/29/2018
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: e51fb166ccba793f9f2aa9d11a109280bf8eea93
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486988"
---
# <a name="working-with-linq"></a><span data-ttu-id="9c32b-103">Praca z technologią LINQ</span><span class="sxs-lookup"><span data-stu-id="9c32b-103">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="9c32b-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="9c32b-104">Introduction</span></span>

<span data-ttu-id="9c32b-105">W tym samouczku pokazano funkcje programu .NET Core i C# języka.</span><span class="sxs-lookup"><span data-stu-id="9c32b-105">This tutorial teaches you features in .NET Core and the C# language.</span></span> <span data-ttu-id="9c32b-106">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="9c32b-106">You’ll learn:</span></span>

- <span data-ttu-id="9c32b-107">Jak można wygenerować sekwencji za pomocą LINQ.</span><span class="sxs-lookup"><span data-stu-id="9c32b-107">How to generate sequences with LINQ.</span></span>
- <span data-ttu-id="9c32b-108">Jak napisać metody, które mogą być łatwo używane w kwerendach LINQ.</span><span class="sxs-lookup"><span data-stu-id="9c32b-108">How to write methods that can be easily used in LINQ queries.</span></span>
- <span data-ttu-id="9c32b-109">Jak rozróżnianie między eager i leniwa ocena.</span><span class="sxs-lookup"><span data-stu-id="9c32b-109">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="9c32b-110">Te techniki dowiesz się, tworząc aplikację, która przedstawia jedną z podstawowych umiejętności wszelkie magician: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="9c32b-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="9c32b-111">Krótko mówiąc faro shuffle jest techniką, gdzie możesz podzielić talii kart dokładnie w połowie, a następnie shuffle przeplatają każdego jedną kartę, z każda część odbudować oryginalnego slajdów.</span><span class="sxs-lookup"><span data-stu-id="9c32b-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="9c32b-112">Magicians Użyj tej techniki, ponieważ wszystkie karty w znanej lokalizacji po każdym losowa, a kolejność jest wzorzec powtarzające się.</span><span class="sxs-lookup"><span data-stu-id="9c32b-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span>

<span data-ttu-id="9c32b-113">Do własnych celów jest światła hearted przyjrzeć manipulowanie sekwencji danych.</span><span class="sxs-lookup"><span data-stu-id="9c32b-113">For your purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="9c32b-114">Aplikację, którą utworzysz konstruowania talii kart, a następnie wykonać sekwencję przesuwa, zapisywanie sekwencji zawsze wtedy.</span><span class="sxs-lookup"><span data-stu-id="9c32b-114">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="9c32b-115">Zostanie również porównać zaktualizowane kolejność oryginalnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="9c32b-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="9c32b-116">W tym samouczku składa się z wielu kroków.</span><span class="sxs-lookup"><span data-stu-id="9c32b-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="9c32b-117">Po każdym kroku możesz uruchomić aplikację i wyświetlić postęp.</span><span class="sxs-lookup"><span data-stu-id="9c32b-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="9c32b-118">Można również wyświetlić [ukończone przykładowe](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) w repozytorium dotnet/samples w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="9c32b-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="9c32b-119">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="9c32b-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9c32b-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9c32b-120">Prerequisites</span></span>

<span data-ttu-id="9c32b-121">Należy skonfigurować maszynę w taki sposób, aby uruchomić platformy .NET core.</span><span class="sxs-lookup"><span data-stu-id="9c32b-121">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="9c32b-122">Instrukcje dotyczące instalacji można znaleźć na [platformy .NET Core](https://www.microsoft.com/net/core) strony.</span><span class="sxs-lookup"><span data-stu-id="9c32b-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="9c32b-123">Mogą uruchamiać tę aplikację w systemie Windows, Ubuntu Linux, OS X lub w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="9c32b-123">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="9c32b-124">Musisz zainstalować wybrany edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="9c32b-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="9c32b-125">Opisy poniżej użycia [programu Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora.</span><span class="sxs-lookup"><span data-stu-id="9c32b-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="9c32b-126">Można jednak użyć dowolnego narzędzia potrafisz.</span><span class="sxs-lookup"><span data-stu-id="9c32b-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="9c32b-127">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="9c32b-127">Create the Application</span></span>

<span data-ttu-id="9c32b-128">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c32b-128">The first step is to create a new application.</span></span> <span data-ttu-id="9c32b-129">Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c32b-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="9c32b-130">Upewnij się, że sposób bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="9c32b-130">Make that the current directory.</span></span> <span data-ttu-id="9c32b-131">Wpisz polecenie `dotnet new console` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="9c32b-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="9c32b-132">Spowoduje to utworzenie plikach startowych dla podstawowych aplikacji "Hello World".</span><span class="sxs-lookup"><span data-stu-id="9c32b-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="9c32b-133">Jeśli nie znasz języka C#, [w tym samouczku](console-teleprompter.md) wyjaśnienie struktury programu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="9c32b-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="9c32b-134">Może odczytywać, który i następnie wróć tutaj, aby dowiedzieć się więcej na temat LINQ.</span><span class="sxs-lookup"><span data-stu-id="9c32b-134">You can read that and then return here to learn more about LINQ.</span></span>

## <a name="creating-the-data-set"></a><span data-ttu-id="9c32b-135">Tworzenie zestawu danych</span><span class="sxs-lookup"><span data-stu-id="9c32b-135">Creating the Data Set</span></span>

<span data-ttu-id="9c32b-136">Przed rozpoczęciem upewnij się, że następujące wiersze na początku `Program.cs` pliku wygenerowanego przez `dotnet new console`:</span><span class="sxs-lookup"><span data-stu-id="9c32b-136">Before you begin, make sure that the following lines are at the top of the `Program.cs` file generated by `dotnet new console`:</span></span>

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="9c32b-137">Jeśli te trzy wiersze (`using` instrukcji) nie są w górnej części pliku nasz program nie zostanie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="9c32b-137">If these three lines (`using` statements) aren't at the top of the file, our program will not compile.</span></span>

<span data-ttu-id="9c32b-138">Teraz, gdy wszystkie odwołania, które należy rozważyć, co stanowi talii kart.</span><span class="sxs-lookup"><span data-stu-id="9c32b-138">Now that you have all of the references that you'll need, consider what constitutes a deck of cards.</span></span> <span data-ttu-id="9c32b-139">Często talii kart gry zawiera cztery kolory, a każdy sposób ma trzynaście wartości.</span><span class="sxs-lookup"><span data-stu-id="9c32b-139">Commonly, a deck of playing cards has four suits, and each suit has thirteen values.</span></span> <span data-ttu-id="9c32b-140">Normalnie, należy rozważyć utworzenie `Card` klasy bezpośrednio off bat i wypełnianie zbiór `Card` obiekty ręcznie.</span><span class="sxs-lookup"><span data-stu-id="9c32b-140">Normally, you might consider creating a `Card` class right off the bat and populating a collection of `Card` objects by hand.</span></span> <span data-ttu-id="9c32b-141">Za pomocą LINQ może być bardziej zwięzłe niż zwykły sposób radzenia sobie z tworzeniem talii kart.</span><span class="sxs-lookup"><span data-stu-id="9c32b-141">With LINQ, you can be more concise than the usual way of dealing with creating a deck of cards.</span></span> <span data-ttu-id="9c32b-142">Zamiast tworzyć `Card` klasy, można utworzyć dwie sekwencje do reprezentowania kolory i rangi texeli, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="9c32b-142">Instead of creating a `Card` class, you can create two sequences to represent suits and ranks, respectively.</span></span> <span data-ttu-id="9c32b-143">Utworzysz naprawdę proste parę [ *metody iteracyjne* ](../iterators.md#enumeration-sources-with-iterator-methods) wygeneruje rangę i kolory jako <xref:System.Collections.Generic.IEnumerable%601>s ciągów:</span><span class="sxs-lookup"><span data-stu-id="9c32b-143">You'll create a really simple pair of [*iterator methods*](../iterators.md#enumeration-sources-with-iterator-methods) that will generate the ranks and suits as <xref:System.Collections.Generic.IEnumerable%601>s of strings:</span></span>

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

<span data-ttu-id="9c32b-144">Umieść je poniżej `Main` method in Class metoda swoje `Program.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="9c32b-144">Place these underneath the `Main` method in your `Program.cs` file.</span></span> <span data-ttu-id="9c32b-145">Korzystanie z tych dwóch metod zarówno `yield return` składni, aby utworzyć sekwencję podczas ich działania.</span><span class="sxs-lookup"><span data-stu-id="9c32b-145">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="9c32b-146">Kompilator tworzy obiekt, który implementuje <xref:System.Collections.Generic.IEnumerable%601> i generuje sekwencję ciągów, ponieważ są one wymagane.</span><span class="sxs-lookup"><span data-stu-id="9c32b-146">The compiler builds an object that implements <xref:System.Collections.Generic.IEnumerable%601> and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="9c32b-147">Teraz Użyj te metody iteratora, aby utworzyć zbiór kart.</span><span class="sxs-lookup"><span data-stu-id="9c32b-147">Now, use these iterator methods to create the deck of cards.</span></span> <span data-ttu-id="9c32b-148">Będzie umieścić zapytania LINQ w naszym `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="9c32b-148">You'll place the LINQ query in our `Main` method.</span></span> <span data-ttu-id="9c32b-149">Poniżej znajduje się ona:</span><span class="sxs-lookup"><span data-stu-id="9c32b-149">Here's a look at it:</span></span>

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

<span data-ttu-id="9c32b-150">Wielokrotność `from` generuje klauzule <xref:System.Linq.Enumerable.SelectMany%2A>, co powoduje utworzenie pojedynczego ciągu z łączenia każdego elementu w pierwszej kolejności, przy czym każdy element w drugiej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9c32b-150">The multiple `from` clauses produce a <xref:System.Linq.Enumerable.SelectMany%2A>, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="9c32b-151">Kolejność jest ważna dla naszych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="9c32b-151">The order is important for our purposes.</span></span> <span data-ttu-id="9c32b-152">Pierwszy element w pierwszej sekwencji źródłowej (kolory) w połączeniu z każdego elementu w drugiej sekwencji (Klasyfikacja).</span><span class="sxs-lookup"><span data-stu-id="9c32b-152">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Ranks).</span></span> <span data-ttu-id="9c32b-153">To zapewnia wszystkie karty trzynaście pierwszy koloru.</span><span class="sxs-lookup"><span data-stu-id="9c32b-153">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="9c32b-154">Ten proces jest powtarzany, przy czym każdy element w pierwszej kolejności (kolory).</span><span class="sxs-lookup"><span data-stu-id="9c32b-154">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="9c32b-155">Wynik końcowy jest talii kart uporządkowane według kolory, a następnie według wartości.</span><span class="sxs-lookup"><span data-stu-id="9c32b-155">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="9c32b-156">Ważne jest, aby pamiętać, że możliwość zapisu LINQ w składni zapytań powyżej czy należy użyć składni metody zamiast tego, zawsze jest możliwe przejść z jednej formy składnia do innego.</span><span class="sxs-lookup"><span data-stu-id="9c32b-156">It's important to keep in mind that whether you choose to write your LINQ in the query syntax used above or use method syntax instead, it's always possible to go from one form of syntax to the other.</span></span> <span data-ttu-id="9c32b-157">Zapytanie powyżej napisanych w składni zapytania mogą być napisane w składni metody jako:</span><span class="sxs-lookup"><span data-stu-id="9c32b-157">The above query written in query syntax can be written in method syntax as:</span></span>

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

<span data-ttu-id="9c32b-158">Kompilator tłumaczy instrukcji LINQ, zapisane ze składnią kwerendy w składni wywołania metody równoważne.</span><span class="sxs-lookup"><span data-stu-id="9c32b-158">The compiler translates LINQ statements written with query syntax into the equivalent method call syntax.</span></span> <span data-ttu-id="9c32b-159">W związku z tym niezależnie od wybranego składni, dwie wersje zapytanie generuje ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="9c32b-159">Therefore, regardless of your syntax choice, the two versions of the query produce the same result.</span></span> <span data-ttu-id="9c32b-160">Wybierz, które składni działa najlepiej w danej sytuacji: na przykład, jeśli pracujesz w zespole, w których niektóre elementy członkowskie mają trudności przy użyciu składni metody, spróbuj preferowanie za pomocą składni zapytania.</span><span class="sxs-lookup"><span data-stu-id="9c32b-160">Choose which syntax works best for your situation: for instance, if you're working in a team where some of the members have difficulty with method syntax, try to prefer using query syntax.</span></span>

<span data-ttu-id="9c32b-161">Przejdź dalej i uruchom aplikację przykładową na tym etapie konstruowania.</span><span class="sxs-lookup"><span data-stu-id="9c32b-161">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="9c32b-162">Wszystkie karty 52 będzie wyświetlany w talii kart.</span><span class="sxs-lookup"><span data-stu-id="9c32b-162">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="9c32b-163">Może okazać się bardzo pomocne uruchomić ten przykład w debugerze, aby obserwować sposób, w jaki `Suits()` i `Ranks()` wykonywania metody.</span><span class="sxs-lookup"><span data-stu-id="9c32b-163">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Ranks()` methods execute.</span></span> <span data-ttu-id="9c32b-164">Wyraźnie widać, że każdego ciągu w każdej sekwencji jest generowany tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="9c32b-164">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Wyświetlanie aplikacji wypisywanie 52 kart okna konsoli.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="9c32b-166">Manipulowanie kolejności</span><span class="sxs-lookup"><span data-stu-id="9c32b-166">Manipulating the Order</span></span>

<span data-ttu-id="9c32b-167">Następnie skoncentrować się na sposób ma zostać losowo zmieniona kolejność kart w talii.</span><span class="sxs-lookup"><span data-stu-id="9c32b-167">Next, focus on how you're going to shuffle the cards in the deck.</span></span> <span data-ttu-id="9c32b-168">Pierwszym krokiem w dowolnej dobre shuffle jest podzielenie slajdów w dwóch.</span><span class="sxs-lookup"><span data-stu-id="9c32b-168">The first step in any good shuffle is to split the deck in two.</span></span> <span data-ttu-id="9c32b-169"><xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> metody, które są częścią interfejsów API LINQ zapewnia tę funkcję dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="9c32b-169">The <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods that are part of the LINQ APIs provide that feature for you.</span></span> <span data-ttu-id="9c32b-170">Umieść je poniżej `foreach` Pętla:</span><span class="sxs-lookup"><span data-stu-id="9c32b-170">Place them underneath the `foreach` loop:</span></span>

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

<span data-ttu-id="9c32b-171">Jednakże nie istnieje metoda shuffle z zalet w standardowej bibliotece, dzięki czemu będzie trzeba napisać własny.</span><span class="sxs-lookup"><span data-stu-id="9c32b-171">However, there's no shuffle method to take advantage of in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="9c32b-172">Metoda losowa, który zostanie utworzony przedstawiono kilka technik, które ma być używany do programów opartych na LINQ, dzięki czemu każda część tego procesu zostaną wyjaśnione w krokach.</span><span class="sxs-lookup"><span data-stu-id="9c32b-172">The shuffle method you'll be creating illustrates several techniques that you'll use with LINQ-based programs, so each part of this process will be explained in steps.</span></span>

<span data-ttu-id="9c32b-173">Aby dodać funkcjonalność do interakcji z <xref:System.Collections.Generic.IEnumerable%601> wrócisz z zapytań LINQ, musisz zapisać niektórych specjalnymi rodzajami metody o nazwie [metody rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9c32b-173">In order to add some functionality to how you interact with the <xref:System.Collections.Generic.IEnumerable%601> you'll get back from LINQ queries, you'll need to write some special kinds of methods called [extension methods](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="9c32b-174">Krótko mówiąc, metody rozszerzenia jest specjalnego przeznaczenia *statycznej metody* , dodaje nowe funkcje do już istniejącego typu bez konieczności modyfikowania oryginalnego typu, aby dodać funkcje.</span><span class="sxs-lookup"><span data-stu-id="9c32b-174">Briefly, an extension method is a special purpose *static method* that adds new functionality to an already-existing type without having to modify the original type you want to add functionality to.</span></span>

<span data-ttu-id="9c32b-175">Nadaj nową stronę główną Twoje rozszerzenia metody, dodając nową *statyczne* plik klasy do programu o nazwie `Extensions.cs`, a następnie uruchom kompilowania z pierwszą metodą rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="9c32b-175">Give your extension methods a new home by adding a new *static* class file to your program called `Extensions.cs`, and then start building out the first extension method:</span></span>

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

<span data-ttu-id="9c32b-176">Wyszukaj w podpisie metody moment, w szczególności parametry:</span><span class="sxs-lookup"><span data-stu-id="9c32b-176">Look at the method signature for a moment, specifically the parameters:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="9c32b-177">Możesz zobaczyć dodanie `this` modyfikator na pierwszy argument do metody.</span><span class="sxs-lookup"><span data-stu-id="9c32b-177">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="9c32b-178">Oznacza to, że należy wywołać metodę, tak jakby był metodą elementu członkowskiego typu pierwszego argumentu.</span><span class="sxs-lookup"><span data-stu-id="9c32b-178">That means you call the method as though it were a member method of the type of the first argument.</span></span> <span data-ttu-id="9c32b-179">Tej deklaracji metody również następujące standardowe idiom gdzie typy wejściowe i wyjściowe są `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="9c32b-179">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="9c32b-180">Czy rozwiązanie umożliwia metody LINQ zezwalającym ze sobą, aby wykonywać bardziej złożone zapytania.</span><span class="sxs-lookup"><span data-stu-id="9c32b-180">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

<span data-ttu-id="9c32b-181">Naturalnie ponieważ talii podzielić połowami, należy dołączyć te połowami ze sobą.</span><span class="sxs-lookup"><span data-stu-id="9c32b-181">Naturally, since you split the deck into halves, you'll need to join those halves together.</span></span> <span data-ttu-id="9c32b-182">W kodzie, oznacza to, użytkownik będzie można wyliczanie zarówno sekwencji zakupione w ramach <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> jednocześnie, *`interleaving`* elementy i tworzenia jednej sekwencji: Twoje przekazanych teraz talii kart.</span><span class="sxs-lookup"><span data-stu-id="9c32b-182">In code, this means you'll be enumerating both of the sequences you acquired through <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> at once, *`interleaving`* the elements, and creating one sequence: your now-shuffled deck of cards.</span></span> <span data-ttu-id="9c32b-183">Zapisywanie LINQ metodę, która współdziała z dwóch sekwencji wymaga zrozumienia sposobu <xref:System.Collections.Generic.IEnumerable%601> działa.</span><span class="sxs-lookup"><span data-stu-id="9c32b-183">Writing a LINQ method that works with two sequences requires that you understand how <xref:System.Collections.Generic.IEnumerable%601> works.</span></span>

<span data-ttu-id="9c32b-184"><xref:System.Collections.Generic.IEnumerable%601> Interfejs ma jedną z metod: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c32b-184">The <xref:System.Collections.Generic.IEnumerable%601> interface has one method: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span></span> <span data-ttu-id="9c32b-185">Obiekt zwrócony przez <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> ma metodę, aby przejść do następnego elementu i właściwości, która pobiera bieżącego elementu w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9c32b-185">The object returned by <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="9c32b-186">Te dwa elementy członkowskie użyje do wyliczania kolekcji i zwracają elementy.</span><span class="sxs-lookup"><span data-stu-id="9c32b-186">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="9c32b-187">Ta metoda przeplotu będzie metody iteratora, więc zamiast tworzenia kolekcji i zwraca kolekcję, użyjesz `yield return` składni pokazanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="9c32b-187">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span>

<span data-ttu-id="9c32b-188">Oto implementacja tej metody:</span><span class="sxs-lookup"><span data-stu-id="9c32b-188">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="9c32b-189">Teraz, gdy ta metoda jest napisanych, wróć do `Main` metody i shuffle slajdów, gdy:</span><span class="sxs-lookup"><span data-stu-id="9c32b-189">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

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

## <a name="comparisons"></a><span data-ttu-id="9c32b-190">Porównania</span><span class="sxs-lookup"><span data-stu-id="9c32b-190">Comparisons</span></span>

<span data-ttu-id="9c32b-191">Przesuwa ile zajmuje można ustawić na pokład z powrotem do jego oryginalnej kolejności?</span><span class="sxs-lookup"><span data-stu-id="9c32b-191">How many shuffles it takes to set the deck back to its original order?</span></span> <span data-ttu-id="9c32b-192">Aby dowiedzieć się, będzie konieczne napisanie metody, która określa, czy dwie sekwencje mają taki sam.</span><span class="sxs-lookup"><span data-stu-id="9c32b-192">To find out, you'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="9c32b-193">Po utworzeniu tej metody, należy umieścić kod, który rozmieszcza slajdów w pętli i sprawdź, gdy jest użyta w kolejności.</span><span class="sxs-lookup"><span data-stu-id="9c32b-193">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="9c32b-194">Zapisywanie metodę, aby określić, czy dwie sekwencje są równe powinno być proste.</span><span class="sxs-lookup"><span data-stu-id="9c32b-194">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="9c32b-195">Jest podobną strukturę z metodą, którą zapisano mieszania slajdów.</span><span class="sxs-lookup"><span data-stu-id="9c32b-195">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="9c32b-196">Tylko to czas, zamiast `yield return`ing każdego elementu, będzie można porównać zgodnych elementów w każdej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9c32b-196">Only this time, instead of `yield return`ing each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="9c32b-197">Sekwencje całą sekwencję zostać wyliczone, jeśli pasuje do każdego elementu, są takie same:</span><span class="sxs-lookup"><span data-stu-id="9c32b-197">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="9c32b-198">Spowoduje to pokazanie drugi idiom LINQ: metody terminala.</span><span class="sxs-lookup"><span data-stu-id="9c32b-198">This shows a second LINQ idiom: terminal methods.</span></span> <span data-ttu-id="9c32b-199">Wykonaj sekwencję jako dane wejściowe (lub w tym przypadku dwie sekwencje) i zwraca pojedynczą wartość skalarną.</span><span class="sxs-lookup"><span data-stu-id="9c32b-199">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="9c32b-200">Korzystając z metody terminala, są one zawsze końcowe metody w łańcuchu metody LINQ, dlatego nazwa zapytania "terminalu".</span><span class="sxs-lookup"><span data-stu-id="9c32b-200">When using terminal methods, they are always the final method in a chain of methods for a LINQ query, hence the name "terminal".</span></span>

<span data-ttu-id="9c32b-201">Można to zobaczyć w działaniu używanej do określania, kiedy talii jest w jego oryginalnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="9c32b-201">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="9c32b-202">Umieść kod shuffle wewnątrz pętli, a następnie Zatrzymaj, gdy sekwencja jest ponownie w jego oryginalnej kolejności, stosując `SequenceEquals()` metody.</span><span class="sxs-lookup"><span data-stu-id="9c32b-202">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="9c32b-203">Widać, że zawsze będzie ostatnią metodę w każdym zapytaniu, ponieważ zwraca pojedynczą wartość zamiast sekwencji:</span><span class="sxs-lookup"><span data-stu-id="9c32b-203">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

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

<span data-ttu-id="9c32b-204">Uruchom kod coś do tej pory i zwróć uwagę na sposób talii zmienia się na każdym shuffle.</span><span class="sxs-lookup"><span data-stu-id="9c32b-204">Run the code you've got so far and take note of how the deck rearranges on each shuffle.</span></span> <span data-ttu-id="9c32b-205">Po 8 przesuwa (iteracji nie-pętli while), talii powraca do oryginalnej konfiguracji została, podczas pierwszego utworzenia początkowego zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="9c32b-205">After 8 shuffles (iterations of the do-while loop), the deck returns to the original configuration it was in when you first created it from the starting LINQ query.</span></span>

## <a name="optimizations"></a><span data-ttu-id="9c32b-206">Optymalizacje</span><span class="sxs-lookup"><span data-stu-id="9c32b-206">Optimizations</span></span>

<span data-ttu-id="9c32b-207">Wykonuje przykładowe dołączeniu do tej pory *się shuffle*, gdzie kart górny i dolny pozostają takie same, przy każdym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="9c32b-207">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="9c32b-208">Upewnijmy się, co zmiany: użyjemy *w losowo* zamiast tego, gdzie wszystkie karty 52 zmiana położenia.</span><span class="sxs-lookup"><span data-stu-id="9c32b-208">Let's make one change: we'll use an *in shuffle* instead, where all 52 cards change position.</span></span> <span data-ttu-id="9c32b-209">Dla w losowo możesz przeplot slajdów, aby pierwszy karty w dolnej połowie staje się pierwszej karty w talii kart.</span><span class="sxs-lookup"><span data-stu-id="9c32b-209">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="9c32b-210">Oznacza to, że ostatnią kartę w górnej połowie staje się karta dolnej.</span><span class="sxs-lookup"><span data-stu-id="9c32b-210">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="9c32b-211">Jest to prostą zmianę pojedynczej linii kodu.</span><span class="sxs-lookup"><span data-stu-id="9c32b-211">This is a simple change to a singular line of code.</span></span> <span data-ttu-id="9c32b-212">Aktualizacja bieżącego zapytania losowa, przełączając położenie <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c32b-212">Update the current shuffle query by switching the positions of <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span> <span data-ttu-id="9c32b-213">Spowoduje to zmianę kolejności górnej i dolnej części talii:</span><span class="sxs-lookup"><span data-stu-id="9c32b-213">This will change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="9c32b-214">Ponownie uruchom program, a zobaczysz, że zajmuje 52 iteracji dla slajdów zmienić kolejność sam.</span><span class="sxs-lookup"><span data-stu-id="9c32b-214">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="9c32b-215">Będzie również uruchomić, należy zwrócić uwagę spadku wydajności niektórych obniżyć wydajność, ponieważ program kontynuuje działanie.</span><span class="sxs-lookup"><span data-stu-id="9c32b-215">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="9c32b-216">Istnieje kilka przyczyn.</span><span class="sxs-lookup"><span data-stu-id="9c32b-216">There are a number of reasons for this.</span></span> <span data-ttu-id="9c32b-217">Rozwiązano problem z jednym z głównych powodów tego spadku wydajności: nieefektywne użycie [ *obliczanie leniwe*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9c32b-217">You can tackle one of the major causes of this performance drop: inefficient use of [*lazy evaluation*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="9c32b-218">Krótko mówiąc obliczanie leniwe stanów obliczania instrukcji nie jest wykonywana do czasu jej wartość jest potrzebna.</span><span class="sxs-lookup"><span data-stu-id="9c32b-218">Briefly, lazy evaluation states that the evaluation of a statement is not performed until its value is needed.</span></span> <span data-ttu-id="9c32b-219">Zapytania LINQ są instrukcje, które są oceniane opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="9c32b-219">LINQ queries are statements that are evaluated lazily.</span></span> <span data-ttu-id="9c32b-220">Sekwencji są generowane tylko wtedy, gdy elementy są wymagane.</span><span class="sxs-lookup"><span data-stu-id="9c32b-220">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="9c32b-221">Zazwyczaj, który jest główną zaletą LINQ.</span><span class="sxs-lookup"><span data-stu-id="9c32b-221">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="9c32b-222">Jednak użycie takich jak ten program, powoduje to wykładniczy wzrost w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9c32b-222">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="9c32b-223">Należy pamiętać, firma Microsoft wygenerowania oryginalnego slajdów, za pomocą zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="9c32b-223">Remember that we generated the original deck using a LINQ query.</span></span> <span data-ttu-id="9c32b-224">Każdy losowa jest generowany, wykonując trzy zapytań LINQ w poprzednim slajdów.</span><span class="sxs-lookup"><span data-stu-id="9c32b-224">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="9c32b-225">Wszystkie te są wykonywane opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="9c32b-225">All these are performed lazily.</span></span> <span data-ttu-id="9c32b-226">Oznacza to również, że te procedury są wykonywane ponownie każdorazowo, gdy wymagane są sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9c32b-226">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="9c32b-227">Przez razem, gdy można uzyskać dostęp do 52nd iteracji możesz teraz trwa ponowne generowanie oryginalnego slajdów many, wiele razy.</span><span class="sxs-lookup"><span data-stu-id="9c32b-227">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="9c32b-228">Napiszmy dziennika, aby zademonstrować to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="9c32b-228">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="9c32b-229">Następnie możesz go ma naprawić.</span><span class="sxs-lookup"><span data-stu-id="9c32b-229">Then, you'll fix it.</span></span>

<span data-ttu-id="9c32b-230">W swojej `Extensions.cs` pliku, wpisz lub skopiuj poniższe metody.</span><span class="sxs-lookup"><span data-stu-id="9c32b-230">In your `Extensions.cs` file, type in or copy the method below.</span></span> <span data-ttu-id="9c32b-231">Ta metoda rozszerzenia tworzy nowy plik o nazwie `debug.log` w ramach katalogu projektu i rejestruje zapytania, które obecnie jest wykonywana w pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="9c32b-231">This extension method creates a new file called `debug.log` within your project directory and records what query is currently being executed to the log file.</span></span> <span data-ttu-id="9c32b-232">Ta metoda rozszerzenia można dołączyć do dowolnego zapytania, aby oznaczyć, że zapytanie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="9c32b-232">This extension method can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="9c32b-233">Następnie przygotuj Instrumentację definicję każdego zapytania za pomocą komunikatu dziennika:</span><span class="sxs-lookup"><span data-stu-id="9c32b-233">Next, instrument the definition of each query with a log message:</span></span>

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

<span data-ttu-id="9c32b-234">Należy zauważyć, że nie logujesz się za każdym razem, gdy możesz uzyskać dostęp do kwerendy.</span><span class="sxs-lookup"><span data-stu-id="9c32b-234">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="9c32b-235">Zaloguj się tylko wtedy, gdy tworzysz oryginalnego zapytania.</span><span class="sxs-lookup"><span data-stu-id="9c32b-235">You log only when you create the original query.</span></span> <span data-ttu-id="9c32b-236">Program nadal zajmuje dużo czasu do uruchomienia, ale spowoduje to wyświetlenie dlaczego.</span><span class="sxs-lookup"><span data-stu-id="9c32b-236">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="9c32b-237">Gdy wyczerpią się z rejestrowania włączony, przełącznik shuffle poza systemem shuffle w cierpliwość.</span><span class="sxs-lookup"><span data-stu-id="9c32b-237">If you run out of patience running the in shuffle with logging turned on, switch back to the out shuffle.</span></span> <span data-ttu-id="9c32b-238">Nadal zobaczysz efekty obliczanie z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="9c32b-238">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="9c32b-239">W jednym przebiegu wykonuje kwerendy 2592, w tym wszystkich wartości i sposób generowania.</span><span class="sxs-lookup"><span data-stu-id="9c32b-239">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="9c32b-240">Można zwiększyć wydajność kod do zmniejszenia liczby wykonań, które wprowadzasz w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="9c32b-240">You can improve the performance of the code here to reduce the number of executions you make.</span></span> <span data-ttu-id="9c32b-241">Proste rozwiązanie, możesz wprowadzić polega na *pamięci podręcznej* wyniki oryginalnego zapytania LINQ, który konstruuje talii kart.</span><span class="sxs-lookup"><span data-stu-id="9c32b-241">A simple fix you can make is to *cache* the results of the original LINQ query that constructs the deck of cards.</span></span> <span data-ttu-id="9c32b-242">Obecnie wykonujesz zapytania ponownie i ponownie każdym razem, gdy nie — gdy pętla przechodzi przez iteracji, ponownie tworząc talii kart i losowego jego grupowania na każdym.</span><span class="sxs-lookup"><span data-stu-id="9c32b-242">Currently, you're executing the queries again and again every time the do-while loop goes through an iteration, re-constructing the deck of cards and reshuffling it every time.</span></span> <span data-ttu-id="9c32b-243">W pamięci podręcznej talii kart, można korzystać z metody LINQ <xref:System.Linq.Enumerable.ToArray%2A> i <xref:System.Linq.Enumerable.ToList%2A>; gdy Dołącz je do zapytania, będzie wykonują te same akcje Informujesz im, ale teraz będzie przechowują wyniki w tablicy lub listy, w zależności od tego, w jakiej metody Możesz wybrać do wywołania.</span><span class="sxs-lookup"><span data-stu-id="9c32b-243">To cache the deck of cards, you can leverage the LINQ methods <xref:System.Linq.Enumerable.ToArray%2A> and <xref:System.Linq.Enumerable.ToList%2A>; when you append them to the queries, they'll perform the same actions you've told them to, but now they'll store the results in an array or a list, depending on which method you choose to call.</span></span> <span data-ttu-id="9c32b-244">Append — metoda LINQ <xref:System.Linq.Enumerable.ToArray%2A> do zapytania i ponownie uruchom program:</span><span class="sxs-lookup"><span data-stu-id="9c32b-244">Append the LINQ method <xref:System.Linq.Enumerable.ToArray%2A> to both queries and run the program again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="9c32b-245">Poza losowa jest teraz do 30 zapytania.</span><span class="sxs-lookup"><span data-stu-id="9c32b-245">Now the out shuffle is down to 30 queries.</span></span> <span data-ttu-id="9c32b-246">Ponownie uruchom za pomocą w losowo i zostaną wyświetlone podobne ulepszenia: teraz wykonuje 162 zapytania.</span><span class="sxs-lookup"><span data-stu-id="9c32b-246">Run again with the in shuffle and you'll see similar improvements: it now executes 162 queries.</span></span>

<span data-ttu-id="9c32b-247">Należy pamiętać, że w tym przykładzie jest **zaprojektowane** do wyróżnienia przypadki użycia, w którym leniwa ocena może spowodować problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="9c32b-247">Please note that this example is **designed** to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="9c32b-248">Chociaż jest to ważne zobaczyć, gdzie leniwa ocena może wpłynąć na wydajność kodu jest równie ważne dowiedzieć się, że nie wszystkie kwerendy należy uruchamiać eagerly.</span><span class="sxs-lookup"><span data-stu-id="9c32b-248">While it's important to see where lazy evaluation can impact code performance, it's equally important to understand that not all queries should run eagerly.</span></span> <span data-ttu-id="9c32b-249">Wydajności trafień, możesz pociągnąć za sobą bez użycia <xref:System.Linq.Enumerable.ToArray%2A> jest, ponieważ każdy nowy układ talii kart składa się z poprzednich rozmieszczenia.</span><span class="sxs-lookup"><span data-stu-id="9c32b-249">The performance hit you incur without using <xref:System.Linq.Enumerable.ToArray%2A> is because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="9c32b-250">Przy użyciu leniwa ocena oznacza, że każda nowa konfiguracja slajdów składa się z oryginalnego slajdów, nawet wykonywania kodu, który skompilowany `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="9c32b-250">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="9c32b-251">Dzięki któremu dużą ilość dodatkowej pracy.</span><span class="sxs-lookup"><span data-stu-id="9c32b-251">That causes a large amount of extra work.</span></span>

<span data-ttu-id="9c32b-252">W praktyce niektóre algorytmy uruchamiania, również przy użyciu eager oceny, a pozostałe, również korzystając z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="9c32b-252">In practice, some algorithms run well using eager evaluation, and others run well using lazy evaluation.</span></span> <span data-ttu-id="9c32b-253">Dzienne użycie opóźnieniem zwykle jest lepszym rozwiązaniem, gdy źródło danych jest oddzielnym procesie, takich jak aparat bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9c32b-253">For daily usage, lazy evaluation is usually a better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="9c32b-254">W przypadku baz danych z opóźnieniem pozwala bardziej złożone zapytania, które można wykonać tylko jeden obiegu do procesu bazy danych i z powrotem do pozostałej części kodu.</span><span class="sxs-lookup"><span data-stu-id="9c32b-254">For databases, lazy evaluation allows more complex queries to execute only one round trip to the database process and back to the rest of your code.</span></span> <span data-ttu-id="9c32b-255">LINQ jest elastyczny, czy chcesz korzystać z opóźnieniem lub eager oceny, więc mierzenia procesów i wybrać, niezależnie od rodzaju oceny zapewnia najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="9c32b-255">LINQ is flexible whether you choose to utilize lazy or eager evaluation, so measure your processes and pick whichever kind of evaluation gives you the best performance.</span></span>

## <a name="conclusion"></a><span data-ttu-id="9c32b-256">Wniosek</span><span class="sxs-lookup"><span data-stu-id="9c32b-256">Conclusion</span></span>

<span data-ttu-id="9c32b-257">W tym projekcie omówione są:</span><span class="sxs-lookup"><span data-stu-id="9c32b-257">In this project, you covered:</span></span>
- <span data-ttu-id="9c32b-258">do istotnych sekwencji za pomocą zapytań LINQ do agregowania danych</span><span class="sxs-lookup"><span data-stu-id="9c32b-258">using LINQ queries to aggregate data into a meaningful sequence</span></span>
- <span data-ttu-id="9c32b-259">Zapisywanie metody rozszerzenia umożliwiające dodawanie własnych niestandardowych funkcji do zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="9c32b-259">writing Extension methods to add our own custom functionality to LINQ queries</span></span>
- <span data-ttu-id="9c32b-260">Znajdowanie obszarów w naszym kodzie, w którym nasze zapytań LINQ napotkać problemy z wydajnością, takie jak uszkodzenie szybkości</span><span class="sxs-lookup"><span data-stu-id="9c32b-260">locating areas in our code where our LINQ queries might run into performance issues like degraded speed</span></span>
- <span data-ttu-id="9c32b-261">Obliczanie z opóźnieniem i chętnie Zapoznamy w odniesieniu do zapytań LINQ oraz skutków tego procesu, mogą pojawić się na wydajności zapytań</span><span class="sxs-lookup"><span data-stu-id="9c32b-261">lazy and eager evaluation in regards to LINQ queries and the implications they might have on query performance</span></span>

<span data-ttu-id="9c32b-262">Oprócz LINQ przedstawiono nieco dotyczących używania magicians techniki, aby uzyskać wskazówki karty.</span><span class="sxs-lookup"><span data-stu-id="9c32b-262">Aside from LINQ, you learned a bit about a technique magicians use for card tricks.</span></span> <span data-ttu-id="9c32b-263">Magicians Użyj Faro shuffle, ponieważ może kontrolować, gdzie wszystkie karty przemieszcza się w talii kart.</span><span class="sxs-lookup"><span data-stu-id="9c32b-263">Magicians use the Faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="9c32b-264">Teraz gdy wiesz, nie zepsucia go wszystkim innym użytkownikom!</span><span class="sxs-lookup"><span data-stu-id="9c32b-264">Now that you know, don't spoil it for everyone else!</span></span>

<span data-ttu-id="9c32b-265">Aby uzyskać więcej informacji na temat LINQ zobacz:</span><span class="sxs-lookup"><span data-stu-id="9c32b-265">For more information on LINQ, see:</span></span>
- [<span data-ttu-id="9c32b-266">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="9c32b-266">Language Integrated Query (LINQ)</span></span>](../programming-guide/concepts/linq/index.md)
  - [<span data-ttu-id="9c32b-267">Wprowadzenie do LINQ</span><span class="sxs-lookup"><span data-stu-id="9c32b-267">Introduction to LINQ</span></span>](../programming-guide/concepts/linq/index.md)
  - [<span data-ttu-id="9c32b-268">Podstawowe operacje zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="9c32b-268">Basic LINQ Query Operations (C#)</span></span>](../programming-guide/concepts/linq/basic-linq-query-operations.md)
  - [<span data-ttu-id="9c32b-269">Przekształcanie danych za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="9c32b-269">Data Transformations With LINQ (C#)</span></span>](../programming-guide/concepts/linq/data-transformations-with-linq.md)
  - [<span data-ttu-id="9c32b-270">Składnia zapytania i metody w technologii LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="9c32b-270">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
  - [<span data-ttu-id="9c32b-271">Funkcje C# obsługujące LINQ</span><span class="sxs-lookup"><span data-stu-id="9c32b-271">C# Features That Support LINQ</span></span>](../programming-guide/concepts/linq/features-that-support-linq.md)
    