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
# <a name="working-with-linq"></a>Praca z technologią LINQ

## <a name="introduction"></a>Wprowadzenie

W tym samouczku pokazano pewną liczbę funkcji platformy .NET Core i języka C#. Dowiesz się:

*   Sposób generowania sekwencji za pomocą LINQ
*   Jak napisać metody, które mogą być łatwo używane w kwerendach LINQ.
*   Jak rozróżnianie między eager i leniwa ocena.

Te techniki dowiesz się, tworząc aplikację, która przedstawia jedną z podstawowych umiejętności wszelkie magician: [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle). Krótko mówiąc faro shuffle jest techniką, gdzie możesz podzielić talii kart dokładnie w połowie, a następnie shuffle przeplatają każdego jedną kartę, z każda część odbudować oryginalnego slajdów.

Magicians Użyj tej techniki, ponieważ wszystkie karty w znanej lokalizacji po każdym losowa, a kolejność jest wzorzec powtarzające się. 

Dla naszych potrzeb jest światła hearted przyjrzeć manipulowanie sekwencji danych. Aplikację, którą utworzysz konstruowania talii kart, a następnie wykonać sekwencję przesuwa, zapisywanie sekwencji zawsze wtedy. Zostanie również porównać zaktualizowane kolejność oryginalnej kolejności.

W tym samouczku składa się z wielu kroków. Po każdym kroku możesz uruchomić aplikację i wyświetlić postęp. Można również wyświetlić [ukończone przykładowe](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) w repozytorium dotnet/samples w witrynie GitHub. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Wymagania wstępne

