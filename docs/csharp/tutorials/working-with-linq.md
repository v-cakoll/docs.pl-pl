---
title: Praca z technologią LINQ
description: Ten samouczek omawia sposób generowania sekwencji za pomocą LINQ, pisanie metody używane w kwerendach LINQ i rozróżnienie między eager i leniwa ocena.
ms.date: 10/29/2018
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: e37c013add02f651875db7b908ae2b49711d996d
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609305"
---
# <a name="working-with-linq"></a>Praca z technologią LINQ

## <a name="introduction"></a>Wprowadzenie

W tym samouczku pokazano funkcje programu .NET Core i C# języka. Dowiesz się:

- Jak można wygenerować sekwencji za pomocą LINQ.
- Jak napisać metody, które mogą być łatwo używane w kwerendach LINQ.
- Jak rozróżnianie między eager i leniwa ocena.

Te techniki dowiesz się, tworząc aplikację, która przedstawia jedną z podstawowych umiejętności wszelkie magician: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle). Krótko mówiąc faro shuffle jest techniką, gdzie możesz podzielić talii kart dokładnie w połowie, a następnie shuffle przeplatają każdego jedną kartę, z każda część odbudować oryginalnego slajdów.

Magicians Użyj tej techniki, ponieważ wszystkie karty w znanej lokalizacji po każdym losowa, a kolejność jest wzorzec powtarzające się.

Do własnych celów jest światła hearted przyjrzeć manipulowanie sekwencji danych. Aplikację, którą utworzysz konstruowania talii kart, a następnie wykonać sekwencję przesuwa, zapisywanie sekwencji zawsze wtedy. Zostanie również porównać zaktualizowane kolejność oryginalnej kolejności.

W tym samouczku składa się z wielu kroków. Po każdym kroku możesz uruchomić aplikację i wyświetlić postęp. Można również wyświetlić [ukończone przykładowe](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) w repozytorium dotnet/samples w witrynie GitHub. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Wymagania wstępne

