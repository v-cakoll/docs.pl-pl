---
title: Iteratory
description: Dowiedz się, jak używać wbudowanych iteratorów języka C# i jak tworzyć własne niestandardowe metody iteratorem.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 1933ecf83e9fa234f9b88c815d8ab527997c97f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399617"
---
# <a name="iterators"></a>Iteratory

Prawie każdy program, który piszesz, będzie musiał iterować nad kolekcją. Napiszesz kod, który sprawdza każdy element w kolekcji.

Utworzysz również metody iteratorem, które są metodami, które tworzą iterator dla elementów tej klasy. Mogą być używane do:

+ Wykonywanie akcji na każdym elemencie w kolekcji.
+ Wyliczanie kolekcji niestandardowej.
+ Rozszerzanie [LINQ](linq/index.md) lub innych bibliotek.
+ Tworzenie potoku danych, w którym dane są przepływać wydajnie za pomocą metod iteratorem.

Język Języka C# zawiera funkcje dla obu tych scenariuszy. Ten artykuł zawiera omówienie tych funkcji.

Ten samouczek ma wiele kroków. Po każdym kroku można uruchomić aplikację i zobaczyć postęp. Możesz również [wyświetlić lub pobrać wypełniony przykład](https://github.com/dotnet/samples/blob/master/csharp/iterators) dla tego tematu. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="iterating-with-foreach"></a>Iteracji z foreach

Wyliczanie kolekcji jest `foreach` proste: słowo kluczowe wylicza kolekcję, wykonując osadzoną instrukcję raz dla każdego elementu w kolekcji:

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

To już wszystko. Aby iterate całej zawartości kolekcji, instrukcja `foreach` jest wszystko, czego potrzebujesz. Stwierdzenie `foreach` to nie jest jednak magiczne. Opiera się na dwóch ogólnych interfejsach zdefiniowanych w bibliotece rdzenia .NET `IEnumerable<T>` w `IEnumerator<T>`celu wygenerowania kodu niezbędnego do iterate kolekcji: i . Mechanizm ten wyjaśniono bardziej szczegółowo poniżej.

Oba te interfejsy mają również odpowiedniki `IEnumerable` `IEnumerator`nierodzajowe: i . Wersje [ogólne](programming-guide/generics/index.md) są preferowane dla nowoczesnego kodu.

## <a name="enumeration-sources-with-iterator-methods"></a>Źródła wyliczania z metodami iteratorem

Inną wspaniałą funkcją języka C# umożliwia tworzenie metod, które tworzą źródło wyliczenia. Są one określane jako *metody iterator .* Metoda iteratora definiuje sposób generowania obiektów w sekwencji na żądanie. `yield return` Kontekstowe słowa kluczowe służy do definiowania metody iteratorego.

Można napisać tę metodę do produkcji sekwencji liczb całkowitych od 0 do 9:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    yield return 0;
    yield return 1;
    yield return 2;
    yield return 3;
    yield return 4;
    yield return 5;
    yield return 6;
    yield return 7;
    yield return 8;
    yield return 9;
}
```

Powyższy kod `yield return` przedstawia różne instrukcje, aby wyróżnić fakt, że można użyć wielu dyskretnych `yield return` instrukcji w metodzie sterytora.
Można (i często zrobić) używać innych konstrukcji języka, aby uprościć kod metody iteratora. Poniższa definicja metody daje dokładnie taką samą sekwencję liczb:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

Nie musisz decydować o jednym czy drugim. Możesz mieć tyle `yield return` instrukcji, ile jest to konieczne, aby zaspokoić potrzeby metody:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    index = 100;
    while (index < 110)
        yield return index++;
}
```

To jest podstawowa składnia. Rozważmy przykład świata rzeczywistego, w którym można napisać metodę iterator. Wyobraź sobie, że korzystasz z projektu IoT, a czujniki urządzeń generują bardzo duży strumień danych. Aby uzyskać wrażenie danych, można napisać metodę, która pobiera próbki co n-ty element danych. Ta mała metoda iterator robi sztuczkę:

```csharp
public static IEnumerable<T> Sample(this IEnumerable<T> sourceSequence, int interval)
{
    int index = 0;
    foreach (T item in sourceSequence)
    {
        if (index++ % interval == 0)
            yield return item;
    }
}
```