Należy skonfigurować maszynę w taki sposób, aby uruchomić platformy .NET core. Instrukcje dotyczące instalacji można znaleźć na [platformy .NET Core](https://www.microsoft.com/net/core) strony. Mogą uruchamiać tę aplikację w systemie Windows, Ubuntu Linux, OS X lub w kontenerze platformy Docker. Musisz zainstalować wybrany edytor kodu. Opisy poniżej użycia [programu Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora. Można jednak użyć dowolnego narzędzia potrafisz.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji. Upewnij się, że sposób bieżącego katalogu. Wpisz polecenie `dotnet new console` w wierszu polecenia. Spowoduje to utworzenie plikach startowych dla podstawowych aplikacji "Hello World".

Jeśli nie znasz języka C#, [w tym samouczku](console-teleprompter.md) wyjaśnienie struktury programu w języku C#. Może odczytywać, który i następnie wróć tutaj, aby dowiedzieć się więcej na temat LINQ. 

## <a name="creating-the-data-set"></a>Tworzenie zestawu danych

Zacznijmy od utworzenia talii kart. Należy to zrobić tego przy użyciu zapytania LINQ, która ma dwa źródła (jedną dla czterech odpowiada, jeden dla trzynaście wartości). Tych źródeł będzie łączyć w talii kart 52. A `Console.WriteLine` instrukcji wewnątrz `foreach` pętli Wyświetla karty.

Oto zapytanie:

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

Wielokrotność `from` generuje klauzule `SelectMany`, co powoduje utworzenie pojedynczego ciągu z łączenia każdego elementu w pierwszej kolejności, przy czym każdy element w drugiej sekwencji. Kolejność jest ważna dla naszych potrzeb. Pierwszy element w pierwszej sekwencji źródłowej (kolory) w połączeniu z każdego elementu w drugiej sekwencji (wartości). To zapewnia wszystkie karty trzynaście pierwszy koloru. Ten proces jest powtarzany, przy czym każdy element w pierwszej kolejności (kolory). Wynik końcowy jest talii kart uporządkowane według kolory, a następnie według wartości.

Następnie należy tworzyć metody Suits() i Ranks(). Zacznijmy od bardzo prosty zestaw *metody iteracyjne* , którzy generują sekwencja jako wyliczalny element z ciągami:

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

Korzystanie z tych dwóch metod zarówno `yield return` składni, aby utworzyć sekwencję podczas ich działania. Kompilator tworzy obiekt, który implementuje `IEnumerable<T>` i generuje sekwencję ciągów, ponieważ są one wymagane.

W tym można skompilować należy dodać następujące dwa wiersze na początku pliku:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
```

Przejdź dalej i uruchom aplikację przykładową na tym etapie konstruowania. Wszystkie karty 52 będzie wyświetlany w talii kart. Może okazać się bardzo pomocne uruchomić ten przykład w debugerze, aby obserwować sposób, w jaki `Suits()` i `Values()` wykonywania metody. Wyraźnie widać, że każdego ciągu w każdej sekwencji jest generowany tylko wtedy, gdy jest to konieczne.

![Okno konsoli aplikacji wypisywanie 52 kart](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a>Manipulowanie kolejności

Następnie utworzymy metody narzędzie, które może wykonywać losowa. Pierwszym krokiem jest podzielenie slajdów w dwóch. `Take()` i `Skip()` metody, które są częścią interfejsów API LINQ zapewnia tę funkcję dla nas:

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

Metoda shuffle nie istnieje w standardowej bibliotece, dzięki czemu będzie trzeba napisać własny. Ta nowa metoda przedstawiono kilka technik, które ma być używany do programów opartych na LINQ, więc opisano każdej części metody w krokach.

Podpis metody tworzy *— metoda rozszerzenia*:

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

Metoda rozszerzenia jest specjalnego przeznaczenia *metody statycznej.* Możesz zobaczyć dodanie `this` modyfikator na pierwszy argument do metody. Oznacza to, że należy wywołać metodę, tak jakby był metodą elementu członkowskiego typu pierwszego argumentu.

Metody rozszerzenia mogą być deklarowane tylko w `static` klasy, więc Utwórz nową klasę statycznego o nazwie `extensions` dla tej funkcji. Kontynuuj w tym samouczku, a te zostaną umieszczone w tej samej klasy należy dodać więcej metod rozszerzenia.

Tej deklaracji metody również następujące standardowe idiom gdzie typy wejściowe i wyjściowe są `IEnumerable<T>`. Czy rozwiązanie umożliwia metody LINQ zezwalającym ze sobą, aby wykonywać bardziej złożone zapytania.

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

Będziesz wyliczanie zarówno sekwencje jednocześnie, z przeplotem elementy i utworzenie jednego obiektu.  Zapisywanie LINQ metodę, która współdziała z dwóch sekwencji wymaga zrozumienia sposobu `IEnumerable` działa.

`IEnumerable` Interfejs ma jedną z metod: `GetEnumerator()`. Obiekt zwrócony przez `GetEnumerator()` ma metodę, aby przejść do następnego elementu i właściwości, która pobiera bieżącego elementu w sekwencji. Te dwa elementy członkowskie użyje do wyliczania kolekcji i zwracają elementy. Ta metoda przeplotu będzie metody iteratora, więc zamiast tworzenia kolekcji i zwraca kolekcję, użyjesz `yield return` składni pokazanych powyżej. 

Oto implementacja tej metody:

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Teraz, gdy ta metoda jest napisanych, wróć do `Main` metody i shuffle slajdów, gdy:

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

Zobaczmy, ile przesuwa zajmuje można ustawić na pokład z powrotem do jego oryginalnej kolejności. Będzie konieczne napisanie metody, która określa, czy dwie sekwencje mają taki sam. Po utworzeniu tej metody, należy umieścić kod, który rozmieszcza slajdów w pętli i sprawdź, gdy jest użyta w kolejności.

Zapisywanie metodę, aby określić, czy dwie sekwencje są równe powinno być proste. Jest podobną strukturę z metodą, którą zapisano mieszania slajdów. Tylko tym razem zamiast wydajności zwracanie każdego elementu, można będzie porównywać zgodnych elementów w każdej sekwencji. Sekwencje całą sekwencję zostać wyliczone, jeśli pasuje do każdego elementu, są takie same:

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Spowoduje to pokazanie drugi idiom Linq: metody terminala. Wykonaj sekwencję jako dane wejściowe (lub w tym przypadku dwie sekwencje) i zwraca pojedynczą wartość skalarną. Te metody, gdy są one używane, są zawsze ostatnią metodę zapytania. (Stąd nazwa). 

Można to zobaczyć w działaniu używanej do określania, kiedy talii jest w jego oryginalnej kolejności. Umieść kod shuffle wewnątrz pętli, a następnie Zatrzymaj, gdy sekwencja jest ponownie w jego oryginalnej kolejności, stosując `SequenceEquals()` metody. Widać, że zawsze będzie ostatnią metodę w każdym zapytaniu, ponieważ zwraca pojedynczą wartość zamiast sekwencji:

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

Uruchamianie aplikacji przykładowej i zobacz, jak talii Reorganizuje na każdym shuffle aż powraca do oryginalnej konfiguracji po 8 iteracjach.

## <a name="optimizations"></a>Optymalizacje

Wykonuje przykładowe dołączeniu do tej pory *się shuffle*, gdzie kart górny i dolny pozostają takie same, przy każdym uruchomieniu. Upewnijmy się zmienić, i uruchom *w losowo*, gdzie wszystkie karty 52 zmiana położenia. Dla w losowo możesz przeplot slajdów, aby pierwszy karty w dolnej połowie staje się pierwszej karty w talii kart. Oznacza to, że ostatnią kartę w górnej połowie staje się karta dolnej. Który różni się tylko jeden wiersz. Zaktualizuj mieszania, aby zmienić kolejność górnej i dolnej części talii wywołanie:

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Ponownie uruchom program, a zobaczysz, że zajmuje 52 iteracji dla slajdów zmienić kolejność sam. Będzie również uruchomić, należy zwrócić uwagę spadku wydajności niektórych obniżyć wydajność, ponieważ program kontynuuje działanie.

Istnieje kilka przyczyn. Udzielmy jedną z głównych przyczyn: nieefektywne użycie *obliczanie leniwe*.

Zapytania LINQ są oceniane opóźnieniem. Sekwencji są generowane tylko wtedy, gdy elementy są wymagane. Zazwyczaj, który jest główną zaletą LINQ. Jednak użycie takich jak ten program, powoduje to wykładniczy wzrost w czasie wykonywania.

Oryginalny slajdów został wygenerowany przy użyciu zapytania LINQ. Każdy losowa jest generowany, wykonując trzy zapytań LINQ w poprzednim slajdów. Wszystkie te są wykonywane opóźnieniem. Oznacza to również, że te procedury są wykonywane ponownie każdorazowo, gdy wymagane są sekwencji. Przez razem, gdy można uzyskać dostęp do 52nd iteracji możesz teraz trwa ponowne generowanie oryginalnego slajdów many, wiele razy. Napiszmy dziennika, aby zademonstrować to zachowanie. Następnie możesz go ma naprawić.

Oto metoda dziennika, który można dołączyć do dowolnego zapytania, aby oznaczyć, że zapytanie jest wykonywane.

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Następnie przygotuj Instrumentację definicję każdego zapytania za pomocą komunikatu dziennika:

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

Należy zauważyć, że nie logujesz się za każdym razem, gdy możesz uzyskać dostęp do kwerendy. Zaloguj się tylko wtedy, gdy tworzysz oryginalnego zapytania. Program nadal zajmuje dużo czasu do uruchomienia, ale spowoduje to wyświetlenie dlaczego. Po uruchomieniu o cierpliwość systemem wewnętrzny mieszania za pomocą funkcji rejestrowania włączona, przejdź z powrotem do zewnętrznego losowa. Nadal zobaczysz efekty obliczanie z opóźnieniem. W jednym przebiegu wykonuje kwerendy 2592, w tym wszystkich wartości i sposób generowania.

Istnieje łatwy sposób zaktualizować ten program, aby uniknąć tych operacji wykonywania. Istnieją metody LINQ `ToArray()` i `ToList()` spowodować, że zapytanie, aby uruchomić i zapisać wyniki w tablicy lub listy, odpowiednio. Metody te służy do danych wyników zapytania w pamięci podręcznej, zamiast ponownie wykonaj zapytanie źródła.  Dołącz zapytania, które generują talii kart z wywołaniem `ToArray()` i ponownie uruchom zapytanie:

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Uruchom ponownie i zewnętrzne losowa jest poniżej 30 zapytania. Ponownie uruchom za pomocą wewnętrznego losowa i zostaną wyświetlone podobne ulepszenia. (Obecnie wykonuje zapytania 162).

Nie błędnie interpretuje planowanie, który eagerly uruchamiać wszystkie zapytania w tym przykładzie. W tym przykładzie jest przeznaczony do wyróżnienia przypadki użycia, w którym leniwa ocena może spowodować problemy z wydajnością. Wynika to z każdej z umów nowy zbiór kart składa się z poprzednich rozmieszczenia. Przy użyciu leniwa ocena oznacza, że każda nowa konfiguracja slajdów składa się z oryginalnego slajdów, nawet wykonywania kodu, który skompilowany `startingDeck`. Dzięki któremu dużą ilość dodatkowej pracy. 

W praktyce niektóre algorytmy Uruchom znacznie lepsze, za pomocą eager oceny, a pozostałe — znacznie lepsze, za pomocą obliczanie z opóźnieniem. (Ogólnie rzecz biorąc, obliczanie z opóźnieniem jest dużo lepszym rozwiązaniem, gdy źródło danych jest oddzielnym procesie, takich jak aparat bazy danych. W takich przypadkach opóźnieniem umożliwia bardziej złożone zapytania, które można wykonać tylko jeden komunikację dwustronną proces bazy danych.) LINQ umożliwia zarówno z opóźnieniem i chętnie Zapoznamy oceny. Zmierz i wybrać najlepszy wybór.

## <a name="preparing-for-new-features"></a>Przygotowanie do nowych funkcji

Kod napisany w tym przykładzie to przykład tworzenia prostego prototypu, który wykonuje zadania. Jest to doskonały sposób eksplorowania obszar problemu, a dla wielu funkcji, może być najlepszym rozwiązaniem stałe. Już wykorzystywane *typy anonimowe* dla karty, a każda karta jest reprezentowany przez parametry.

*Typy anonimowe* mają wiele zalet produktywności. Nie trzeba zdefiniować klasę sobie, aby reprezentować pamięć masową. Kompilator generuje typ dla Ciebie. Typ wygenerowanego przez kompilator korzysta z wielu najlepszych rozwiązań dla obiektów danych proste. Ma ona *niezmienne*, co oznacza, że żaden z jej właściwości można zmienić po został skonstruowany. Typy anonimowe są wewnętrzne dla zestawu, więc nie są widoczne jako część publicznego interfejsu API dla tego zestawu. Typy anonimowe zawierają również przesłonięcia z `ToString()` metodę, która zwraca sformatowany ciąg z każdej wartości.

Typy anonimowe ma również wady. Nie mają nazw dostępnych, więc nie można go użyć jako wartości zwracane lub argumentów Można zauważyć, że używanym żadnych metod powyżej w te typy anonimowe są metody rodzajowe. Zastępowania metody `ToString()` może nie być ma więcej funkcji wzrostem aplikacji. 

W przykładzie użyto również ciągi, kolor i rangi każdej karty. Który jest dość Otwórz zakończone. System typów języka C# mogą pomóc nam w ulepszaniu lepszego kodu, wykorzystując `enum` typów w przypadku tych wartości.

Zacznij od kolory. Jest to idealny moment, aby użyć `enum`:

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

`Suits()` Metoda zmienia się również typ i implementację:

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

Następnie wykonaj tę samą zmianę o randze kart:

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

I metoda, która generuje je:

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

Jako jeden końcowy oczyszczania stwórzmy typu reprezentującego karty, zamiast polegania na typ anonimowy. Typy anonimowe to idealne rozwiązanie dla typów lokalna, lekki, ale w tym przykładzie karty gry jest jednym z głównych pojęć. Powinna ona konkretnego typu.

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

Ten typ korzysta *automatycznie implementowane właściwości tylko do odczytu* które są ustawiane w konstruktorze, a następnie nie może być modyfikowany. On również sprawia, że użycie [Interpolacja ciągów](../language-reference/tokens/interpolated.md) funkcja, która ułatwia formatowanie ciągów w danych wyjściowych.

Zaktualizuj zapytanie, które generuje początkowy slajdów, aby użyć nowego typu:

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

Skompiluj i uruchom ponownie. Dane wyjściowe są nieco bardziej przejrzyste i kod jest nieco bardziej oczywiste i można rozszerzyć, aby łatwiej.

## <a name="conclusion"></a>Wniosek

Ten przykład pokazuje niektórych metod LINQ, jak utworzyć swoje własne metody, które będą używane łatwo za pomocą LINQ włączone kodu. On również pokazuje różnice między obliczanie z opóźnieniem i chętnie Zapoznamy oraz wpływ, jaki decyzja może mieć na wydajność.

Omówiono nieco jeden magician techniki. Magicians Użyj faro shuffle, ponieważ może kontrolować, gdzie wszystkie karty przemieszcza się w talii kart. W niektórych wskazówki magician ma zachować karty na pokład członka grupy odbiorców i rozmieszcza kilka razy, wiedząc, gdzie przejdzie tej karty. Inne Iluzje wymagają talii ustawić w określony sposób. Magician ustawi slajdów, przed wykonaniem lewy. Następnie zostanie ona mieszania slajdów 5 razy przy użyciu zewnętrznego losowa. Na etapie ona pokazują, jak wygląda losowe slajdów, mieszania go 3 razy więcej i slajdów, ustaw dokładnie tak jak chce mieć.
