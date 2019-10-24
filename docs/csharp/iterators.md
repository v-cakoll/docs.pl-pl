---
title: Iteratory
description: Dowiedz się, jak używać wbudowanych C# iteratorów i jak tworzyć własne niestandardowe metody iteratora.
ms.date: 06/20/2016
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: c378ceb651eed7e7a3d8c738bd4b2b3cf7de2a0f
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773874"
---
# <a name="iterators"></a>Iteratory

Prawie każdy napisany program będzie musiał wykonać iterację w kolekcji. Napiszesz kod, który analizuje każdy element w kolekcji.

Utworzysz również metody iteratora, które są metodami, które tworzą iterator dla elementów tej klasy. Można ich używać w programie:

+ Wykonywanie akcji dla każdego elementu w kolekcji.
+ Wyliczanie kolekcji niestandardowej.
+ Rozszerzanie [LINQ](linq/index.md) lub innych bibliotek.
+ Tworzenie potoku danych, w którym dane są efektywnie przesyłane za pomocą metod iteratora.

C# Język zawiera funkcje obu tych scenariuszy. Ten artykuł zawiera omówienie tych funkcji.

Ten samouczek zawiera wiele kroków. Po każdym kroku można uruchomić aplikację i postępować według postępu. Możesz również [wyświetlić lub pobrać ukończony przykład](https://github.com/dotnet/samples/blob/master/csharp/iterators) dla tego tematu. Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="iterating-with-foreach"></a>Iteracja przy użyciu instrukcji foreach

Wyliczanie kolekcji jest proste: słowo kluczowe `foreach` wylicza kolekcję, wykonując osadzoną instrukcję dla każdego elementu w kolekcji:

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

To wszystko. Aby wykonać iterację całej zawartości kolekcji, należy uzyskać instrukcję `foreach`. Instrukcja `foreach` nie jest magiczna, chociaż. Opiera się on na dwóch ogólnych interfejsach zdefiniowanych w bibliotece .NET Core w celu wygenerowania kodu niezbędnego do iteracji kolekcji: `IEnumerable<T>` i `IEnumerator<T>`. Ten mechanizm został wyjaśniony bardziej szczegółowo poniżej.

Oba te interfejsy mają również nieogólne odpowiedniki: `IEnumerable` i `IEnumerator`. Wersje [Ogólne](programming-guide/generics/index.md) są preferowane w przypadku nowoczesnych kodów.

## <a name="enumeration-sources-with-iterator-methods"></a>Źródła wyliczenia z metodami iteratora

Kolejną doskonałą cechą języka C# jest możliwość tworzenia metod, które tworzą Źródło dla wyliczenia. Są one nazywane *metodami iteratora*. Metoda iteratora definiuje sposób generowania obiektów w sekwencji, gdy jest to wymagane. Do zdefiniowania metody iteratora służą `yield return` kontekstowe słowa kluczowe.

Można napisać tę metodę, aby utworzyć sekwencję liczb całkowitych z zakresu od 0 do 9:

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

W powyższym kodzie przedstawiono odrębne instrukcje `yield return`, aby zaznaczyć fakt, że w metodzie iteratora można użyć wielu instrukcji `yield return` dyskretnych.
Można (i często) używać innych konstrukcji językowych, aby uprościć kod metody iterator. Poniższa definicja metody daje dokładną sekwencję liczb:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

Nie musisz decydować o sobie. W razie potrzeby można mieć dowolną liczbę instrukcji `yield return`, aby spełnić wymagania metody:

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

Jest to podstawowa składnia. Rozważmy przykład Real świecie, w którym można napisać metodę iteratora. Wyobraź sobie, że jesteś w projekcie IoT, a czujniki urządzeń generują bardzo duży strumień danych. Aby uzyskać działanie dla danych, można napisać metodę, która próbuje pobrać każdy n-ty element danych. Ta mała Metoda iteratora jest jedną z lew:

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

Istnieje jedno ważne ograniczenie metod iteratora: nie można mieć instrukcji `return` i instrukcji `yield return` w tej samej metodzie. Następujące elementy nie zostaną skompilowane:

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

To ograniczenie zwykle nie jest problemem. Możesz użyć `yield return` w całej metodzie lub oddzielić oryginalną metodę na wiele metod, niektóre przy użyciu `return`, a niektóre przy użyciu `yield return`.

Ostatnią metodę można zmodyfikować nieco, aby użyć `yield return` wszędzie:

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

Czasami odpowiednia odpowiedź polega na podzieleniu metody iteratora na dwie różne metody. Jeden, który używa `return` i sekundy, który używa `yield return`. Rozważ sytuację, w której możesz chcieć zwrócić pustą kolekcję lub 5 pierwszych liczb nieparzystych na podstawie argumentu logicznego. Można napisać te dwie metody:

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

Zapoznaj się z powyższymi metodami. Najpierw używa standardowej instrukcji `return` do zwrócenia pustej kolekcji lub iteratora utworzonego przez drugą metodę. Druga metoda używa instrukcji `yield return`, aby utworzyć żądaną sekwencję.

## <a name="deeper-dive-into-foreach"></a>Dokładniejsze szczegółowe do `foreach`

Instrukcja `foreach` rozszerza się do standardowego idiom, który używa interfejsów `IEnumerable<T>` i `IEnumerator<T>` do iteracji dla wszystkich elementów kolekcji. Minimalizuje ona także błędy deweloperów, aby nie zarządzać zasobami.

Kompilator tłumaczy pętlę `foreach` przedstawioną w pierwszym przykładzie na coś podobnego do tej konstrukcji:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Powyższa konstrukcja reprezentuje kod wygenerowany przez C# kompilator w wersji 5 i nowszych. Przed wersjami 5 zmienna `item` miała inny zakres:

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

Ta zmiana została zmieniona, ponieważ wcześniejsze zachowanie może prowadzić do delikatnej i trudnej diagnostyki błędów obejmujących wyrażenia lambda. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).

Dokładny kod generowany przez kompilator jest nieco bardziej skomplikowany i obsługuje sytuacje, w których obiekt zwrócony przez `GetEnumerator()` implementuje interfejs `IDisposable`. Pełne rozszerzenie generuje kod bardziej podobny do tego:

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

Sposób, w jaki moduł wyliczający jest usuwany, zależy od właściwości typu `enumerator`. W ogólnym przypadku klauzula `finally` rozszerza się do:

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

Jeśli jednak typ `enumerator` jest typem zapieczętowanym i nie istnieje niejawna konwersja z typu `enumerator` do `IDisposable`, klauzula `finally` zostanie rozwinięta do pustego bloku:

```csharp
finally
{
}
```

Jeśli istnieje niejawna konwersja z typu `enumerator` do `IDisposable`, a `enumerator` jest typem wartości niedopuszczających wartości null, klauzula `finally` zostanie rozwinięta do:

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

Thankfully nie musisz zapamiętać wszystkich tych szczegółów. Instrukcja `foreach` obsługuje wszystkie te wszystkie szczegóły. Kompilator wygeneruje poprawny kod dla dowolnego z tych konstrukcji.
