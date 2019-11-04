---
title: Wprowadzenie do programowania funkcyjnego w F#
description: Poznaj podstawy programowania funkcjonalnego w programie F#.
ms.date: 10/29/2018
ms.openlocfilehash: e1a0edc61dbe13012c48e166d490e22ebc70d6a0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424710"
---
# <a name="introduction-to-functional-programming-in-f"></a>Wprowadzenie do programowania funkcjonalnego w języku F\#

Programowanie funkcjonalne to styl programowania, który kładzie nacisk na korzystanie z funkcji i niezmienne dane. Programowanie funkcjonalne o określonym typie jest połączone z typami statycznymi, na przykład z F#. Ogólnie rzecz biorąc, następujące koncepcje zostały wyróżnione w programowaniu funkcjonalnym:

* Działa jako konstrukcje podstawowe, z których korzystasz
* Wyrażenia zamiast instrukcji
* Niezmienne wartości w zmiennych
* Programowanie deklaratywne nad bezwzględnym programowaniem

W tej serii zapoznajesz koncepcje i wzorce w programowaniu funkcjonalnym F#przy użyciu programu. W ten sposób dowiesz się, jak F# również.

## <a name="terminology"></a>Terminologia

Programowanie funkcjonalne, takie jak inne odmiany programistyczne, zawiera słownictwo, które trzeba poznać. Poniżej przedstawiono niektóre typowe terminy, w których zobaczysz cały czas:

* **Function** -a funkcja jest konstrukcja, która spowoduje wygenerowanie danych wyjściowych po otrzymaniu danych wejściowych. Bardziej formalnie _mapuje_ element z jednego zestawu na inny. Ta formalność jest przekształcana w konkretną na wiele sposobów, szczególnie w przypadku korzystania z funkcji, które działają na kolekcjach danych. Jest to najbardziej podstawowe (i ważne) koncepcje programowania funkcjonalnego.
* **Wyrażenie** -wyrażenie jest konstrukcja w kodzie, która tworzy wartość. W F#programie ta wartość musi być powiązana lub jawnie ignorowana. Wyrażenie może być nieuproszczone zamieniane przez wywołanie funkcji.
* **Czystość** — czystość jest właściwością funkcji, w taki sposób, że jej wartość zwracana jest zawsze taka sama dla tych samych argumentów i że jej Ocena nie ma żadnych efektów ubocznych. Czysta funkcja zależy wyłącznie od jej argumentów.
* **Przezroczystość referencyjna** — przezroczystość referencyjna jest właściwością wyrażeń, które mogą zostać zastąpione danymi wyjściowymi bez wpływania na zachowanie programu.
* **Niezmienności** -niezmienności oznacza, że wartości nie można zmienić w miejscu. Jest to w przeciwieństwie do zmiennych, które mogą ulec zmianie w miejscu.

## <a name="examples"></a>Przykłady

W poniższych przykładach przedstawiono podstawowe pojęcia.

### <a name="functions"></a>Funkcje

Najbardziej typową i podstawową konstrukcją w programowaniu funkcjonalnym jest funkcja. Oto prosta funkcja, która dodaje 1 do liczby całkowitej:

```fsharp
let addOne x = x + 1
```

Podpis typu jest następujący:

```fsharp
val addOne: x:int -> int
```

Podpis może być odczytywany jako "`addOne` akceptuje `int` o nazwie `x` i spowoduje utworzenie `int`". Bardziej formalnie `addOne` _mapuje_ wartość z zestawu liczb całkowitych na zestaw liczb całkowitych. Token `->` oznacza to mapowanie. W F#programie zwykle można przyjrzeć się sygnatury funkcji w celu uzyskania sensu, co robi.

