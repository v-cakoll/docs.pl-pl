---
title: Wprowadzenie do programowania funkcyjnego w F#
description: Poznaj podstawy programowania funkcyjnego w F#.
ms.date: 10/29/2018
ms.openlocfilehash: d4a9bb0cd826b41aca96e12e2bcb5aab80c18eb4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "25863841"
---
# <a name="introduction-to-functional-programming-in-f"></a>Wprowadzenie do programowania funkcyjnego w F# #

Programowanie funkcjonalne jest stylu programowania, która kładzie nacisk na korzystanie z funkcji i niezmienialnymi danymi. Jest wpisane programowania funkcjonalnego, podczas programowania funkcjonalnego jest połączony z typów statycznych, takich jak za pomocą F#. Ogólnie rzecz biorąc następujące pojęcia są wyróżniono w programowaniu funkcjonalności:

* Funkcje jako głównymi konstrukcjami, których używasz
* Wyrażeń, zamiast instrukcji
* Niezmienne wartości zmiennych
* Programowanie deklaratywne za pośrednictwem programowanie imperatywne

W tej serii przedstawimy pojęcia i wzorce w funkcjonalności programowania przy użyciu F#. Po drodze dowiesz się, niektóre F# zbyt.

## <a name="terminology"></a>Terminologia

Programowanie funkcjonalne, podobnie jak inne programowania paradygmatów jest powiązana z słownictwo, który ostatecznie trzeba będzie Dowiedz się więcej. Poniżej przedstawiono niektóre typowe terminy, zobaczysz cały czas:

* **Funkcja** — funkcja jest konstrukcja, która spowoduje wygenerowanie danych wyjściowych, gdy dane wejściowe. Więcej formalnie go _mapuje_ element z jednego zestawu do innego zestawu. Ta formalism zostało zniesione pod konkretny na wiele sposobów, zwłaszcza w przypadku korzystania z funkcji, które działają na zbiory danych. To najbardziej podstawowy (i ważne) pojęciem programowania funkcjonalnego. 
* **Wyrażenie** -wyrażenie jest konstrukcja w kodzie, który generuje wartość. W F#, ta wartość musi być powiązany lub jawnie ignorowane. Wyrażenie może być przypadku zastąpiony wywołania funkcji.
* **Czystość** -czystości to właściwość funkcji w taki sposób, że jego wartość zwracana jest zawsze taki sam, aby uzyskać te same argumenty i że jego oceny nie ma żadnych efektów ubocznych. Czystej funkcji zależy od całkowicie argumentów.
* **Przezroczystość referencyjną** -referencyjną przezroczystości jest właściwość wyrażeń taki sposób, że ich, można zastąpić swoje dane wyjściowe bez wywierania wpływu na zachowanie programu.
* **Niezmienność** -niezmienności oznacza wartość nie może być zmieniona w miejscu. Jest to w przeciwieństwie do zmiennych, które można zmienić w miejscu.

## <a name="examples"></a>Przykłady

W poniższych przykładach pokazano tych podstawowych założeń.

### <a name="functions"></a>Funkcje

Najbardziej typowe i podstawowe konstrukcję w programowania funkcjonalnego jest funkcją. Poniżej przedstawiono prosty funkcja, która dodaje 1 na liczbę całkowitą:

```fsharp
let addOne x = x + 1
```

Podpis jego typ jest następująca:

```fsharp
val addOne: x:int -> int
```

Podpis mogą być odczytywane jako "`addOne` akceptuje `int` o nazwie `x` i będzie generować `int`". Więcej formalnie `addOne` jest _mapowania_ wartość z liczby całkowite na liczby całkowite. `->` Token, oznacza to mapowanie. W F#, zwykle przyjrzymy się sygnatura funkcji, aby poznać jego przeznaczenie.

Dlatego jest podpis ważna W typizowanych programowania funkcjonalnego, implementacja funkcji jest często mniej istotne niż rzeczywisty typ podpisu! Fakt, `addOne` dodaje wartość od 1 do liczby całkowitej jest interesująca w czasie wykonywania, ale gdy są konstruowanie programu fakt, że akceptuje i zwraca `int` to, co informuje, jak faktycznie użyjesz tej funkcji. Ponadto, gdy funkcja poprawnie (względem jeho signatura typu), diagnozowanie problemów może odbywać się tylko w treści `addOne` funkcji. Jest to tempa za wpisane programowania funkcjonalnego.

### <a name="expressions"></a>Wyrażenia

Wyrażenia są konstrukcji, które obliczają do wartości. W przeciwieństwie do instrukcji, które wykonują akcję, można traktować wyrażeń wykonywanie akcji, która zapewnia ponownie wartość. Wyrażenia prawie zawsze są używane na rzecz instrukcji programowania funkcjonalnego.