Istnieje jedno ważne ograniczenie metod iteratorem: nie można `return` mieć `yield return` zarówno instrukcji, jak i instrukcji w tej samej metodzie. Następujące nie skompiluje:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    // generates a compile time error:
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;
}
```

To ograniczenie zwykle nie stanowi problemu. Masz do wyboru użycie `yield return` całej metody lub oddzielenie oryginalnej metody na `return`wiele metod, `yield return`niektóre przy użyciu , a niektóre przy użyciu .

Możesz nieco zmodyfikować ostatnią `yield return` metodę, aby użyć wszędzie:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```

Czasami właściwą odpowiedzią jest podzielenie metody iteratorego na dwie różne metody. Taki, `return`który używa , `yield return`a drugi, który używa . Rozważmy sytuację, w której można zwrócić pustą kolekcję lub pierwszych 5 liczb nieparzystych na podstawie argumentu logicznego. Można napisać, że jak te dwie metody:

```csharp
public IEnumerable<int> GetSingleDigitOddNumbers(bool getCollection)
{
    if (getCollection == false)
        return new int[0];
    else
        return IteratorMethod();
}

private IEnumerable<int> IteratorMethod()
{
    int index = 0;
    while (index < 10)
    {
        if (index % 2 == 1)
            yield return index;
        index++;
    }
}
```

Spójrz na powyższe metody. Pierwszy używa standardowej `return` instrukcji, aby zwrócić puste kolekcji lub iterator utworzony przez drugą metodę. Druga metoda używa `yield return` instrukcji do tworzenia żądanesekwencji.

## <a name="deeper-dive-into-foreach"></a>Głębiej zanurz się w`foreach`

Instrukcja `foreach` rozszerza się na idiom `IEnumerable<T>` standardowy, który używa i `IEnumerator<T>` interfejsów do itetencji we wszystkich elementach kolekcji. Minimalizuje również błędy, które deweloperzy popełniają, nie właściwie zarządzając zasobami.

Kompilator tłumaczy `foreach` pętlę pokazaną w pierwszym przykładzie na coś podobnego do tej konstrukcji:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Powyższa konstrukcja reprezentuje kod generowany przez kompilator C# w wersji 5 i powyżej. Przed wersją 5 `item` zmienna miała inny zakres:

```csharp
// C# versions 1 through 4:
IEnumerator<int> enumerator = collection.GetEnumerator();
int item = default(int);
while (enumerator.MoveNext())
{
    item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Zostało to zmienione, ponieważ wcześniejsze zachowanie może prowadzić do subtelnych i trudnych do zdiagnozowania błędów z udziałem wyrażeń lambda. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [Wyrażenia Lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md).

Dokładny kod generowany przez kompilator jest nieco bardziej skomplikowane i obsługuje `GetEnumerator()` sytuacje, `IDisposable` w których obiekt zwracany przez implementuje interfejs. Pełne rozszerzenie generuje kod bardziej podobny do tego:

```csharp
{
    var enumerator = collection.GetEnumerator();
    try
    {
        while (enumerator.MoveNext())
        {
            var item = enumerator.Current;
            Console.WriteLine(item.ToString());
        }
    } finally
    {
        // dispose of enumerator.
    }
}
```

Sposób, w jaki wyliczacz jest usuwany, zależy od `enumerator`charakterystyki typu . W ogólnym przypadku `finally` klauzula rozszerza się na:

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

Jednakże jeśli typ `enumerator` jest typ zapieczętowany i nie ma niejawne konwersji z typu `enumerator` do `IDisposable`, klauzula `finally` rozszerza się do pustego bloku:

```csharp
finally
{
}
```

Jeśli istnieje niejawna konwersja `enumerator` `IDisposable`z `enumerator` typu do , i jest `finally` typem wartości niepodlegających null, klauzula rozszerza się na:

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

Na szczęście nie musisz pamiętać o tych wszystkich szczegółach. Oświadczenie `foreach` obsługuje wszystkie te niuanse dla Ciebie. Kompilator wygeneruje poprawny kod dla dowolnej z tych konstrukcji.