Dlatego dlaczego sygnatura jest ważna? W przypadku programowania w określonym zakresie implementacja funkcji jest często mniej ważna niż faktyczny podpis typu! Fakt, że `addOne` dodaje wartość 1 do liczby całkowitej, jest interesujący w czasie wykonywania, ale podczas konstruowania programu, fakt, że akceptuje, i zwraca `int`, wskazuje, jak faktycznie będzie używana ta funkcja. Ponadto po poprawnym użyciu tej funkcji (w odniesieniu do podpisu typu) diagnozowanie wszelkich problemów może odbywać się tylko w treści funkcji `addOne`. Jest to tempo związane z programowaniem funkcjonalności w określonym typie.

### <a name="expressions"></a>Wyrażenia

Wyrażenia są konstrukcjami, które są szacowane do wartości. W przeciwieństwie do instrukcji, które wykonują akcję, wyrażenia mogą być uważane za wykonywanie akcji, która zwraca wartość. Wyrażenia są prawie zawsze używane na korzyść instrukcji w programowaniu funkcjonalnym.

Rozważmy poprzednią funkcję, `addOne`. Treść `addOne` jest wyrażeniem:

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

Jest to wynik tego wyrażenia, który definiuje typ wyniku funkcji `addOne`. Na przykład, wyrażenie, które powoduje, że ta funkcja może zostać zmieniony na inny typ, taki jak `string`:

```fsharp
let addOne x = x.ToString() + "1"
```

Sygnatura funkcji jest teraz:

```fsharp
val addOne: x:'a -> string
```

Ponieważ dowolny typ w F# może mieć `ToString()` wywoływany, typ `x` został generyczny (nazywany [automatycznym generalizacją](../language-reference/generics/automatic-generalization.md)), a wynikowy typ to `string`.

Wyrażenia nie są tylko treścią funkcji. Można utworzyć wyrażenia, które tworzą wartość używaną w innym miejscu. Wspólny `if`:

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

Wyrażenie `if` generuje wartość o nazwie `result`. Należy pamiętać, że można pominąć `result` całkowicie, wprowadzając `if` wyrażenie treści funkcji `addOneIfOdd`. Kluczem do zapamiętania w przypadku wyrażeń jest utworzenie wartości.

Istnieje typ specjalny, `unit`, który jest używany, gdy nie ma niczego do zwrócenia. Rozważmy na przykład tę prostą funkcję:

```fsharp
let printString (str: string) =
    printfn "String is: %s" str
```

Podpis wygląda następująco:

```fsharp
val printString: str:string -> unit
```

Typ `unit` wskazuje, że nie jest zwracana wartość rzeczywista. Jest to przydatne, gdy masz procedurę, która musi "do pracy" mimo braku wartości do zwrócenia w wyniku tej pracy.

Jest to bardzo zróżnicowane dla bezwzględnego programowania, gdzie równoważna konstrukcja `if` jest instrukcją, a Tworzenie wartości jest często wykonywane z mutacją zmiennych. Na przykład w programie C#kod może być zapisany w następujący sposób:

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

Warto zauważyć, że C# a inne języki w stylu C obsługują [wyrażenie Trzyelementowy](../../csharp/language-reference/operators/conditional-operator.md), które umożliwia programowanie warunkowe oparte na wyrażeniach.

W programowaniu funkcjonalnym rzadko można przystąpić do wartości instrukcji. Chociaż niektóre języki funkcjonalne obsługują instrukcje i mutacje, nie jest powszechna możliwość używania tych koncepcji w programowaniu funkcjonalnym.

### <a name="pure-functions"></a>Czyste funkcje

Jak wspomniano wcześniej, czyste funkcje to funkcje, które:

* Należy zawsze oszacować tę samą wartość dla tych samych danych wejściowych.
* Nie ma żadnych efektów ubocznych.

Warto traktować funkcje matematyczne w tym kontekście. W przypadku matematyki funkcje są zależne od ich argumentów i nie mają żadnych efektów ubocznych. W funkcji matematycznej `f(x) = x + 1`wartość `f(x)` zależy od wartości `x`. Czyste funkcje w programowaniu funkcjonalnym są takie same.

Podczas pisania czystej funkcji, funkcja musi zależeć tylko od jej argumentów i nie wykonuje żadnej akcji, która skutkuje efektem ubocznym.

