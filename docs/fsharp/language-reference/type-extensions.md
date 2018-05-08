---
title: Rozszerzenia typu (F#)
description: 'Dowiedz się, jak rozszerzenia typu F # zezwala na dodawanie nowych elementów członkowskich do typu wcześniej zdefiniowanego obiektu.'
ms.date: 05/16/2016
ms.openlocfilehash: 2181745ea75894fbfe35d5522c130baaf1876455
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="type-extensions"></a>Rozszerzenia typu

Typ rozszerzenia umożliwiają dodawanie nowych elementów członkowskich do typu wcześniej zdefiniowanego obiektu.

## <a name="syntax"></a>Składnia

```fsharp
// Intrinsic extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]

// Optional extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]
```

## <a name="remarks"></a>Uwagi
Istnieją dwie formy rozszerzeń typu, które ma nieco inną składnię i zachowania. *Rozszerzenie wewnętrzne* to rozszerzenie, które pojawia się w tej samej przestrzeni nazw lub modułu, w tym samym pliku źródłowego, a w tym samym zestawie (plik DLL lub plik wykonywalny) jako rozszerzanego typu. *Opcjonalne rozszerzenie* to rozszerzenie, które znajduje się poza oryginalnego modułu, przestrzeni nazw lub zestawie rozszerzanego typu. Wewnętrzne rozszerzenia są wyświetlane na typ po typ się zbadana przez odbicie, ale opcjonalne rozszerzenia nie. Opcjonalne rozszerzenia musi być w modułach i są tylko w zakresie po otwarciu moduł, który zawiera rozszerzenia.

W poprzednich składni *typename* reprezentuje typ, który zostanie rozszerzone. Można ją rozszerzyć dowolnego typu, który jest dostępny, ale nazwa typu musi być nazwą typu rzeczywistego nie skrót typu. Można zdefiniować wiele elementów członkowskich w jeden typ rozszerzenia. *Własny identyfikator* reprezentuje wystąpienie obiektu wywoływany, tak jak w przypadku zwykłej elementów członkowskich.

`end` — Słowo kluczowe jest opcjonalna w lightweight — składnia.

Elementów członkowskich zdefiniowanych w rozszerzenia typu może służyć podobnie jak w innych elementach członkowskich w typie klasy. Podobnie jak inni członkowie ich być statyczne lub wystąpienia elementów członkowskich. Te metody są również znane jako *metody rozszerzenia*; właściwości są określane jako *właściwości rozszerzenia*i tak dalej. Rozszerzenie opcjonalne elementy członkowskie są kompilowane do statycznych elementów członkowskich, dla których wystąpienie obiektu jest przekazywany niejawnie jako pierwszym parametrem. Działają one jednak, tak jakby były elementów członkowskich wystąpień lub statycznych elementów członkowskich w zależności od sposobu są zadeklarowane. Elementy członkowskie rozszerzeń niejawne są uwzględnione jako elementy członkowskie tego typu i można go używać bez ograniczeń.

Metody rozszerzenia nie może być metody wirtualne lub abstrakcyjne. One przeciążenia innych metod o tej samej nazwie, ale kompilator daje preferencje metody bez rozszerzenia w przypadku niejednoznaczne wywołanie.

Jeśli istnieje wiele rozszerzeń typu wewnętrznej dla jednego typu, wszystkie elementy członkowskie muszą być unikatowe. Dla typu opcjonalne rozszerzenia elementy członkowskie w rozszerzeniach innego typu na ten sam typ mogą mieć tych samych nazwach. Niejednoznaczności błędów tylko wtedy, gdy kod klienta otwiera dwa różne zakresy, które definiują tej samej nazwy elementów członkowskich.

W poniższym przykładzie typu w module ma rozszerzenie typu wewnętrznego. Dla kodu klienta poza modułu rozszerzenia typu pojawia się jako zwykły element członkowski typu we wszystkich aspektach.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3701.fs)]

Rozszerzenia typu wewnętrznej służy do oddzielnych definicji typu na sekcje. Może to być przydatne w zarządzaniu definicje dużego typu, na przykład zachowanie oddzielny kod wygenerowany przez kompilator i napisanego kodu lub zgrupować kodu utworzone przez różne osoby lub skojarzone z różnych funkcji.

W poniższym przykładzie opcjonalny type — rozszerzenie rozszerza `System.Int32` typ z metody rozszerzenia `FromString` wywołującym statycznego elementu członkowskiego `Parse`. `testFromString` Metody pokazuje, że nowy element członkowski jest nazywany podobnie jak wszystkie wystąpienia elementu członkowskiego.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3702.fs)]

Podobnie jak wszystkie inne metody pojawi się nowy element członkowski wystąpienia `Int32` typu w funkcji IntelliSense, ale tylko wtedy, gdy moduł, który zawiera rozszerzenie jest otwarte lub w inny sposób w zakresie.

## <a name="generic-extension-methods"></a>Metody rozszerzenia w ogólnych
Przed F # 3.1, kompilator języka F # nie obsługuje języka C# — styl metody rozszerzenia zmienną typu ogólnego, typu tablicy, typ krotki lub typem funkcji języka F # jako parametr "this". 3.1 F # obsługuje korzystanie z tych elementów członkowskich rozszerzenia.

Na przykład w kodzie języka F # 3.1, można użyć metody rozszerzenia podpisów, które przypominają następującej składni w języku C#:

```csharp
static member Method<T>(this T input, T other)
```

Ta metoda jest szczególnie przydatne, gdy parametr typu ogólnego jest ograniczony. Ponadto można zadeklarować elementów członkowskich rozszerzenia następująco w kodzie języka F # i zdefiniować dodatkowe, semantycznie bogaty zestaw metod rozszerzenia. W języku F # zazwyczaj zdefiniowane jako w poniższym przykładzie przedstawiono elementy członkowskie rozszerzeń:

```fsharp
open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq { for x in xs do for i in 1 .. n do yield x }
```

Jednak dla typu ogólnego, zmienna typu może nie być ograniczone. Teraz można zadeklarować C# — styl Członkowskim rozszerzenia języka F # w celu obejścia tego ograniczenia. Łącząc tego rodzaju deklaracji przy użyciu funkcji wbudowanej języka F # można przedstawić ogólnego algorytmów jako elementy członkowskie rozszerzeń.

Należy wziąć pod uwagę następujące oświadczenie:

```fsharp
[<Extension>]
type ExtraCSharpStyleExtensionMethodsInFSharp () =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

Za pomocą tej deklaracji, można napisać kod, podobny do poniższego polecenia.

```fsharp
let listOfIntegers = [ 1 .. 100 ]
let listOfBigIntegers = [ 1I to 100I ]
let sum1 = listOfIntegers.Sum()
let sum2 = listOfBigIntegers.Sum()
```

W tym kodzie ten sam kod arytmetyczne ogólnego jest stosowany do listy dwa typy bez przeładowanie, definiując rozszerzenia jednego członka.


## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Elementy członkowskie](members/index.md)