Należy wziąć pod uwagę poprzednie funkcji `addOne`. Treść `addOne` to wyrażenie:

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

Jest to wynik tego wyrażenia, który definiuje typ wyniku `addOne` funkcji. Na przykład, wyrażenie, które tworzą tej funkcji można ją zmienić w taki sposób, na być innego typu, taką jak `string`:

```fsharp
let addOne x = x.ToString() + "1"
```

Podpis funkcji jest teraz:

```fsharp
val addOne: x:'a -> string
```

Od dowolnego typu w F# może mieć `ToString()` wywoływać w nim typ `x` wprowadzono ogólnego (o nazwie [automatyczna Generalizacja](../language-reference/generics/automatic-generalization.md)), a wynikowy typ to `string`.

Wyrażenia nie są po prostu treści funkcji. Może mieć wyrażenia, które generują wartość, których używasz w innym miejscu. Często jest `if`:

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

`if` Wyrażenia generują wartość o nazwie `result`. Należy zauważyć, że można pominąć `result` całości, dzięki czemu `if` wyrażenia treści z `addOneIfOdd` funkcji. Kluczową kwestią do zapamiętania informacji na temat wyrażeń jest, aby spowodować wartość.

Jest specjalnym typem `unit`, który jest używany, gdy nie ma nic do zwrócenia. Na przykład należy wziąć pod uwagę tej prostej funkcji:

```fsharp
let printString (str: string) =
    printfn "String is: %s" s
```

Podpis wygląda następująco:

```fsharp
val printString: str:string -> unit
```

`unit` Typu wskazuje, że nie ma rzeczywiste wartości zwracanych. Jest to przydatne, gdy masz procedurę, która musi "work" pomimo posiadanie żadnej wartości do zwrócenia w wyniku tej pracy.

To sharp natomiast do programowania imperatywnego, gdzie odpowiednik `if` konstrukcja jest instrukcją i produkcji wartości często odbywa się za pomocą mutacja zmiennych. Na przykład w C#, kod może być zapisany jako:

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

Warto zauważyć, że C# i innych językach w stylu języka C obsługuje [trójargumentowy wyrażenie](../../csharp/language-reference/operators/conditional-operator.md), co umożliwia oparte na wyrażeniach warunkowych programowania.

W programowaniu funkcjonalności, to rzadkość, aby mutować wartości za pomocą instrukcji. Mimo że w przypadku niektórych języków funkcjonalnych obsługuje oświadczenia i mutacji, nie jest często używa tych pojęć w programowania funkcjonalnego.

### <a name="pure-functions"></a>Czystych funkcji

Jak wspomniano wcześniej, czystej funkcji funkcji:

* Zawsze należy przeprowadzić ocenę na tę samą wartość dla tych samych danych wejściowych.
* Mieć żadnych efektów ubocznych.

Warto traktować funkcji matematycznych, w tym kontekście. W matematyce funkcje być zależne tylko od ich argumentów i nie ma żadnych efektów ubocznych. W funkcji matematycznych `f(x) = x + 1`, wartość `f(x)` zależy tylko od wartości `x`. Czystej funkcji w programowania funkcjonalnego jest taki sam sposób.

Podczas pisania czystą funkcję, funkcja musi być zależne tylko od argumentów i wykonuje żadnych działań, które powoduje efekt uboczny.

Oto przykład-czystej funkcji, ponieważ zależy od globalnej, modyfikowalnego stanu:

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

`addOneToValue` Funkcja jest wyraźnie oczyścić zanieczyszczony, ponieważ `value` można zmienić w dowolnym momencie, będzie mieć wartość inną niż 1. Tego wzorca w zależności od wartości globalnej jest unikać w programowania funkcjonalnego.

Oto inny przykład-czystą funkcję, bo efekt uboczny:

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

Chociaż ta funkcja nie zależy od wartości globalnej, zapisuje wartość `x` danych wyjściowych programu. Mimo że nie ma natury błąd w ten sposób, to oznacza, że funkcja nie jest czysty.

Usuwanie `printfn` Instrukcja finally sprawia, że funkcja czystego:

```fsharp
let addOneToValue x = x + 1
```

Chociaż ta funkcja nie jest z natury _lepsze_ niż poprzednia wersja z `printfn` instrukcji zagwarantować wszystkie ta funkcja nie jest zwrócona wartość. To wywołanie funkcji raz lub 1 MLD razy będą nadal powodować tak samo: po prostu produkcji wartości. To występowanie jest przydatne w programowania funkcjonalnego, zgodnie z jego oznacza, że wszelkie czystą funkcję referentially przezroczysty.

### <a name="referential-transparency"></a>Przezroczystość referencyjnej

