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
# <a name="work-with-language-integrated-query-linq"></a>Korzystanie z zapytań zintegrowanych z językiem (LINQ)

## <a name="introduction"></a>Wprowadzenie

W tym samouczku przedstawiono funkcje platformy .NET Core i C# języka. Omawiane tematy:

- Generuj sekwencje przy użyciu LINQ.
- Metody zapisu, które mogą być łatwo używane w zapytaniach LINQ.
- Rozróżnianie między eager i oceną z opóźnieniem.

Poznasz te techniki, tworząc aplikację, która pokazuje jedną z podstawowych umiejętności dowolnego czarodziej: [Faro losowo](https://en.wikipedia.org/wiki/Faro_shuffle). Krótko Faro losowo to technika, w której można podzielić talię kart dokładnie na połowę, a następnie losowo przeplata każdą kartę z każdej połowy w celu odbudowania oryginalnego talii.

Magicians użyć tej techniki, ponieważ każda karta znajduje się w znanej lokalizacji po każdym rozłożeniu losowym, a kolejność jest powtarzalnym wzorcem.

Na potrzeby Twoich celów jest jasne spojrzenie na manipulowanie sekwencjami danych. Aplikacja, którą utworzysz, konstruuje talię kart, a następnie wykonuje sekwencję losową, pisząc sekwencję za każdym razem. Porównano również zaktualizowaną kolejność do oryginalnej kolejności.

Ten samouczek zawiera wiele kroków. Po każdym kroku można uruchomić aplikację i postępować według postępu. Możesz również zobaczyć [ukończony przykład](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) w repozytorium GitHub/Samples. Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować maszynę do uruchamiania programu .NET Core. Instrukcje instalacji można znaleźć na stronie [pobierania programu .NET Core](https://dotnet.microsoft.com/download) . Możesz uruchomić tę aplikację w systemie Windows, Ubuntu Linux lub OS X lub w kontenerze platformy Docker. Musisz zainstalować swój ulubiony Edytor kodu. Poniższe opisy wykorzystują [Visual Studio Code](https://code.visualstudio.com/) , który jest edytorem dla wielu platform. Można jednak korzystać z dowolnych narzędzi, z którymi masz doświadczenie.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i Utwórz nowy katalog dla aplikacji. Upewnij się, że bieżący katalog. Wpisz `dotnet new console` polecenia w wierszu polecenia. Spowoduje to utworzenie plików początkowych dla podstawowej aplikacji "Hello world".

Jeśli wcześniej nie korzystano C# z [tego samouczka, ten samouczek](console-teleprompter.md) wyjaśnia strukturę C# programu. Możesz przeczytać ten element, a następnie wrócić tutaj, aby dowiedzieć się więcej na temat LINQ.

## <a name="create-the-data-set"></a>Tworzenie zestawu danych

Przed rozpoczęciem upewnij się, że następujące wiersze znajdują się na początku pliku `Program.cs` wygenerowanego przez `dotnet new console`:

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

Jeśli te trzy wiersze (instrukcje`using`) nie znajdują się na początku pliku, nasz program nie zostanie skompilowany.

Teraz, gdy masz wszystkie odwołania, których potrzebujesz, weź pod uwagę co to jest talia kart. Często talia kart gry ma cztery kolory, a każdy z nich ma trzynastie wartości. Zwykle warto rozważyć utworzenie klasy `Card` po prawej stronie bat i wypełnianie kolekcji obiektów `Card`. Dzięki LINQ można być bardziej zwięzłe niż zwykły sposób tworzenia talii kart. Zamiast tworzyć klasy `Card`, można utworzyć dwie sekwencje, aby reprezentować odpowiednio kolory i Range. Utworzysz bardzo prostą parę [*metod iteratorów*](../iterators.md#enumeration-sources-with-iterator-methods) , które będą generować Range i ubrania jako <xref:System.Collections.Generic.IEnumerable%601>s ciągów:

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

Umieść je poniżej metody `Main` w pliku `Program.cs`. Te dwie metody wykorzystują składnię `yield return` do tworzenia sekwencji podczas jej uruchamiania. Kompilator kompiluje obiekt, który implementuje <xref:System.Collections.Generic.IEnumerable%601> i generuje sekwencję ciągów w miarę ich żądania.

Teraz Użyj tych metod iteratora do utworzenia talii kart. Kwerenda LINQ zostanie umieszczona w naszej metodzie `Main`. Oto jak wygląda:

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

Wielo`from`owe klauzule tworzą <xref:System.Linq.Enumerable.SelectMany%2A>, który tworzy jedną sekwencję od łączenia każdego elementu w pierwszej sekwencji z każdym elementem w drugiej sekwencji. Kolejność jest ważna dla naszych celów. Pierwszy element w pierwszej sekwencji źródłowej (kolory) jest połączony z każdym elementem w drugiej sekwencji (rangi). Spowoduje to wygenerowanie wszystkich trzynastu kart pierwszego koloru. Ten proces jest powtarzany przy każdym elemencie w pierwszej sekwencji (kolory). Wynik końcowy to talia kart uporządkowanych według kolorów, a następnie wartości.

Należy pamiętać, że niezależnie od tego, czy użytkownik zdecyduje się pisać składnik LINQ we wskazanej powyżej składni zapytania lub użyć składni metody zamiast tego, zawsze możliwe jest przechodzenie z jednej formy składni. Powyższe zapytanie zapisywane w składni zapytania można napisać w składni metody jako:

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

Kompilator tłumaczy instrukcje LINQ zapisywane z składnią zapytania na równoważną składnię wywołania metody. W związku z tym, niezależnie od wyboru składni, dwie wersje zapytania dają ten sam wynik. Wybierz, która składnia najlepiej sprawdza się w danej sytuacji: na przykład jeśli pracujesz w zespole, w którym niektórzy członkowie mają problemy ze składnią metody, spróbuj użyć składni zapytania.

Zacznij korzystać z przykładu skompilowanego w tym punkcie. Spowoduje to wyświetlenie wszystkich kart 52 na pokładzie. Przydatne może być uruchomienie tego przykładu w debugerze, aby obserwować sposób wykonywania `Suits()` i `Ranks()` metod. Można jasno zobaczyć, że każdy ciąg w każdej sekwencji jest generowany tylko w razie konieczności.

![Okno konsoli z zapisaniem aplikacji z kartami 52.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulate-the-order"></a>Manipulowanie kolejnością

Następnie należy skoncentrować się na tym, w jaki sposób mają być losowo używane karty na pokładzie. Pierwszym krokiem w każdym dobrym rozbiciem jest podzielenie talii na dwa. Metody <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A>, które są częścią interfejsów API LINQ, udostępniają tę funkcję. Umieść je poniżej pętli `foreach`:

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

Jednak nie ma metody losowej, aby skorzystać z funkcji w bibliotece standardowej, więc musisz napisać własny. Metoda Losowa, która zostanie utworzona, ilustruje kilka technik, które będą używane z programami LINQ, więc każda część tego procesu zostanie omówiona w krokach.

Aby dodać niektóre funkcje do korzystania z <xref:System.Collections.Generic.IEnumerable%601> można wrócić z zapytań LINQ, należy napisać specjalne rodzaje metod nazywanych [metodami rozszerzenia](../programming-guide/classes-and-structs/extension-methods.md). Krótko Metoda rozszerzenia to *metoda statyczna* specjalnego przeznaczenia, która dodaje nową funkcję do już istniejącego typu bez konieczności modyfikowania oryginalnego typu, do którego ma zostać dodana funkcja.

Nadaj rozszerzeniom nowe metody, dodając nowy plik *statycznej* klasy do programu o nazwie `Extensions.cs`, a następnie rozpocznij tworzenie pierwszej metody rozszerzenia:

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

Zapoznaj się z chwilą podpis metody, a w tym parametry:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

Możesz zobaczyć dodanie modyfikatora `this` pierwszego argumentu do metody. Oznacza to, że wywoływana jest metoda, tak jakby była to metoda członkowska typu pierwszego argumentu. Ta deklaracja metody jest również zgodna ze standardową idiom, w którym typy wejściowe i wyjściowe są `IEnumerable<T>`. To rozwiązanie umożliwia łączenie metod LINQ ze sobą w celu wykonywania bardziej złożonych zapytań.

Naturalnie, ze względu na rozdzielenie talii na połowy, należy dołączyć te połówki razem. W kodzie oznacza to, że zostaną wyliczone obie sekwencje nabyte za pośrednictwem <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> na raz, *`interleaving`* elementów i utworzenie jednej sekwencji: teraz rozjmowana talia kart. Pisanie metody LINQ, która współpracuje z dwoma sekwencjami, wymaga zrozumienia sposobu działania <xref:System.Collections.Generic.IEnumerable%601>.

Interfejs <xref:System.Collections.Generic.IEnumerable%601> ma jedną metodę: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>. Obiekt zwrócony przez <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> ma metodę do przejścia do następnego elementu i właściwość, która pobiera bieżący element w sekwencji. Te dwa elementy członkowskie będą używane do wyliczenia kolekcji i zwrócenia elementów. Ta metoda przeplotu będzie metodą iteratora, dlatego zamiast kompilowania kolekcji i zwracania kolekcji, użyj składni `yield return` pokazanej powyżej.

Oto implementacja tej metody:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Teraz, po zapisaniu tej metody, Wróć do metody `Main` i przetwórz losowo talię:

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

Ile trwa losowo, aby ustawić pokład z powrotem do oryginalnej kolejności? Aby dowiedzieć się, należy napisać metodę, która określa, czy dwie sekwencje są równe. Po zastosowaniu tej metody należy umieścić kod, który wystawia talię w pętli, i sprawdzić, czy talia jest odwrócona.

Pisanie metody w celu ustalenia, czy dwie sekwencje są równe, powinny być bezpośrednie. Jest to podobna struktura do metody, która została zapisana w celu rozdzielenia talii. Tylko ten czas, a nie `yield return`Wykorzystaj każdego elementu, porównano pasujące elementy każdej sekwencji. Gdy cała sekwencja została wyliczona, jeśli każdy element jest zgodny, sekwencje są takie same:

[!CODE-csharp[SequenceEquals](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Przedstawiono w nim drugą LINQ idiom: metody terminalowe. Przyjmuje sekwencję jako dane wejściowe (lub w tym przypadku dwie sekwencje) i zwracają pojedynczą wartość skalarną. W przypadku korzystania z metod terminalu są zawsze końcową metodą w łańcuchu metod dla zapytania LINQ, w związku z czym nazwa "Terminal".

Ten element można zobaczyć w działaniu, gdy jest on używany do określenia, kiedy talia zostanie przywrócona w oryginalnej kolejności. Umieść kod losowy wewnątrz pętli i Zatrzymaj, gdy sekwencja zostanie przywrócona w oryginalnej kolejności, stosując metodę `SequenceEquals()`. Można zobaczyć, że zawsze będzie to Ostatnia metoda w dowolnych zapytania, ponieważ zwraca jedną wartość zamiast sekwencji:

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

Uruchom kod, który został już osiągnięty, i zanotuj, jak talia jest zmieniana na każdym losowo. Po 8 losowo (iteracji pętli "do-while") na pokładzie zostanie przywrócona oryginalna konfiguracja, która znajdowała się podczas pierwszego tworzenia go na podstawie uruchomienia zapytania LINQ.

## <a name="optimizations"></a>Optymalizacje

Utworzona przez Ciebie przykład jest wykonywana *losowo*, gdy karty górne i dolne pozostają takie same w każdym przebiegu. Wprowadźmy jedną zmianę: zamiast tego będziemy używać *w* tym miejscu, gdzie wszystkie karty 52 zmieniają pozycję. W przypadku losowego odtwarzania talii należy pozostawać, aby pierwsza karta w dolnej połowie stała się pierwszą kartą na pokładzie. Oznacza to, że ostatnia karta w górnej połowie zmieni się na najniższą kartę. Jest to prosta zmiana w pojedynczej linii kodu. Zaktualizuj bieżące losowe zapytanie, przełączając pozycje <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A>. Spowoduje to zmianę kolejności górnej i dolnej części talii:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Uruchom program ponownie, a zobaczysz, że dla talii zostanie wykonanych 52 iteracji na potrzeby zmiany kolejności. Należy również pamiętać o poważnym obniżeniu wydajności, gdy program będzie kontynuował pracę.

Istnieje kilka przyczyn tego działania. Możesz skorzystać z jednej z głównych przyczyn tego spadku wydajności: niewydajne użycie [*oceny z opóźnieniem*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Krótko, z opóźnieniem, że Ocena instrukcji nie jest wykonywana, dopóki jej wartość nie jest wymagana. Zapytania LINQ to instrukcje, które są oceniane opóźnieniem. Sekwencje są generowane tylko w przypadku, gdy są żądane elementy. Zwykle jest to główna korzyść dla LINQ. Jednak w przypadku użycia takiego jak ten program powoduje wzrost wykładniczy w czasie wykonywania.

Należy pamiętać, że wygenerowałeś oryginalne talie przy użyciu zapytania LINQ. Każda losowo jest generowana przez wykonywanie trzech zapytań LINQ na poprzednim talii. Wszystkie te są wykonywane opóźnieniem. Oznacza to również, że są wykonywane ponownie przy każdym żądaniu sekwencji. Po otrzymaniu do iteracji 52nd można ponownie wygenerować oryginalny tali wiele razy. Napiszmy dziennik, aby zademonstrować to zachowanie. Następnie należy rozwiązać ten problem.

W pliku `Extensions.cs` wpisz lub skopiuj metodę poniżej. Ta metoda rozszerzenia tworzy nowy plik o nazwie `debug.log` w katalogu projektu i rejestruje, jakie zapytanie jest aktualnie wykonywane w pliku dziennika. Tę metodę rozszerzenia można dołączyć do dowolnego zapytania, aby oznaczyć, że zapytanie zostało wykonane.

[!CODE-csharp[LogQuery](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Zostanie wyświetlona czerwona zygzakowata `File`, co oznacza, że nie istnieje. Nie kompiluje się, ponieważ kompilator nie wie, co `File`. Aby rozwiązać ten problem, pamiętaj, aby dodać następujący wiersz kodu poniżej pierwszego wiersza w `Extensions.cs`:

```csharp
using System.IO;
```

Powinno to rozwiązać problem, a czerwony błąd znika.

Następnie instrument definicji każdego zapytania z komunikatem dziennika:

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

Należy zauważyć, że nie rejestruje się za każdym razem, gdy uzyskujesz dostęp do zapytania. Rejestruje się tylko podczas tworzenia oryginalnego zapytania. Uruchomienie programu nadal trwa długo, ale teraz można zobaczyć dlaczego. W przypadku wypróbowania korzystania z trybu losowania z włączonym rejestrowaniem, przełącz się z powrotem na konfigurację losową. Nadal zobaczysz efekty oceny z opóźnieniem. W jednym przebiegu są wykonywane zapytania 2592, w tym cała wartość i generowanie koloru.

W tym miejscu można poprawić wydajność kodu, aby zmniejszyć liczbę wykonanych wykonań. Prosta poprawka, którą można wprowadzić, to *buforowanie* wyników oryginalnego zapytania LINQ, które konstruuje talię kart. Obecnie wykonujesz zapytania ponownie i ponownie za każdym razem, gdy pętla do-while przechodzi przez iterację, należy ponownie skonstruować talię kart i reshuffling je za każdym razem. Aby buforować talię kart, można wykorzystać metody LINQ <xref:System.Linq.Enumerable.ToArray%2A> i <xref:System.Linq.Enumerable.ToList%2A>; Po dołączeniu ich do zapytań będą one wykonywały te same akcje, które zostały przez Ciebie zapamiętane, ale teraz przechowują wyniki w tablicy lub liście, w zależności od wybranej metody do wywołania. Dołącz metodę LINQ <xref:System.Linq.Enumerable.ToArray%2A> do obu zapytań i ponownie uruchom program:

[!CODE-csharp[Main](../../../samples/snippets/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Teraz wychodząca wartość jest wyłączana do 30 zapytań. Uruchom ponownie z użyciem funkcji losowej i zobaczysz podobne udoskonalenia: teraz wykonuje zapytania 162.

Należy pamiętać, że ten przykład został **zaprojektowany** w celu wyróżnienia przypadków użycia, gdy Ocena z opóźnieniem może spowodować problemy z wydajnością. Chociaż ważne jest, aby sprawdzić, gdzie Ocena z opóźnieniem może wpłynąć na wydajność kodu, należy jednak pamiętać, że nie wszystkie zapytania powinny uruchamiać eagerly. Trafienie wydajności, które pozostało bez użycia <xref:System.Linq.Enumerable.ToArray%2A> to ponieważ każde nowe rozmieszczenie kart jest zbudowane z poprzedniego rozmieszczenia. Użycie oceny z opóźnieniem oznacza, że każda nowa konfiguracja jest tworzona na podstawie oryginalnego pokładu, nawet w przypadku wykonywania kodu, który został skompilowany `startingDeck`. Powoduje to znaczną ilość dodatkowego nakładu pracy.

W przypadku niektórych algorytmów działa dobrze przy użyciu oceny eager, a inne działają dobrze przy użyciu oceny z opóźnieniem. W przypadku codziennego użycia Ocena z opóźnieniem jest zazwyczaj lepszym wyborem, gdy źródło danych jest osobnym procesem, takim jak aparat bazy danych. W przypadku baz danych Ocena z opóźnieniem umożliwia bardziej skomplikowane zapytania wykonywanie tylko jednej rundy w procesie bazy danych i powrót do reszty kodu. LINQ jest elastyczne, niezależnie od tego, czy zdecydujesz się na użycie oceny z opóźnieniem, czy eager, więc Zmierz procesy i wybieraj niezależny rodzaj oceny zapewnia najlepszą wydajność.

## <a name="conclusion"></a>Podsumowanie

W tym projekcie omówiono następujące zagadnienia:

- Używanie zapytań LINQ do agregowania danych w zrozumiałej sekwencji
- Pisanie metod rozszerzających, aby dodać własną funkcję niestandardową do zapytań LINQ
- Lokalizowanie obszarów w naszym kodzie, w których nasze zapytania LINQ mogą działać w przypadku problemów z wydajnością, takich jak obniżona szybkość
- obliczenia opóźnione i eager w odniesieniu do zapytań LINQ oraz implikacje, które mogą mieć na wydajność zapytań

Oprócz LINQ wyuczysz się, jak korzystać z techniki Magicians na wskazówki dotyczące kart. Magicians używają Faro losowo, ponieważ mogą one kontrolować, gdzie każda karta przenosi na talię. Teraz, gdy już wiesz, nie ryzykuj go dla innych osób!

Aby uzyskać więcej informacji na temat LINQ, zobacz:

- [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md)
- [Wprowadzenie do LINQ](../programming-guide/concepts/linq/index.md)
- [Podstawowe operacje zapytań LINQ (C#)](../programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Przekształcenia danych za pomocą LINQC#()](../programming-guide/concepts/linq/data-transformations-with-linq.md)
- [Składnia zapytania i składni metody w LINQ (C#)](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
- [Funkcje C# obsługujące LINQ](../programming-guide/concepts/linq/features-that-support-linq.md)
