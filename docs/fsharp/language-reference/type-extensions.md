---
title: Rozszerzenia typu (F#)
description: 'Dowiedz się, jak rozszerzeń typu F # zezwala na dodawanie nowych członków do typu obiektu zdefiniowanego wcześniej.'
ms.date: 07/20/2018
ms.openlocfilehash: 27238db1fd0803f62c32755fbc4ab7688f5c107e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855064"
---
# <a name="type-extensions"></a>Rozszerzenia typu

Rozszerzenia typu (nazywane również _rozszerzeniach_) to rodzina funkcji, które pozwalają na dodawanie nowych członków do typu obiektu zdefiniowanego wcześniej. Są trzy funkcje:

* Rozszerzeń typu wewnętrznego
* Opcjonalnych rozszerzeń typów
* Metody rozszerzenia

Każda mogą być używane w różnych scenariuszach i zawiera różne kompromisy.

## <a name="syntax"></a>Składnia

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [static] member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a>Rozszerzeń typu wewnętrznego

Rozszerzenie typu wewnętrznego jest rozszerzeniem typu, która rozszerza typ zdefiniowany przez użytkownika.

Rozszerzeń typu wewnętrznego musi być zdefiniowany w tym samym pliku **i** w tej samej przestrzeni nazw lub module jako typ, są one rozszerzanie. Inne definicji spowoduje ich trwa [opcjonalnych rozszerzeń typów](type-extensions.md#optional-type-extensions).

Rozszerzeń typu wewnętrznego są czasami bardziej przejrzysty sposób oddzielić funkcje od deklaracji typu. Poniższy przykład pokazuje jak zdefiniować rozszerzenie typu wewnętrznego:

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

Przy użyciu rozszerzenia typu umożliwia rozdzielenie każdego z następujących czynności:

* Deklaracja `Variant` typu
* Funkcje, aby wydrukować `Variant` klasy, w zależności od jego "kształt"
* Możliwość dostępu do funkcji drukowania stylem obiektu `.`— Notacja

Jest to alternatywa do definiowania wszystko jako członka na `Variant`. Chociaż nie jest z natury lepszym rozwiązaniem, może być oczyszczarki reprezentacja tych funkcji w niektórych sytuacjach.

Rozszerzeń typu wewnętrznego są kompilowane jako elementy członkowskie typu rozszerzania i są wyświetlane w typie, gdy typ jest badany przez odbicie.

## <a name="optional-type-extensions"></a>Opcjonalnych rozszerzeń typów

Opcjonalne rozszerzenie typu to rozszerzenie, które pojawia się poza oryginalnym module, przestrzeni nazw lub zestawu typ zostanie przedłużony.

Opcjonalnych rozszerzeń typów są przydatne do rozszerzania typu, który nie został zdefiniowany samodzielnie. Na przykład:

```fsharp
module Extensions

open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for i in 1 .. n do
                    yield x
        }
```

Teraz uzyskiwać dostęp do `RepeatElements` tak, jakby jest członkiem <xref:System.Collections.Generic.IEnumerable%601> tak długo, jak `Extensions` modułu jest otwarty w zakresie, w którym pracujesz.

Opcjonalne rozszerzenia nie są wyświetlane w typie rozszerzonym, gdy badany przez odbicie. Opcjonalne rozszerzenia muszą być w modułach i są one w zakresie wyłącznie wtedy, gdy moduł, który zawiera rozszerzenie jest otwarty lub jest w zakresie.

Opcjonalne elementy członkowskie rozszerzeń są kompilowane do statycznych elementów członkowskich, dla których wystąpienie obiektu jest przekazywane niejawnie jako pierwszy parametr. Jednak działają one tak, jakby były elementami członkowskimi wystąpień lub elementami statycznymi według tego jak są one zdeklarowane.

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a>Ogólne ograniczenia rozszerzeń typu wewnętrzne i opcjonalne

Istnieje możliwość zadeklarować rozszerzenie typu dla typu ogólnego, gdy zmienna typu jest ograniczone. Wymagane jest, że ograniczenie deklaracji rozszerzenia pasuje do ograniczenia zadeklarowanym typem.

Jednak nawet wtedy, gdy ograniczenia są dopasowywane między zadeklarowanym typem i rozszerzenie typu, jest możliwe ograniczenie był wywnioskowany przez jednostkę rozszerzonej elementu członkowskiego, która nakłada różnych wymagań dla parametru typu niż zadeklarowanym typem. Na przykład:

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

Nie istnieje sposób, aby otrzymać ten kod, aby pracować z opcjonalne rozszerzenie typu:

* Podobnie jak, `Sum` składowa ma różne ograniczenia `'T` (`static member get_Zero` i `static member (+)`) niż określa rozszerzenie typu.
* Modyfikowanie rozszerzenie typu mają ten sam ograniczenie jako `Sum` nie będzie już zgodny zdefiniowane ograniczenia na `IEnumerable<'T>`.
* Tworzenie, zmienianie członka do `member inline Sum` zapewni błąd niezgodność ograniczenia typu

Co to jest pożądane to metody statyczne, "float w miejscu", które może być prezentowana tak, jakby ich one rozszerzanie typu. Jest to, gdzie metody rozszerzenia stają się niezbędne.

## <a name="extension-methods"></a>Metody rozszerzenia

Na koniec metody rozszerzenia (nazywane czasem "C# styl elementy członkowskie rozszerzeń") może być zadeklarowana w F # jako metodę statyczną składową klasy.

Metody rozszerzenia są przydatne w przypadku gdy chcesz zdefiniować rozszerzenia dla typu ogólnego, który będzie ograniczać zmienna typu. Na przykład:

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

W przypadku tego kodu spowoduje, że będzie wyglądała, jakby `Sum` jest zdefiniowany w <xref:System.Collections.Generic.IEnumerable%601>, tak długo, jak `Extensions` został otwarty lub znajduje się w zakresie.

## <a name="other-remarks"></a>Inne uwagi

Rozszerzenia typu dostępne są także następujące atrybuty:

* Można rozszerzyć dowolny typ, który jest możliwy.
* Rozszerzenia typu wewnętrzne i opcjonalnych można zdefiniować _wszelkie_ typ elementu członkowskiego, nie tylko metody. Dlatego właściwości rozszerzenia są również możliwe, na przykład.
* `self-identifier` Tokenu w [składni](type-extensions.md#syntax) reprezentuje wystąpienie tego typu wywoływany, podobnie jak zwykłych członków.
* Rozszerzone członkowie mogą być statyczne lub wystąpieniami elementów członkowskich.
* Zmienne typu rozszerzenia typu musi być zgodna ograniczenia zadeklarowanym typem.

Dla typu rozszerzenia dostępne są także następujące ograniczenia:

* Typ rozszerzenia nie obsługują wirtualne ani abstrakcyjne.
* Rozszerzenia typu nie obsługują zastąpienie metody jako rozszerzenia.
* Typ rozszerzenia nie obsługują [statycznie rozwiązywanych parametrach typu](generics/statically-resolved-type-parameters.md).
* Opcjonalne rozszerzenia typu nie obsługują konstruktory jako rozszerzenia.
* Rozszerzenia typu nie może być zdefiniowana w [skróty typów](type-abbreviations.md).
* Rozszerzenia typu nie są prawidłowe dla `byref<'T>` (chociaż może być deklarowane).
* Rozszerzenia typu jest nieprawidłowa dla atrybutów (chociaż może być deklarowane).
* Można zdefiniować rozszerzenia, które przeciążać inne metody o tej samej nazwie, ale kompilator F # preferuje metod bez rozszerzeń w przypadku wywołania niejednoznacznego.

Na koniec Jeśli istnieje wiele rozszerzeń typu wewnętrznego dla jednego typu, wszystkie elementy członkowskie muszą być unikatowe. Dla opcjonalnych rozszerzeń typów elementy członkowskie w innych rozszerzeniach typów tego samego typu mogą mieć tej samej nazwy. Dwuznaczne błędy występują tylko wtedy, gdy kod klienta otwiera dwa różne zakresy definiujące te same nazwy składników.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Elementy członkowskie](members/index.md)
