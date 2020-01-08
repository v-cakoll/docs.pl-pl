---
title: Rozszerzenia typu
description: Dowiedz F# się, jak rozszerzenia typów umożliwiają dodawanie nowych elementów członkowskich do wcześniej zdefiniowanego typu obiektu.
ms.date: 11/04/2019
ms.openlocfilehash: 3e2c6971156bd562ed5d5428e6b7ffdc520c4cf5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341571"
---
# <a name="type-extensions"></a>Rozszerzenia typu

Rozszerzenia typu (nazywane również _powiększeniami_) są rodziną funkcji, które umożliwiają dodawanie nowych elementów członkowskich do wcześniej zdefiniowanego typu obiektu. Te trzy funkcje są następujące:

- Wewnętrzne rozszerzenia typów
- Opcjonalne rozszerzenia typu
- Metody rozszerzające

Każdy z nich może być używany w różnych scenariuszach i ma różne kompromisy.

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

## <a name="intrinsic-type-extensions"></a>Wewnętrzne rozszerzenia typów

Wewnętrzny typ wewnętrzny to rozszerzenie typu, które rozszerza typ zdefiniowany przez użytkownika.

Wewnętrzne rozszerzenia typu muszą być zdefiniowane w tym samym pliku **i** w tej samej przestrzeni nazw lub module co typ, który rozszerza. Wszystkie inne definicje spowodują, że są one [opcjonalnymi rozszerzeniami typów](type-extensions.md#optional-type-extensions).

Wewnętrzne rozszerzenia typów są czasami bardziej przejrzystym sposobem oddzielania funkcjonalności od deklaracji typu. Poniższy przykład pokazuje, jak zdefiniować rozszerzenie typu wewnętrznego:

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

Użycie rozszerzenia typu umożliwia rozdzielenie następujących elementów:

- Deklaracja typu `Variant`
- Funkcja drukowania klasy `Variant` w zależności od jej "kształtu"
- Sposób dostępu do funkcji drukowania przy użyciu notacji `.`w stylu obiektu

Jest to alternatywa dla definiowania wszystkiego jako elementu członkowskiego na `Variant`. Chociaż nie jest to jeszcze lepsze rozwiązanie, może to być przejrzysta reprezentacja funkcji w niektórych sytuacjach.

Wewnętrzne rozszerzenia typów są kompilowane jako elementy członkowskie typu, które rozszerzają i pojawiają się w typie, gdy typ jest rozpatrywany przez odbicie.

## <a name="optional-type-extensions"></a>Opcjonalne rozszerzenia typu

Opcjonalne rozszerzenie typu to rozszerzenie, które pojawia się poza oryginalnym modułem, przestrzenią nazw lub zestawem rozszerzanego typu.

Opcjonalne rozszerzenia typu są przydatne do rozszerzania typu, który nie został jeszcze zdefiniowany. Na przykład:

```fsharp
module Extensions

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for _ in 1 .. n -> x
        }
```

Teraz możesz uzyskiwać dostęp do `RepeatElements` tak, jakby był członkiem <xref:System.Collections.Generic.IEnumerable%601>, tak długo, jak moduł `Extensions` jest otwarty w zakresie, w którym pracujesz.

Rozszerzenia opcjonalne nie są wyświetlane na rozszerzonym typie, gdy są badane według odbicia. Rozszerzenia opcjonalne muszą znajdować się w modułach i są tylko w zakresie, gdy moduł, który zawiera rozszerzenie, jest otwarty lub jest w innym zakresie.

Opcjonalne elementy członkowskie rozszerzenia są kompilowane do statycznych elementów członkowskich, dla których wystąpienie obiektu jest przekazaniem niejawnie jako pierwszy parametr. Jednak działają tak, jakby były członkami wystąpienia lub statycznymi elementami członkowskimi zgodnie z ich deklarowaniem.

Opcjonalne elementy członkowskie rozszerzenia nie są również widoczne C# dla użytkowników ani Visual Basic. Mogą być używane tylko w innym F# kodzie.

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a>Ogólne ograniczenie wewnętrznych i opcjonalnych rozszerzeń typów

Istnieje możliwość zadeklarować rozszerzenie typu w typie ogólnym, w którym zmienna typu jest ograniczona. Wymóg polega na tym, że ograniczenie deklaracji rozszerzenia jest zgodne z ograniczeniem zadeklarowanego typu.

Jednak nawet wtedy, gdy ograniczenia są dopasowywane między zadeklarowanym typem a rozszerzeniem typu, można wywnioskować ograniczenie przez treść rozszerzonego elementu członkowskiego, który nakłada inny wymóg w parametrze typu niż zadeklarowany typ. Na przykład:

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

Nie ma możliwości uzyskania tego kodu do pracy z opcjonalnym rozszerzeniem typu:

- W takim przypadku element członkowski `Sum` ma inne ograniczenie dotyczące `'T` (`static member get_Zero` i `static member (+)`) niż zdefiniowane przez rozszerzenie typu.
- Modyfikowanie rozszerzenia typu tak samo, jak `Sum` nie będzie już zgodne ze zdefiniowanymi ograniczeniami `IEnumerable<'T>`.
- Zmiana `member this.Sum` na `member inline this.Sum` spowoduje wystąpienie błędu, że ograniczenia typu są niezgodne.

Wymagane są metody statyczne, które "zmiennoprzecinkowe miejsce" i mogą być prezentowane tak, jakby rozszerzali typ. Jest to miejsce, w którym metody rozszerzające stają się niezbędne.

## <a name="extension-methods"></a>Metody rozszerzające

Wreszcie metody rozszerzające (nazywane czasami "C# elementami członkowskimi rozszerzenia stylu") mogą być F# deklarowane jako statyczna metoda członkowska klasy.

Metody rozszerzające są przydatne w przypadku definiowania rozszerzeń dla typu ogólnego, który będzie ograniczać zmienną typu. Na przykład:

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

Gdy jest używany, ten kod będzie wyglądać tak, jakby `Sum` jest zdefiniowany w <xref:System.Collections.Generic.IEnumerable%601>, tak długo, jak `Extensions` został otwarty lub znajduje się w zakresie.

## <a name="other-remarks"></a>Inne uwagi

Rozszerzenia typu mają również następujące atrybuty:

- Dowolny typ, do którego można uzyskać dostęp, może zostać rozszerzony.
- Rozszerzenia typu wewnętrznego i opcjonalnego mogą definiować _dowolny_ typ elementu członkowskiego, a nie tylko metody. Możliwe jest również, że właściwości rozszerzenia są na przykład.
- Token `self-identifier` w [składni](type-extensions.md#syntax) reprezentuje wystąpienie wywoływanego typu, podobnie jak zwykłe elementy członkowskie.
- Rozszerzone elementy członkowskie mogą być statyczne lub składowe wystąpienia.
- Zmienne typu w rozszerzeniu typu muszą być zgodne z ograniczeniami zadeklarowanego typu.

Istnieją również następujące ograniczenia dotyczące rozszerzeń typów:

- Rozszerzenia typu nie obsługują metod wirtualnych ani abstrakcyjnych.
- Rozszerzenia typu nie obsługują metod zastępowania jako rozszerzeń.
- Rozszerzenia typu nie obsługują [statycznie rozpoznanych parametrów typu](./generics/statically-resolved-type-parameters.md).
- Opcjonalne rozszerzenia typu nie obsługują konstruktorów jako rozszerzeń.
- Nie można definiować rozszerzeń typu w [skrótach typu](type-abbreviations.md).
- Rozszerzenia typów nie są prawidłowe dla `byref<'T>` (chociaż można je zadeklarować).
- Rozszerzenia typów nie są prawidłowe dla atrybutów (chociaż mogą być deklarowane).
- Można zdefiniować rozszerzenia, które przeciążą inne metody o tej samej nazwie, F# ale kompilator daje preferencjom metody niewywołujące, jeśli istnieje niejednoznaczne wywołanie.

Jeśli istnieje wiele rozszerzeń typu wewnętrznego dla jednego typu, wszystkie elementy członkowskie muszą być unikatowe. W przypadku opcjonalnych rozszerzeń typu elementy członkowskie w różnych rozszerzeniach typu tego samego typu mogą mieć takie same nazwy. Błędy niejednoznaczne występują tylko wtedy, gdy kod klienta otwiera dwa różne zakresy, które definiują te same nazwy elementów członkowskich.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Elementy członkowskie](./members/index.md)