Przezroczystość referencyjnej jest właściwością wyrażeń i funkcji. Wyrażenie do zachowania przejrzystości referentially musi mieć możliwość zastąpione ich wartość wynikowa bez zmiany zachowania tego programu. Wszystkie czyste funkcje są referentially przezroczyste.

Podobnie jak w przypadku czystych funkcji może być przydatne jest myśleć o przezroczystości referencyjną z punktu widzenia matematyczne. W wyrażeniu matematycznym `y = f(x)`, `f(x)` może być zastąpiony w wyniku funkcji i nadal będzie równa `y`. Ta zasada obowiązuje jednakowo do zachowania więzów programowania funkcjonalnego.

Należy wziąć pod uwagę podczas wywoływania uprzednio zdefiniowany `addOneIfOdd` funkcji dwa razy:

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result

let res1 = addOneIffOdd 1 // Produces 2
let res2 = addOneIffOdd 2 // Produces 2
```

Firma Microsoft można zastąpić każde wywołanie funkcji treści funkcji, zastępując argument `input` poszczególne wartości:

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result

let res1 =
    let result =
        if isOdd 1 then
            1 + 1
        else
            1

    result
let res2 =
    let result =
        if isOdd 2 then
            2 + 1
        else
            2

    result
```

Zarówno `res1` i `res2` mają taką samą wartość, tak jakby została wywołana funkcja wskazująca, że `addOneIfOdd` jest referentially niewidoczny!

Ponadto funkcja nie musi być czysty również być referentially przezroczysty. Należy wziąć pod uwagę poprzednią definicję `addOneTovalue`:

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

Każde wywołanie tej funkcji można również zastąpić jej treści i tych samych czynności nastąpi każdorazowo:

* Wartość przed dodaniem do, wydrukowaniu w danych wyjściowych
* Wartość długości od 1 do niego dodana

Podczas programowania w F#, jest często referencyjną przezroczystości, będący celem, a nie czystości. Jednak jest nadal dobrą praktyką, aby zapisać czystych funkcji, kiedy tylko można.

### <a name="immutability"></a>Niezmienność

Na koniec jest jedną z najbardziej podstawowe pojęcia programowania funkcjonalnego wpisane niezmienności. W F#, wszystkie wartości są niezmienne domyślnie. Oznacza to, że nie może być zmutowania na miejscu, chyba że wyraźnie oznaczyć je jako modyfikowalna.

W praktyce Praca z wartościami niezmiennymi oznacza, że zmienić swoje podejście do programowania z "Muszę coś zmienić", aby "należy utworzyć nową wartość".

Na przykład dodawanie 1 na wartość oznacza produkujących nową wartość, nie mutacja istniejącą grupę:

```fsharp
let value = 1
let secondValue = value + 1
```

W F#, poniższy kod wykonuje **nie** mutować `value` funkcji; zamiast tego wykonuje sprawdzanie równości:

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

Niektóre funkcjonalności języki programowania nie obsługują na wszystkich mutacji. W F#, jest obsługiwane, ale nie jest to domyślne zachowanie dla wartości.

Rozszerza tę koncepcję nawet bardziej struktur danych. W programowania funkcjonalnego, danymi niezmiennymi struktury, takich jak zestawy (i wielu innych) mają różne implementacje niż może być początkowo się spodziewać. Model coś, takie jak dodanie elementu do zestawu nie zmienia się zestaw, generuje _nowe_ zestawu przy użyciu wartości dodanej. Dzieje się w tle to często odbywa się przez to struktura różnych danych, która pozwala na efektywne śledzenia wartość tak, aby w efekcie można podać odpowiednie reprezentacja danych.

Ten styl pracy z wartościami i struktur danych ma krytyczne znaczenie, ponieważ wymusza można traktować każdej operacji, która modyfikuje coś tak, jakby tworzy nową wersję aplikacji. Umożliwi to np. równości i porównywalności zachować spójność w swoich programach.

## <a name="next-steps"></a>Następne kroki

Następna sekcja dokładnie obejmuje funkcje, eksplorowanie różne sposoby, można ich używać w programowania funkcjonalnego.

[Funkcje pierwszej klasy](first-class-functions.md) Eksploruje funkcje głęboko, przedstawiający sposób ich użycia w różnych kontekstach.

## <a name="further-reading"></a>Dalsze informacje

[Myśl funkcjonalnie](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) seria jest innym świetnym zasobem, aby dowiedzieć się więcej o programowania funkcjonalnego, za pomocą F#. Poruszono w nim podstawowe informacje na temat programowania funkcjonalnego w sposób pragmatyczne i łatwe do odczytania przy użyciu F# funkcji w celu zilustrowania koncepcji.