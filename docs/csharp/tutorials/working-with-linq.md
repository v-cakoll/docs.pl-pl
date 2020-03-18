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
# <a name="work-with-language-integrated-query-linq"></a>Praca z zazapytaniem zintegrowanym z językiem (LINQ)

## <a name="introduction"></a>Wprowadzenie

W tym samouczku nauczy Cię funkcje w .NET Core i języku C#. Omawiane tematy:

- Generowanie sekwencji za pomocą LINQ.
- Pisanie metod, które mogą być łatwo używane w zapytaniach LINQ.
- Rozróżnianie oceny chętnej i leniwej.

Nauczysz się tych technik, budując aplikację, która pokazuje jedną z podstawowych umiejętności każdego maga: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle). Krótko mówiąc, faro shuffle to technika, w której dzielisz talię kart dokładnie na pół, a następnie tasowanie przeplata każdą kartę z każdej połowy, aby odbudować oryginalną talię.

Magowie używają tej techniki, ponieważ każda karta znajduje się w znanej lokalizacji po każdym shuffle, a kolejność jest powtarzającym się wzorem.

Dla Twoich celów jest to lekkie spojrzenie na manipulowanie sekwencjami danych. Aplikacja, którą zbudujesz, tworzy talię kart, a następnie wykonuje sekwencję tasowania, zapisując sekwencję za każdym razem. Zostanie również porównane zaktualizowane zamówienie z oryginalnym zamówieniem.