Oto przykład funkcji nieczystych, ponieważ zależy ona od globalnego, modyfikowalnego stanu:

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

Funkcja `addOneToValue` jest jasno nieczytelna, ponieważ `value` można zmienić w dowolnym momencie, aby miała inną wartość niż 1. Ten wzorzec w zależności od wartości globalnej należy unikać w programowaniu funkcjonalnym.

Oto inny przykład nieczystej funkcji, ponieważ wykonuje efekt uboczny:

```fsharp
let addOneToValue x =
    printfn "x is %d" x
    x + 1
```

Chociaż ta funkcja nie jest zależna od wartości globalnej, zapisuje wartość `x` w danych wyjściowych programu. Chociaż nie ma żadnego niewłaściwego w tym celu, oznacza to, że funkcja nie jest czysta. Jeśli inna część programu zależy od elementu zewnętrznego do programu, takiego jak bufor wyjściowy, wywołanie tej funkcji może mieć wpływ na tę inną część programu.

Usunięcie instrukcji `printfn` powoduje, że funkcja jest czysta:

```fsharp
let addOneToValue x = x + 1
```

Mimo że ta funkcja nie jest jeszcze _lepsza_ niż poprzednia wersja przy użyciu instrukcji `printfn`, gwarantuje, że cała ta funkcja zwraca wartość. Wywołanie tej funkcji dowolna liczba razy daje ten sam wynik: po prostu tworzy wartość. Przewidywalność podaną przez czystość to coś wielu programistów.

### <a name="immutability"></a>Niezmienności

Na koniec jednym z najważniejszych koncepcji programowania funkcjonalnego z typem jest niezmienności. W F#programie wszystkie wartości są domyślnie niezmienne. Oznacza to, że nie można ich zmodyfikować w miejscu, chyba że jawnie Oznacz je jako modyfikowalne.

W tym przypadku praca z niezmiennymi wartościami oznacza zmianę podejścia do programowania z, "muszę zmienić coś" na "chcę utworzyć nową wartość".

Na przykład dodanie 1 do wartości oznacza wygenerowanie nowej wartości, a nie mutację istniejącej:

```fsharp
let value = 1
let secondValue = value + 1
```

W F#programie Poniższy **kod nie powoduje mutacji** funkcji `value`; Zamiast tego sprawdza równość:

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

Niektóre funkcjonalne Języki programowania nie obsługują mutacji. W F#programie jest obsługiwane, ale nie jest to domyślne zachowanie dla wartości.

Koncepcja ta rozszerza jeszcze więcej do struktur danych. W programowaniu funkcjonalnym niezmienne struktury danych, takie jak zestawy (i wiele innych), mają inną implementację niż oczekiwano. Ze względu na to, że dodanie elementu do zestawu nie powoduje zmiany zestawu, tworzy _Nowy_ zestaw z dodaną wartością. W obszarze okładek jest to często realizowane przez inną strukturę danych, która umożliwia efektywne śledzenie wartości, dzięki czemu w wyniku tego można otrzymać odpowiednią reprezentację danych.

Ten styl pracy z wartościami i strukturami danych jest krytyczny, ponieważ Wymusza traktowanie dowolnej operacji, która modyfikuje coś, tak jakby tworzy nową wersję tego elementu. Pozwala to na takie jak równość i porównywalność w programach.

## <a name="next-steps"></a>Następne kroki

W następnej sekcji znajdują się dokładne funkcje, eksplorowanie różnych sposobów korzystania z nich w programowaniu funkcjonalnym.

[Funkcje pierwszej klasy](first-class-functions.md) eksplorują funkcje głęboko i pokazują, jak można ich używać w różnych kontekstach.

## <a name="further-reading"></a>Dalsze odczytywanie

Warto zastanowić się [, że szereg funkcjonalny](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) jest innym doskonałym zasobem F#, aby uzyskać informacje na temat programowania funkcjonalnego. Obejmuje ona podstawowe programowanie funkcjonalne w sposób pragmatyczny i łatwy do odczytu, przy użyciu F# funkcji do zilustrowania koncepcji.
