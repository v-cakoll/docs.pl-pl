---
title: Praca z LINQ
description: "W tym samouczku jest przedstawienie sposobu generowania sekwencji za pomocą LINQ, zapisać metod do użycia w zapytaniach LINQ i rozróżnienia oceny wczesny i opóźnieniem."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/28/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: 3f0fcfebf37d9e6dad52c69111cc5e374ae27183
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="working-with-linq"></a>Praca z LINQ

## <a name="introduction"></a>Wprowadzenie

Ten samouczek zawiera szereg funkcji .NET Core i języka C#. Dowiesz się:

*   Sposób generowania sekwencji za pomocą LINQ
*   Jak napisać metody, które mogą być łatwo używane w zapytaniach LINQ.
*   Jak rozróżnienia oceny wczesny i opóźnieniem.

Te techniki dowiesz się, tworząc aplikację prezentującą podstawowe umiejętności żadnych magician: [losowa faro](https://en.wikipedia.org/wiki/Faro_shuffle). Krótko mówiąc losowa faro to technika gdzie podzielić talii karty dokładnie w połowie, a następnie losowa przeplata każdego jednej karty z każdej połowy odbudować talii oryginalnego.

Magicians użyć tej metody, ponieważ wszystkie karty w znanej lokalizacji po każdym losowa, a kolejność jest powtarzane wzorca. 

W celach naszych jest światła hearted przyjrzeć się manipulowanie sekwencji danych. Aplikację, która będzie kompilacji zostanie skonstruować talii kart, a następnie wykonaj sekwencję przesuwa zapisywania sekwencji zawsze wtedy. Będzie także porównać zaktualizowane kolejności do oryginalnego zamówienia.

Ten samouczek ma wiele kroków. Po każdym kroku możesz uruchomić aplikację i wyświetlany jest postęp. Możesz również sprawdzić [ukończone próbki](https://github.com/dotnet/docs/blob/master/samples/csharp/getting-started/console-linq) w repozytorium GitHub dotnet/docs. Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Wymagania wstępne

Należy skonfigurować komputer, aby uruchomić oprogramowanie .NET core. Instrukcje instalacji można znaleźć na [.NET Core](https://www.microsoft.com/net/core) strony. Można uruchomić tej aplikacji, w systemie Windows, Ubuntu Linux, OS X lub w kontenerze Docker. Należy zainstalować w edytorze kodu dotyczącego elementów ulubionych. Opisy poniżej użyj [Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora. Można jednak użyć dowolnego narzędzia potrafisz.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji. Upewnij się, że sposób bieżącego katalogu. Wpisz polecenie `dotnet new console` w wierszu polecenia. Spowoduje to utworzenie plików starter podstawowe aplikacji "Hello World".

Jeśli nie znasz języka C#, [w tym samouczku](console-teleprompter.md) wyjaśnienie struktury programu w języku C#. Może odczytywać, który i następnie wróć tutaj, aby dowiedzieć się więcej na temat LINQ. 

## <a name="creating-the-data-set"></a>Tworzenie zestawu danych

Zacznijmy od utworzenia zbiór kart. Należy to zrobić to przy użyciu zapytania LINQ, która ma dwa źródła (po jednej dla czterech kolorów, jeden dla trzynaście wartości). Tych źródeł będzie łączyć w talii 52 karty. A `Console.WriteLine` instrukcja wewnątrz `foreach` pętli Wyświetla karty.

Oto zapytania:

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

Wielokrotność `from` utworzyć klauzule `SelectMany`, co powoduje pojedynczego ciągu z łączenie każdego elementu w pierwszej kolejności z każdego elementu w drugim sekwencji. Kolejność jest ważna dla naszych celów. Pierwszym elementem w pierwszym sekwencji źródłowej (mechanizmy) jest połączona z każdym elementem w drugim sekwencji (wartości). Daje to wszystkich kart trzynaście koloru pierwszego. Ten proces jest powtarzany z każdego elementu w pierwszym sekwencji (mechanizmy). W rezultacie jest talii kart uporządkowanych według kolorów, a następnie według wartości.

Następnie należy utworzyć metody Suits() i Ranks(). Zacznijmy od naprawdę proste zbiór *metody iteracyjne* który Generowanie sekwencji jako element wyliczalny z ciągami:

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

Korzystanie z tych dwóch metod zarówno `yield return` składnię, aby utworzyć sekwencję podczas ich działania. Kompilator tworzy obiekt, który implementuje `IEnumerable<T>` i generuje sekwencję ciągów, ponieważ są one wymagane.

Przejdź dalej i uruchom na tym etapie konstruowania próbki. Będzie ono wszystkie 52 karty w talii. Może być bardzo przydatne do uruchomienia tego przykładu w debugerze, aby przyjrzeć się jak `Suits()` i `Values()` wykonania metody. Wyraźnie widać, że każdy ciąg każdej sekwencji jest generowany tylko wtedy, gdy jest to potrzebne.

![Okno konsoli aplikacji wypisywanie 52 kart](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a>Manipulowanie kolejności

Następnie utworzymy metody narzędzia, która może przeprowadzać losowa. Pierwszym krokiem jest podzielenie talii w dwóch. `Take()` i `Skip()` metod, które są częścią interfejsów API LINQ zapewnienia tej funkcji nam:

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

Metoda losowa nie istnieje w biblioteki standardowej, będzie trzeba napisać własne. Ta nowa metoda przedstawiono kilka technik, które będą używane z programów opartych na LINQ, więc warto wyjaśnić, każdego częścią metody w krokach.

Podpis metody tworzy *— metoda rozszerzenia*:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

Metody rozszerzenia jest specjalnego przeznaczenia *metody statycznej.* Zostanie wyświetlony dodanie `this` modyfikator na pierwszy argument do metody. Oznacza to, że należy wywołać metodę tak, jakby była metody elementu członkowskiego typu pierwszy argument.

Metody rozszerzenia mogą być deklarowane tylko wewnątrz `static` klas, więc warto utworzyć nowe klasy statycznej o nazwie `extensions` dla tej funkcji. Dodasz więcej metod rozszerzenia nadal w tym samouczku, a te zostaną umieszczone w tej samej klasy.

Ta deklaracja metody również następuje standardowe idiom gdzie typy wejściowe i wyjściowe są `IEnumerable<T>`. Czy rozwiązanie umożliwia tworzenie łańcucha metody LINQ ze sobą w celu wykonywania bardziej złożonych zapytań.

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

Będzie można wyliczania sekwencji obu na raz, naprzemiennego wykonywania elementów i tworzenie jeden obiekt.  Pisanie zapytań LINQ metodę, która współdziała z dwóch sekwencji wymaga, że rozumiesz, jak `IEnumerable` działa.

`IEnumerable` Interfejs ma jedną metodę: `GetEnumerator()`. Obiekt zwrócony przez `GetEnumerator()` ma metodę, aby przejść do następnego elementu i właściwości, która pobiera bieżący element w sekwencji. Użyjesz tych dwóch członków wyliczyć kolekcji, a następnie wróć elementów. Ta metoda przeplotu będzie metodę iteratora, zamiast tworzenia kolekcji i zwracanie kolekcji, użyjesz `yield return` składni przedstawionych powyżej. 

Oto implementacja tej metody:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Teraz, gdy napisanych tej metody, wróć do `Main` — metoda i losowa talii raz:

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

## <a name="comparisons"></a>Porównania

Zobaczmy, ile przesuwa zajmuje można ustawić talii z powrotem do jej oryginalnej kolejności. Będzie konieczne napisanie metody, która określa, czy dwie sekwencje mają takie same. Po utworzeniu tej metody należy umieścić kod, który shuffles talii w pętli i sprawdź, gdy jest talii w kolejności.

Pisanie metodę, aby ustalić, czy dwie sekwencje są równe powinna być prosta. Jest strukturze podobnej metody, którą zapisano losowo talii. Teraz, zamiast yield zwracanie każdego elementu, można będzie porównywać tylko zgodnych elementów w każdej sekwencji. Sekwencje całą sekwencję wyliczeniu, jeśli pasuje do każdego elementu, są takie same:

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Oznacza to, drugi idiom Linq: metody terminala. Podejmij sekwencji jako dane wejściowe (lub w tym przypadku dwóch sekwencji) i zwraca pojedynczą wartość skalarną. Te metody, gdy są one używane są zawsze metodę końcową zapytania. (Stąd nazwa). 

Widać to w akcji używanej do określania, kiedy talii jest w jej oryginalnej kolejności. Umieść kod losowa wewnątrz pętli i Zatrzymaj, gdy sekwencja jest w jej oryginalnej kolejności, stosując `SequenceEquals()` metody. Można zauważyć, że zawsze powinien być ostatnią metodą każde zapytanie operacji, ponieważ zwraca pojedynczą wartość zamiast sekwencji:

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

Uruchom próbkę i zobacz, jak talii Reorganizuje na każdym losowa, dopóki zwróci oryginalnej konfiguracji po 8 iteracji.

## <a name="optimizations"></a>Optymalizacje

Wykonuje próbki zostały już utworzone w do tej pory *w losowo*, gdzie kart górny i dolny nie zmieniają się przy każdym uruchomieniu. Można wprowadzić zmiany, i uruchom *limit losowa*, w którym wszystkie karty 52 zmienić położenie. Dla poza losowa, możesz interleave talii tak, aby pierwszy karty w dolnej połowie staje się pierwszym karty w talii. Oznacza to, że ostatni karty w górnej połowie staje się karty dolnej. To jest tylko jeden wiersz zmiany. Aktualizacja wywołanie losowo, aby zmienić kolejność górny i dolny połowy talii:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Ponownie uruchom program, i zobaczysz trwa 52 iteracji w celu talii zmienić kolejność samej siebie. Będzie również uruchomić należy zauważyć niektórych degradations obniżyć wydajność, ponieważ program będzie kontynuował działanie.

Istnieje wiele przyczyn tej. Umożliwia spełnienia jednego z głównych powodów: nieefektywne użycie *obliczanie leniwe*.

Zapytania LINQ są oceniane w trybie opóźnienia. Sekwencje są generowane tylko wtedy, gdy elementy są wymagane. Zwykle, który jest główną zaletą LINQ. Jednak użycie takich jak ten program, powoduje wykładniczym wzrostem czasu wykonywania.

Oryginalny talii został wygenerowany za pomocą zapytań LINQ. Każdy losowa jest generowany przez wykonywanie zapytań LINQ trzy na poprzedniej talii. Wszystkie te są wykonywane w trybie opóźnienia. Oznacza to również, że są wykonywane ponownie każdym razem, gdy wymagany jest sekwencja. W czasie, uzyskasz 52nd iteracji możesz jest ponownie wygenerować oryginalnego talii wiele, wiele razy. Napisz dziennika, aby pokazać to zachowanie. Następnie będzie napraw go.

Oto metoda dziennika, który można dołączyć do dowolnej kwerendy do oznaczenia, że zapytanie jest wykonywane.

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Następnie Instrumentacja definicji każdego zapytania o komunikat dziennika:

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

Należy zauważyć, że nie możesz zalogować się za każdym razem, gdy dostęp zapytania. Możesz zalogować się wyłącznie w przypadku utworzenia oryginalne zapytanie. Program nadal trwa długo do uruchomienia, ale spowoduje to wyświetlenie dlaczego. Po uruchomieniu o cierpliwość systemem zewnętrznego losowo z rejestrowaniem włączona, wrócić do losowa wewnętrzny. Obliczanie leniwe efekty będą nadal wyświetlane. W jednym przebiegu wykonywania kwerend 2592, w tym wszystkie wartości i koloru generacji.

Jest to prosty sposób można zaktualizować tego programu, aby uniknąć wszystkich tych wykonania. Brak metody LINQ `ToArray()` i `ToList()` spowodować zapytania do uruchomienia i odpowiednio zapisane wyniki w tablicy lub na liście. Te metody umożliwiają pamięci podręcznej danych wyników zapytania, zamiast ponownie wykonaj zapytanie źródła.  Dołącz zapytania generujących talii kart z wywołaniem do `ToArray()` i ponownie uruchom zapytanie:

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Uruchom ponownie, a wewnętrzny losowa jest do 30 zapytania. Uruchom ponownie, nadając zewnętrzne losowa i zobaczysz ulepszenia podobne. (Go teraz wykonuje zapytania 162).

Nie błędnie interpretuje planowanie, który dzielenia na uruchamiać wszystkie zapytania w tym przykładzie. W tym przykładzie jest przeznaczona do Wyróżnij przypadków użycia, w którym obliczanie leniwe może spowodować problemy z wydajnością. Wynika to z każdego nowego rozmieszczenie talii składa się z poprzednim rozmieszczenia. Przy użyciu obliczanie leniwe oznacza, że każda nowa konfiguracja talii składa się z oryginalnego talii, nawet wykonywanie kodu, który skompilowany `startingDeck`. Która powoduje dużą ilość dodatkowej pracy. 

W praktyce niektóre algorytmy Uruchom znacznie poprawia przy użyciu wczesny oceny, a pozostałe — znacznie poprawia przy użyciu obliczanie leniwe. (Ogólnie rzecz biorąc, obliczanie leniwe jest znacznie lepszym rozwiązaniem gdy źródłem danych jest oddzielnych procesach, takich jak aparatu bazy danych. W takich przypadkach obliczanie leniwe umożliwia bardziej złożonych zapytań można wykonać tylko jeden obiegu do procesu bazy danych.) LINQ umożliwia zarówno opóźnieniem i wczesny oceny. Zmierz i wybierz najlepszym rozwiązaniem.

## <a name="preparing-for-new-features"></a>Przygotowywanie do nowych funkcji

Napisanych dla tego przykładu kodu jest przykład tworzenia prostego prototyp, który wykonuje zadanie. Jest to doskonały sposób, aby eksplorować miejsca problem, a dla wielu funkcji, może być najlepszym rozwiązaniem trwałych. Zostały użyte *typy anonimowe* dla kart, a każda karta jest reprezentowana przez parametry.

*Typy anonimowe* mają wiele zalet wydajności. Nie trzeba zdefiniować klasę samodzielnie do reprezentowania magazynu. Kompilator generuje typ dla Ciebie. Typ wygenerowanego przez kompilator używa wielu najlepszych rozwiązań dotyczących obiektów proste danych. Ma ona *niezmienialnych*, co oznacza, że żaden z jego właściwości można zmienić po ma zostać wykonane. Typy anonimowe są wewnętrzne dla zestawu, więc nie są one widoczne jako część publicznego interfejsu API dla tego zestawu. Typy anonimowe zawierają również zastąpienia z `ToString()` metodę, która zwraca ciąg sformatowany z każdej wartości.

Typy anonimowe ma także wady. Nie ma nazw dostępnych, więc nie można ich użyć jako wartości zwracane lub argumentów. Można zauważyć, które żadnych metod powyżej używane te typy anonimowe są metody ogólne. Zastąpienie z `ToString()` nie może być mają zgodnie z większą liczbą funkcji rozwoju aplikacji. 

Przykład również używa ciągów dla kolor a rangą każdej karty. Która jest otwarta dość zakończone. System typów języka C# mogą pomóc nam w ulepszaniu lepsze kodu, wykorzystując `enum` typy dla tych wartości.

Rozpocznij od kolory. Jest to idealne czas na użycie `enum`:

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

`Suits()` Metody również zmianę typu i implementacji:

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

Następnie wykonaj te same zmiany o randze kart:

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

I metoda generuje je:

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

Jako jeden końcowego oczyszczania można wprowadzić typu do reprezentowania karty, zdejmując to zadanie typu anonimowego. Typy anonimowe są bardzo niewielka, lokalne typów, ale w tym przykładzie karty do gry jest jednym z głównych pojęć. Należy go konkretnego typu.

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

Ten typ używa *automatycznie implementowane właściwości tylko do odczytu* które są ustawiane w konstruktorze, a następnie nie może być modyfikowany. On również sprawia, że użycie nowego *ciągu interpolacji* funkcja, która ułatwia format ciąg w danych wyjściowych.

Zaktualizuj zapytanie, które generuje początkowy talii do użycia nowego typu:

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

Skompiluj i uruchom ponownie. Dane wyjściowe są nieco bardziej przejrzyste i kod jest bardziej wyczyść i można ją rozszerzyć, co ułatwia.

## <a name="conclusion"></a>Wniosek

W tym przykładzie pokazano, możesz niektórych metod LINQ, jak utworzyć własne metody, które będą używane łatwo za pomocą LINQ włączone kodu. On również wyświetlał różnice między opóźnieniem i wczesny ocena oraz wpływ, jaki decyzji może mieć na wydajność.

Poznanie nieco technika magician jeden. Magicians Użyj losowa faro, ponieważ można kontrolować, którym przechodzi wszystkie karty w talii. W niektórych lewy magician ma umieść karty u góry talii członka grupy odbiorców i przesuwa kilka razy, wiedząc, gdzie przejdzie do tej karty. Inne Iluzje wymagają talii ustawić określony sposób. Magician ustawi talii przed wykonaniem lewy. Następnie użytkownik będzie losowo talii 5 razy przy użyciu losowego wewnętrzny. Na etapie klika Pokaż wygląd losowe talii, losowo go 3 razy więcej i talii ustawić dokładnie tak jak chce mieć.