Ten samouczek ma wiele kroków. Po każdym kroku można uruchomić aplikację i zobaczyć postęp. Możesz również zobaczyć [ukończoną próbkę](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) w repozytorium GitHub dotnet/samples. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować komputer do uruchamiania rdzenia .NET. Instrukcje instalacji można znaleźć na stronie [pobierania .NET Core.](https://dotnet.microsoft.com/download) Możesz uruchomić tę aplikację w systemie Windows, Ubuntu Linux lub OS X lub w kontenerze Platformy Docker. Musisz zainstalować swój ulubiony edytor kodu. Poniższe opisy używają [kodu Programu Visual Studio,](https://code.visualstudio.com/) który jest edytorem open source, między platformami. Możesz jednak użyć dowolnych narzędzi, które Ci się podobają.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i utwórz nowy katalog dla aplikacji. Upewnij się, że bieżący katalog. Wpisz `dotnet new console` polecenie w wierszu polecenia. Spowoduje to utworzenie plików startowych dla podstawowej aplikacji "Hello World".

Jeśli nigdy wcześniej nie używano języka C#, [w tym samouczku](console-teleprompter.md) wyjaśniono strukturę programu C#. Możesz przeczytać, że a następnie wrócić tutaj, aby dowiedzieć się więcej o LINQ.

## <a name="create-the-data-set"></a>Tworzenie zestawu danych

Przed rozpoczęciem upewnij się, że w górnej `Program.cs` części pliku `dotnet new console`generowanego przez:

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

Jeśli te trzy`using` wiersze (instrukcje) nie są w górnej części pliku, nasz program nie będzie kompilować.

Teraz, gdy masz wszystkie odniesienia, które będą potrzebne, zastanów się, co stanowi talię kart. Często talia kart do gry ma cztery garnitury, a każdy garnitur ma trzynaście wartości. Zwykle można rozważyć `Card` utworzenie klasy tuż nietoperza i wypełnianie kolekcji `Card` obiektów ręcznie. Z LINQ możesz być bardziej zwięzły niż zwykły sposób radzenia sobie z tworzeniem talii kart. Zamiast tworzyć `Card` klasę, można utworzyć dwie sekwencje do reprezentowania odpowiednio garnitury i rangi. Utworzysz naprawdę prostą parę [*metod iteratoratu, które wygenerują*](../iterators.md#enumeration-sources-with-iterator-methods) rangi i kolory jako <xref:System.Collections.Generic.IEnumerable%601>ciągi s:

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

Umieść je pod `Main` metodą `Program.cs` w pliku. Te dwie metody wykorzystują `yield return` składnię do tworzenia sekwencji podczas uruchamiania. Kompilator tworzy obiekt, <xref:System.Collections.Generic.IEnumerable%601> który implementuje i generuje sekwencję ciągów, ponieważ są one wymagane.

Teraz użyj tych metod iteratorem, aby stworzyć talię kart. W naszej `Main` metodzie umieścisz zapytanie LINQ. Oto spojrzenie na to:

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

Wiele `from` klauzul tworzy <xref:System.Linq.Enumerable.SelectMany%2A>, który tworzy pojedynczą sekwencję z łączenia każdego elementu w pierwszej sekwencji z każdym elementem w drugiej sekwencji. Zamówienie jest ważne dla naszych celów. Pierwszy element w pierwszej sekwencji źródłowej (Suits) jest połączony z każdym elementem w drugiej sekwencji (Rangi). Daje to wszystkie trzynaście kart pierwszego koloru. Proces ten jest powtarzany z każdym elementem w pierwszej sekwencji (Suits). Efektem końcowym jest talia kart zamówionych przez garnitury, a następnie wartości.

Należy pamiętać, że niezależnie od tego, czy zdecydujesz się zapisać linq w składni kwerendy używanej powyżej, czy zamiast tego użyć składni metody, zawsze można przejść z jednej formy składni do drugiej. Powyższe zapytanie zapisane w składni kwerendy można zapisać w składni metody jako:

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

Kompilator tłumaczy instrukcje LINQ napisane składnią kwerendy na składnię wywołania równoważnej metody. W związku z tym niezależnie od wyboru składni dwie wersje kwerendy dają ten sam wynik. Wybierz, która składnia działa najlepiej dla Twojej sytuacji: na przykład, jeśli pracujesz w zespole, w którym niektóre elementy członkowskie mają trudności ze składnią metody, spróbuj preferować używanie składni zapytania.

Śmiało i uruchomić przykład utworzony w tym momencie. Wyświetli wszystkie 52 karty w talii. Może się okazać, że bardzo pomocne jest uruchomienie tego `Suits()` przykładu w obszarze debugera, aby obserwować, jak i `Ranks()` metody wykonywania. Wyraźnie widać, że każdy ciąg w każdej sekwencji jest generowany tylko wtedy, gdy jest potrzebny.

![Okno konsoli z wypisaniem przez aplikację 52 kart.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulate-the-order"></a>Manipulowanie zamówieniem

Następnie skoncentruj się na tym, jak będziesz tasować karty w talii. Pierwszym krokiem w każdym dobrym shuffle jest podzielenie talii na dwie części. I <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A> metody, które są częścią linq interfejsów API zapewniają tę funkcję dla Ciebie. Umieść je pod `foreach` pętlą:

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

Jednak nie ma metody shuffle, aby skorzystać z w standardowej bibliotece, więc będziesz musiał napisać własne. Metoda shuffle, którą będziesz tworzyć, ilustruje kilka technik, których będziesz używać z programami opartymi na LINQ, więc każda część tego procesu zostanie wyjaśniona w krokach.

Aby dodać niektóre funkcje do interakcji z <xref:System.Collections.Generic.IEnumerable%601> tobą będzie można uzyskać z zapytania LINQ, należy napisać kilka specjalnych rodzajów metod [zwanych metodami rozszerzenia](../programming-guide/classes-and-structs/extension-methods.md). Krótko mówiąc, metoda rozszerzenia jest *metodą statyczną* specjalnego przeznaczenia, która dodaje nowe funkcje do już istniejącego typu bez konieczności modyfikowania oryginalnego typu, do którego chcesz dodać funkcje.

Nadaj metodom rozszerzenia nowy dom, dodając nowy plik `Extensions.cs`klasy *statycznej* do programu o nazwie , a następnie zacznij budować pierwszą metodę rozszerzenia:

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

Spójrz na podpis metody na chwilę, w szczególności parametry:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

Możesz zobaczyć dodanie modyfikatora `this` na pierwszy argument do metody. Oznacza to, że można wywołać metodę tak, jakby była to metoda członkowski typu pierwszego argumentu. Ta deklaracja metody jest również zgodna ze standardowym `IEnumerable<T>`idiomem, w którym są typy danych wejściowych i wyjściowych. Ta praktyka umożliwia linq metody, które mają być połączone ze sobą w celu wykonywania bardziej złożonych zapytań.

Oczywiście, ponieważ dzielisz talię na połówki, musisz połączyć te połówki razem. W kodzie oznacza to, że będziesz wyliczać obie <xref:System.Linq.Enumerable.Take%2A> sekwencje, które zostały nabyte za pośrednictwem i <xref:System.Linq.Enumerable.Skip%2A> od razu, *`interleaving`* elementy i tworzenie jednej sekwencji: teraz tasowane talii kart. Pisanie metody LINQ, która działa z dwiema <xref:System.Collections.Generic.IEnumerable%601> sekwencjami wymaga, aby zrozumieć, jak działa.

Interfejs <xref:System.Collections.Generic.IEnumerable%601> ma jedną <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>metodę: . Obiekt zwracany <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> przez ma metodę, aby przejść do następnego elementu i właściwość, która pobiera bieżący element w sekwencji. Użyjesz tych dwóch elementów członkowskich, aby wyliczyć kolekcję i zwrócić elementy. Ta metoda przeplotu będzie metoda iterator, więc zamiast tworzenia kolekcji i zwracanie `yield return` kolekcji, należy użyć składni pokazano powyżej.

Oto implementacja tej metody:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Teraz, gdy już napisałeś tę metodę, wróć do `Main` metody i shuffle pokładu raz:

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

Ile przetasowań potrzeba, aby przywrócić talię do pierwotnego porządku? Aby się tego dowiedzieć, musisz napisać metodę, która określa, czy dwie sekwencje są równe. Po tej metodzie musisz umieścić kod, który tasuje talię w pętli, i sprawdzić, kiedy talia jest z powrotem w kolejności.

Pisanie metody w celu ustalenia, czy dwie sekwencje są równe powinno być proste. Jest to podobna struktura do metody, którą napisałeś, aby przetasować talię. Tylko tym razem, `yield return`zamiast każdego elementu, porównasz pasujące elementy każdej sekwencji. Gdy cała sekwencja została wyliczona, jeśli każdy element pasuje, sekwencje są takie same:

[!CODE-csharp[SequenceEquals](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Pokazuje to drugi idiom LINQ: metody terminala. Przyjmują sekwencję jako dane wejściowe (lub w tym przypadku dwie sekwencje) i zwracają pojedynczą wartość skalarną. Podczas korzystania z metod terminalowych, są one zawsze ostateczną metodą w łańcuchu metod dla kwerendy LINQ, stąd nazwa "terminal".

Można to zobaczyć w akcji, gdy używasz go do określenia, kiedy pokład jest z powrotem w oryginalnej kolejności. Umieść kod shuffle wewnątrz pętli i zatrzymaj się, gdy sekwencja `SequenceEquals()` jest z powrotem w oryginalnej kolejności, stosując metodę. Widać, że zawsze będzie to metoda ostateczna w dowolnej kwerendzie, ponieważ zwraca pojedynczą wartość zamiast sekwencji:

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

Uruchom kod, który masz do tej pory i zanotuj, jak talia zmienia układ na każdym shuffle. Po 8 tasowania (iteracje pętli do-while), deck powraca do oryginalnej konfiguracji, w której był podczas tworzenia go po raz pierwszy z początkowej kwerendy LINQ.

## <a name="optimizations"></a>Optymalizacje

Przykład, który do tej pory został zbudowany, wykonuje *shuffle out,* gdzie górna i dolna karta pozostają takie same przy każdym uruchomieniu. Wytoczmy jedną zmianę: zamiast tego użyjemy *shuffle,* gdzie wszystkie 52 karty zmienią pozycję. W przypadku przetasowania przeplatasz talię, aby pierwsza karta w dolnej połowie stała się pierwszą kartą w talii. Oznacza to, że ostatnia karta w górnej połowie staje się dolną kartą. Jest to prosta zmiana w liczbie pojedynczej linii kodu. Zaktualizuj bieżącą kwerendę shuffle, <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A>przełączając pozycje i . Spowoduje to zmianę kolejności górnych i dolnych połówek talii:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Uruchom program ponownie, a zobaczysz, że potrzeba 52 iteracji, aby talia sama się uporządkowała. Zaczniesz również zauważać poważne pogorszenie wydajności, gdy program będzie nadal działał.

Istnieje wiele powodów. Można rozwiązać jedną z głównych przyczyn tego spadku wydajności: nieefektywne wykorzystanie [*leniwej oceny*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Krótko mówiąc, ocena z opóźnieniem stwierdza, że ocena instrukcji nie jest wykonywana, dopóki nie jest potrzebna jej wartość. Zapytania LINQ są instrukcje, które są oceniane leniwie. Sekwencje są generowane tylko wtedy, gdy są wymagane elementy. Zazwyczaj jest to duża zaleta LINQ. Jednak w użyciu, takich jak ten program, powoduje to wykładniczy wzrost czasu wykonywania.

Pamiętaj, że wygenerowaliśmy oryginalną talię za pomocą zapytania LINQ. Każde shuffle jest generowany przez wykonanie trzech zapytań LINQ w poprzedniej talii. Wszystkie te są wykonywane leniwie. Oznacza to również, że są one wykonywane ponownie za każdym razem, gdy żądana jest sekwencja. Do czasu dojście do 52 iteracji, jesteś regeneracji oryginalnej talii wiele, wiele razy. Napiszmy dziennik, aby zademonstrować to zachowanie. Następnie naprawisz to.

W `Extensions.cs` pliku wpisz lub skopiuj poniższą metodę. Ta metoda rozszerzenia tworzy `debug.log` nowy plik wywoływany w katalogu projektu i rejestruje, jakie zapytanie jest obecnie wykonywane do pliku dziennika. Tę metodę rozszerzenia można dołączać do dowolnej kwerendy, aby oznaczyć wykonaną kwerendę.

[!CODE-csharp[LogQuery](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Zobaczysz czerwoną fałszon pod `File`, co oznacza, że nie istnieje. Nie będzie kompilować, ponieważ kompilator nie `File` wie, co to jest. Aby rozwiązać ten problem, upewnij się, aby dodać następujący `Extensions.cs`wiersz kodu w pierwszym wierszu w:

```csharp
using System.IO;
```

Powinno to rozwiązać problem i czerwony błąd znika.

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

Należy zauważyć, że nie rejestrujesz się za każdym razem, gdy uzyskujesz dostęp do zapytania. Logujesz się tylko podczas tworzenia oryginalnej kwerendy. Program nadal zajmuje dużo czasu, aby uruchomić, ale teraz można zobaczyć, dlaczego. Jeśli zabraknie cierpliwości uruchomiony w shuffle z rejestrowania włączone, przełącz się z powrotem do out shuffle. Nadal zobaczysz efekty oceny leniwy. W jednym uruchomieniu wykonuje 2592 zapytań, w tym wszystkie wartości i powszedniania koloru.

Można zwiększyć wydajność kodu w tym miejscu, aby zmniejszyć liczbę wykonań, które można wykonać. Prostą poprawką, którą można wprowadzić, jest *buforowanie* wyników oryginalnej kwerendy LINQ, która tworzy talię kart. Obecnie wykonujesz zapytania raz za każdym razem, gdy pętla do-while przechodzi przez iterację, rekonstruując talię kart i przetasowania za każdym razem. Aby buforować talię kart, możesz wykorzystać <xref:System.Linq.Enumerable.ToArray%2A> metody <xref:System.Linq.Enumerable.ToList%2A>LINQ i ; po dodaniu ich do zapytań będą one wykonywać te same akcje, które im powiesz, ale teraz będą przechowywać wyniki w tablicy lub liście, w zależności od wybranej metody. Dołącz metodę <xref:System.Linq.Enumerable.ToArray%2A> LINQ do obu zapytań i uruchom program ponownie:

[!CODE-csharp[Main](../../../samples/snippets/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Teraz obecnie shuffle jest w dół do 30 zapytań. Uruchom ponownie z in shuffle, a zobaczysz podobne ulepszenia: teraz wykonuje 162 zapytań.

Należy pamiętać, że w tym przykładzie jest **przeznaczony** do podkreślenia przypadków użycia, gdzie leniwy oceny może powodować trudności w wydajności. Chociaż ważne jest, aby zobaczyć, gdzie ocena z opóźnieniem może mieć wpływ na wydajność kodu, równie ważne jest, aby zrozumieć, że nie wszystkie zapytania powinny działać z niecierpliwością. Wydajność, którą poniesiesz bez użycia, <xref:System.Linq.Enumerable.ToArray%2A> wynika z tego, że każdy nowy układ talii kart jest zbudowany z poprzedniego układu. Korzystanie z leniwej oceny oznacza, że każda nowa konfiguracja pokładu jest zbudowana z oryginalnej talii, nawet wykonując kod, który zbudował `startingDeck`. To powoduje dużą ilość dodatkowej pracy.

W praktyce niektóre algorytmy działają dobrze przy użyciu chętnie oceny, a inne działają dobrze przy użyciu oceny leniwy. W przypadku codziennego użycia oceny z opóźnieniem jest zwykle lepszym wyborem, gdy źródło danych jest oddzielnyproces, jak aparat bazy danych. W przypadku baz danych oceny z opóźnieniem umożliwia bardziej złożonych zapytań do wykonania tylko jedną podróż w obie strony do procesu bazy danych i z powrotem do reszty kodu. LINQ jest elastyczny, niezależnie od tego, czy zdecydujesz się wykorzystać leniwą lub chętną ocenę, więc mierz procesy i wybieraj niezależnie od rodzaju oceny, która zapewnia najlepszą wydajność.

## <a name="conclusion"></a>Podsumowanie

W tym projekcie omówiłeś:

- używanie zapytań LINQ do agregowania danych w sensowną sekwencję
- pisanie metod rozszerzenia w celu dodania własnych funkcji niestandardowych do zapytań LINQ
- lokalizowanie obszarów w naszym kodzie, w których nasze zapytania LINQ mogą napotkać problemy z wydajnością, takie jak obniżona prędkość
- leniwy i chętnie oceny w odniesieniu do zapytań LINQ i implikacje mogą mieć na wydajność zapytań

Oprócz LINQ, dowiedziałeś się trochę o technice magików używać do sztuczek karty. Magowie używają losu Faro, ponieważ mogą kontrolować, gdzie każda karta porusza się w talii. Teraz, gdy już wiesz, nie psuj go wszystkim innym!

Aby uzyskać więcej informacji na temat LINQ, zobacz:

- [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md)
- [Wprowadzenie do LINQ](../programming-guide/concepts/linq/index.md)
- [Podstawowe operacje zapytań LINQ (C#)](../programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Transformacje danych z LINQ (C#)](../programming-guide/concepts/linq/data-transformations-with-linq.md)
- [Składnia zapytania i metody w technologii LINQ (C#)](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
- [Funkcje C# obsługujące LINQ](../programming-guide/concepts/linq/features-that-support-linq.md)