Należy skonfigurować maszynę w taki sposób, aby uruchomić platformy .NET core. Instrukcje dotyczące instalacji można znaleźć na [platformy .NET Core](https://www.microsoft.com/net/core) strony. Mogą uruchamiać tę aplikację w systemie Windows, Ubuntu Linux, OS X lub w kontenerze platformy Docker. Musisz zainstalować wybrany edytor kodu. Opisy poniżej użycia [programu Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora. Można jednak użyć dowolnego narzędzia potrafisz.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji. Upewnij się, że sposób bieżącego katalogu. Wpisz polecenie `dotnet new console` w wierszu polecenia. Spowoduje to utworzenie plikach startowych dla podstawowych aplikacji "Hello World".

Jeśli nie znasz języka C#, [w tym samouczku](console-teleprompter.md) wyjaśnienie struktury programu w języku C#. Może odczytywać, który i następnie wróć tutaj, aby dowiedzieć się więcej na temat LINQ.

## <a name="creating-the-data-set"></a>Tworzenie zestawu danych

Przed rozpoczęciem upewnij się, że następujące wiersze na początku `Program.cs` pliku wygenerowanego przez `dotnet new console`:

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

Jeśli te trzy wiersze (`using` instrukcji) nie są w górnej części pliku nasz program nie zostanie skompilowany.

Teraz, gdy wszystkie odwołania, które należy rozważyć, co stanowi talii kart. Często talii kart gry zawiera cztery kolory, a każdy sposób ma trzynaście wartości. Normalnie, należy rozważyć utworzenie `Card` klasy bezpośrednio off bat i wypełnianie zbiór `Card` obiekty ręcznie. Za pomocą LINQ może być bardziej zwięzłe niż zwykły sposób radzenia sobie z tworzeniem talii kart. Zamiast tworzyć `Card` klasy, można utworzyć dwie sekwencje do reprezentowania kolory i rangi texeli, odpowiednio. Utworzysz naprawdę proste parę [ *metody iteracyjne* ](../iterators.md#enumeration-sources-with-iterator-methods) wygeneruje rangę i kolory jako <xref:System.Collections.Generic.IEnumerable%601>s ciągów:

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

Umieść je poniżej `Main` method in Class metoda swoje `Program.cs` pliku. Korzystanie z tych dwóch metod zarówno `yield return` składni, aby utworzyć sekwencję podczas ich działania. Kompilator tworzy obiekt, który implementuje <xref:System.Collections.Generic.IEnumerable%601> i generuje sekwencję ciągów, ponieważ są one wymagane.

Teraz Użyj te metody iteratora, aby utworzyć zbiór kart. Będzie umieścić zapytania LINQ w naszym `Main` metody. Poniżej znajduje się ona:

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

Wielokrotność `from` generuje klauzule <xref:System.Linq.Enumerable.SelectMany%2A>, co powoduje utworzenie pojedynczego ciągu z łączenia każdego elementu w pierwszej kolejności, przy czym każdy element w drugiej sekwencji. Kolejność jest ważna dla naszych potrzeb. Pierwszy element w pierwszej sekwencji źródłowej (kolory) w połączeniu z każdego elementu w drugiej sekwencji (Klasyfikacja). To zapewnia wszystkie karty trzynaście pierwszy koloru. Ten proces jest powtarzany, przy czym każdy element w pierwszej kolejności (kolory). Wynik końcowy jest talii kart uporządkowane według kolory, a następnie według wartości.

Ważne jest, aby pamiętać, że możliwość zapisu LINQ w składni zapytań powyżej czy należy użyć składni metody zamiast tego, zawsze jest możliwe przejść z jednej formy składnia do innego. Zapytanie powyżej napisanych w składni zapytania mogą być napisane w składni metody jako:

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

Kompilator tłumaczy instrukcji LINQ, zapisane ze składnią kwerendy w składni wywołania metody równoważne. W związku z tym niezależnie od wybranego składni, dwie wersje zapytanie generuje ten sam wynik. Wybierz, które składni działa najlepiej w danej sytuacji: na przykład, jeśli pracujesz w zespole, w których niektóre elementy członkowskie mają trudności przy użyciu składni metody, spróbuj preferowanie za pomocą składni zapytania.

Przejdź dalej i uruchom aplikację przykładową na tym etapie konstruowania. Wszystkie karty 52 będzie wyświetlany w talii kart. Może okazać się bardzo pomocne uruchomić ten przykład w debugerze, aby obserwować sposób, w jaki `Suits()` i `Ranks()` wykonywania metody. Wyraźnie widać, że każdego ciągu w każdej sekwencji jest generowany tylko wtedy, gdy jest to konieczne.

![Wyświetlanie aplikacji wypisywanie 52 kart okna konsoli.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulating-the-order"></a>Manipulowanie kolejności

Następnie skoncentrować się na sposób ma zostać losowo zmieniona kolejność kart w talii. Pierwszym krokiem w dowolnej dobre shuffle jest podzielenie slajdów w dwóch. <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> metody, które są częścią interfejsów API LINQ zapewnia tę funkcję dla Ciebie. Umieść je poniżej `foreach` Pętla:

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

Jednakże nie istnieje metoda shuffle z zalet w standardowej bibliotece, dzięki czemu będzie trzeba napisać własny. Metoda losowa, który zostanie utworzony przedstawiono kilka technik, które ma być używany do programów opartych na LINQ, dzięki czemu każda część tego procesu zostaną wyjaśnione w krokach.

Aby dodać funkcjonalność do interakcji z <xref:System.Collections.Generic.IEnumerable%601> wrócisz z zapytań LINQ, musisz zapisać niektórych specjalnymi rodzajami metody o nazwie [metody rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md). Krótko mówiąc, metody rozszerzenia jest specjalnego przeznaczenia *statycznej metody* , dodaje nowe funkcje do już istniejącego typu bez konieczności modyfikowania oryginalnego typu, aby dodać funkcje.

Nadaj nową stronę główną Twoje rozszerzenia metody, dodając nową *statyczne* plik klasy do programu o nazwie `Extensions.cs`, a następnie uruchom kompilowania z pierwszą metodą rozszerzenia:

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

Wyszukaj w podpisie metody moment, w szczególności parametry:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

Możesz zobaczyć dodanie `this` modyfikator na pierwszy argument do metody. Oznacza to, że należy wywołać metodę, tak jakby był metodą elementu członkowskiego typu pierwszego argumentu. Tej deklaracji metody również następujące standardowe idiom gdzie typy wejściowe i wyjściowe są `IEnumerable<T>`. Czy rozwiązanie umożliwia metody LINQ zezwalającym ze sobą, aby wykonywać bardziej złożone zapytania.

Naturalnie ponieważ talii podzielić połowami, należy dołączyć te połowami ze sobą. W kodzie, oznacza to, użytkownik będzie można wyliczanie zarówno sekwencji zakupione w ramach <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> jednocześnie, *`interleaving`* elementy i tworzenia jednej sekwencji: Twoje przekazanych teraz talii kart. Zapisywanie LINQ metodę, która współdziała z dwóch sekwencji wymaga zrozumienia sposobu <xref:System.Collections.Generic.IEnumerable%601> działa.

<xref:System.Collections.Generic.IEnumerable%601> Interfejs ma jedną z metod: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>. Obiekt zwrócony przez <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> ma metodę, aby przejść do następnego elementu i właściwości, która pobiera bieżącego elementu w sekwencji. Te dwa elementy członkowskie użyje do wyliczania kolekcji i zwracają elementy. Ta metoda przeplotu będzie metody iteratora, więc zamiast tworzenia kolekcji i zwraca kolekcję, użyjesz `yield return` składni pokazanych powyżej.

Oto implementacja tej metody:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Teraz, gdy ta metoda jest napisanych, wróć do `Main` metody i shuffle slajdów, gdy:

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

## <a name="comparisons"></a>Porównania

Przesuwa ile zajmuje można ustawić na pokład z powrotem do jego oryginalnej kolejności? Aby dowiedzieć się, będzie konieczne napisanie metody, która określa, czy dwie sekwencje mają taki sam. Po utworzeniu tej metody, należy umieścić kod, który rozmieszcza slajdów w pętli i sprawdź, gdy jest użyta w kolejności.

Zapisywanie metodę, aby określić, czy dwie sekwencje są równe powinno być proste. Jest podobną strukturę z metodą, którą zapisano mieszania slajdów. Tylko to czas, zamiast `yield return`ing każdego elementu, będzie można porównać zgodnych elementów w każdej sekwencji. Sekwencje całą sekwencję zostać wyliczone, jeśli pasuje do każdego elementu, są takie same:

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Spowoduje to pokazanie drugi idiom LINQ: metody terminala. Wykonaj sekwencję jako dane wejściowe (lub w tym przypadku dwie sekwencje) i zwraca pojedynczą wartość skalarną. Korzystając z metody terminala, są one zawsze końcowe metody w łańcuchu metody LINQ, dlatego nazwa zapytania "terminalu".

Można to zobaczyć w działaniu używanej do określania, kiedy talii jest w jego oryginalnej kolejności. Umieść kod shuffle wewnątrz pętli, a następnie Zatrzymaj, gdy sekwencja jest ponownie w jego oryginalnej kolejności, stosując `SequenceEquals()` metody. Widać, że zawsze będzie ostatnią metodę w każdym zapytaniu, ponieważ zwraca pojedynczą wartość zamiast sekwencji:

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

Uruchom kod coś do tej pory i zwróć uwagę na sposób talii zmienia się na każdym shuffle. Po 8 przesuwa (iteracji nie-pętli while), talii powraca do oryginalnej konfiguracji została, podczas pierwszego utworzenia początkowego zapytania LINQ.

## <a name="optimizations"></a>Optymalizacje

Wykonuje przykładowe dołączeniu do tej pory *się shuffle*, gdzie kart górny i dolny pozostają takie same, przy każdym uruchomieniu. Upewnijmy się, co zmiany: użyjemy *w losowo* zamiast tego, gdzie wszystkie karty 52 zmiana położenia. Dla w losowo możesz przeplot slajdów, aby pierwszy karty w dolnej połowie staje się pierwszej karty w talii kart. Oznacza to, że ostatnią kartę w górnej połowie staje się karta dolnej. Jest to prostą zmianę pojedynczej linii kodu. Aktualizacja bieżącego zapytania losowa, przełączając położenie <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A>. Spowoduje to zmianę kolejności górnej i dolnej części talii:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Ponownie uruchom program, a zobaczysz, że zajmuje 52 iteracji dla slajdów zmienić kolejność sam. Będzie również uruchomić, należy zwrócić uwagę spadku wydajności niektórych obniżyć wydajność, ponieważ program kontynuuje działanie.

Istnieje kilka przyczyn. Rozwiązano problem z jednym z głównych powodów tego spadku wydajności: nieefektywne użycie [ *obliczanie leniwe*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Krótko mówiąc obliczanie leniwe stanów obliczania instrukcji nie jest wykonywana do czasu jej wartość jest potrzebna. Zapytania LINQ są instrukcje, które są oceniane opóźnieniem. Sekwencji są generowane tylko wtedy, gdy elementy są wymagane. Zazwyczaj, który jest główną zaletą LINQ. Jednak użycie takich jak ten program, powoduje to wykładniczy wzrost w czasie wykonywania.

Należy pamiętać, firma Microsoft wygenerowania oryginalnego slajdów, za pomocą zapytań LINQ. Każdy losowa jest generowany, wykonując trzy zapytań LINQ w poprzednim slajdów. Wszystkie te są wykonywane opóźnieniem. Oznacza to również, że te procedury są wykonywane ponownie każdorazowo, gdy wymagane są sekwencji. Przez razem, gdy można uzyskać dostęp do 52nd iteracji możesz teraz trwa ponowne generowanie oryginalnego slajdów many, wiele razy. Napiszmy dziennika, aby zademonstrować to zachowanie. Następnie możesz go ma naprawić.

W swojej `Extensions.cs` pliku, wpisz lub skopiuj poniższe metody. Ta metoda rozszerzenia tworzy nowy plik o nazwie `debug.log` w ramach katalogu projektu i rejestruje zapytania, które obecnie jest wykonywana w pliku dziennika. Ta metoda rozszerzenia można dołączyć do dowolnego zapytania, aby oznaczyć, że zapytanie jest wykonywane.

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Pojawi się czerwona fala w obszarze `File`, czyli nie istnieje. Go nie będzie skompilować, ponieważ kompilator nie może ustalić, jakie `File` jest. Aby rozwiązać ten problem, upewnij się, że należy dodać następujący wiersz kodu w ramach pierwszego wiersza w `Extensions.cs`:

```csharp
using System.IO;
```

To powinno rozwiązać problem, a czerwony błąd znika.

Następnie przygotuj Instrumentację definicję każdego zapytania za pomocą komunikatu dziennika:

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

Należy zauważyć, że nie logujesz się za każdym razem, gdy możesz uzyskać dostęp do kwerendy. Zaloguj się tylko wtedy, gdy tworzysz oryginalnego zapytania. Program nadal zajmuje dużo czasu do uruchomienia, ale spowoduje to wyświetlenie dlaczego. Gdy wyczerpią się z rejestrowania włączony, przełącznik shuffle poza systemem shuffle w cierpliwość. Nadal zobaczysz efekty obliczanie z opóźnieniem. W jednym przebiegu wykonuje kwerendy 2592, w tym wszystkich wartości i sposób generowania.

Można zwiększyć wydajność kod do zmniejszenia liczby wykonań, które wprowadzasz w tym miejscu. Proste rozwiązanie, możesz wprowadzić polega na *pamięci podręcznej* wyniki oryginalnego zapytania LINQ, który konstruuje talii kart. Obecnie wykonujesz zapytania ponownie i ponownie każdym razem, gdy nie — gdy pętla przechodzi przez iteracji, ponownie tworząc talii kart i losowego jego grupowania na każdym. W pamięci podręcznej talii kart, można korzystać z metody LINQ <xref:System.Linq.Enumerable.ToArray%2A> i <xref:System.Linq.Enumerable.ToList%2A>; gdy Dołącz je do zapytania, będzie wykonują te same akcje Informujesz im, ale teraz będzie przechowują wyniki w tablicy lub listy, w zależności od tego, w jakiej metody Możesz wybrać do wywołania. Append — metoda LINQ <xref:System.Linq.Enumerable.ToArray%2A> do zapytania i ponownie uruchom program:

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Poza losowa jest teraz do 30 zapytania. Ponownie uruchom za pomocą w losowo i zostaną wyświetlone podobne ulepszenia: teraz wykonuje 162 zapytania.

Należy pamiętać, że w tym przykładzie jest **zaprojektowane** do wyróżnienia przypadki użycia, w którym leniwa ocena może spowodować problemy z wydajnością. Chociaż jest to ważne zobaczyć, gdzie leniwa ocena może wpłynąć na wydajność kodu jest równie ważne dowiedzieć się, że nie wszystkie kwerendy należy uruchamiać eagerly. Wydajności trafień, możesz pociągnąć za sobą bez użycia <xref:System.Linq.Enumerable.ToArray%2A> jest, ponieważ każdy nowy układ talii kart składa się z poprzednich rozmieszczenia. Przy użyciu leniwa ocena oznacza, że każda nowa konfiguracja slajdów składa się z oryginalnego slajdów, nawet wykonywania kodu, który skompilowany `startingDeck`. Dzięki któremu dużą ilość dodatkowej pracy.

W praktyce niektóre algorytmy uruchamiania, również przy użyciu eager oceny, a pozostałe, również korzystając z opóźnieniem. Dzienne użycie opóźnieniem zwykle jest lepszym rozwiązaniem, gdy źródło danych jest oddzielnym procesie, takich jak aparat bazy danych. W przypadku baz danych z opóźnieniem pozwala bardziej złożone zapytania, które można wykonać tylko jeden obiegu do procesu bazy danych i z powrotem do pozostałej części kodu. LINQ jest elastyczny, czy chcesz korzystać z opóźnieniem lub eager oceny, więc mierzenia procesów i wybrać, niezależnie od rodzaju oceny zapewnia najlepszą wydajność.

## <a name="conclusion"></a>Wniosek

W tym projekcie omówione są:
- do istotnych sekwencji za pomocą zapytań LINQ do agregowania danych
- Zapisywanie metody rozszerzenia umożliwiające dodawanie własnych niestandardowych funkcji do zapytań LINQ
- Znajdowanie obszarów w naszym kodzie, w którym nasze zapytań LINQ napotkać problemy z wydajnością, takie jak uszkodzenie szybkości
- Obliczanie z opóźnieniem i chętnie Zapoznamy w odniesieniu do zapytań LINQ oraz skutków tego procesu, mogą pojawić się na wydajności zapytań

Oprócz LINQ przedstawiono nieco dotyczących używania magicians techniki, aby uzyskać wskazówki karty. Magicians Użyj Faro shuffle, ponieważ może kontrolować, gdzie wszystkie karty przemieszcza się w talii kart. Teraz gdy wiesz, nie zepsucia go wszystkim innym użytkownikom!

Aby uzyskać więcej informacji na temat LINQ zobacz:
- [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md)
  - [Wprowadzenie do LINQ](../programming-guide/concepts/linq/index.md)
  - [Podstawowe operacje zapytań LINQ (C#)](../programming-guide/concepts/linq/basic-linq-query-operations.md)
  - [Przekształcanie danych za pomocą LINQ (C#)](../programming-guide/concepts/linq/data-transformations-with-linq.md)
  - [Składnia zapytania i metody w technologii LINQ (C#)](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
  - [Funkcje C# obsługujące LINQ](../programming-guide/concepts/linq/features-that-support-linq.md)
