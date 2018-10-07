---
title: Struktury (F#)
description: 'Dowiedz się więcej o F # struktury, typ obiektu compact, który jest często bardziej efektywne niż klasy dla typów z małą ilością danych i prostego zachowanie.'
ms.date: 05/16/2016
ms.openlocfilehash: 08af88132dda28883e246b94585ff4ed8bd2f16a
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845304"
---
# <a name="structures"></a>Struktury

A *struktury* jest typem obiektu compact, który może być bardziej efektywne niż klasę dla typów, które mają niewielką ilość danych i prostego zachowanie.

## <a name="syntax"></a>Składnia

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a>Uwagi

Struktury są *typy wartości*, co oznacza, że są one przechowywane bezpośrednio na stosie, lub gdy są one używane jako pola lub typ elementów tablicy, wbudowanego w obiekcie nadrzędnym. W odróżnieniu od klas i rekordy struktury mają semantykę przekazać przez wartość. Oznacza to, że są one przydatne głównie dla małych wartości zagregowanych danych, które są dostępne i często kopiowany.

W poprzedniej składni są wyświetlane dwie formy. Pierwszy jest składni lekkiej, ale mimo to często jest używana, ponieważ podczas korzystania `struct` i `end` słów kluczowych, można pominąć `StructAttribute` atrybut, który pojawia się w drugim formularzu. Można skrócić `StructAttribute` tylko `Struct`.

*-Definition elementów i-elementy członkowskie typu* w poprzedniej składni reprezentuje element członkowski deklaracje i definicje. Struktury mogą mieć konstruktorów i pola mutable i niezmienne i mogą deklarować elementów członkowskich i implementacje interfejsu. Aby uzyskać więcej informacji, zobacz [członków](members/index.md).

Struktury nie uczestniczą w dziedziczeniu, nie mogą zawierać `let` lub `do` powiązań i nie może rekursywnie zawierać pola własne typu z (mimo że zawierają one komórki odwołań, odwołujące się do ich własnych typu).

Ponieważ nie zezwalają na struktury `let` powiązania, należy zadeklarować pól w strukturach przy użyciu `val` — słowo kluczowe. `val` — Słowo kluczowe definiuje pola typu i jego typu, ale nie zezwala na inicjowanie. Zamiast tego `val` deklaracje są zainicjowana na zero lub wartość null. Z tego powodu struktur, które mają Konstruktor niejawne (czyli parametry, które zawierają zaraz po nazwie struktury w deklaracji) wymagają `val` deklaracje być oznaczona przy użyciu `DefaultValue` atrybutu. Struktury, które mają zdefiniowany Konstruktor nadal obsługuje inicjowania zero. W związku z tym `DefaultValue` atrybutu jest deklaracją, że takie wartość zero jest prawidłowy dla pola. Niejawne konstruktory dla struktury nie wykonuj żadnych akcji, ponieważ `let` i `do` powiązania nie są dozwolone w typie, ale wartości parametru dorozumiany Konstruktor przekazane są dostępne jako pola prywatne.

Jawnych konstruktorów może obejmować Inicjowanie wartości pól. Jeśli masz strukturę, która ma jawny Konstruktor, nadal obsługuje inicjowania zero; jednak nie użyto `DefaultValue` atrybutu na `val` deklaracji, ponieważ powoduje on konflikt z jawny Konstruktor. Aby uzyskać więcej informacji na temat `val` deklaracji, zobacz [pola jawne: `val` — słowo kluczowe](members/explicit-fields-the-val-keyword.md).

Atrybuty i modyfikatory dostępności są dozwolone w strukturach, a następnie wykonaj te same zasady, jak w przypadku innych typów. Aby uzyskać więcej informacji, zobacz [atrybuty](attributes.md) i [kontroli dostępu](access-control.md).

Poniższe przykłady kodu ilustrują definicji struktury.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>Struktury ByRefLike

Można zdefiniować własne struktur, które można stosować `byref`— semantyka, takich jak: zobacz [Zkratka](byrefs.md) Aby uzyskać więcej informacji. Jest to zrobić za pomocą <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> atrybutu:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` nie oznacza `Struct`. Zarówno musi być obecny w typie.

Element "`byref`— takich jak" struct w języku F # to typ wartości powiązanym ze stosu. Nigdy nie zostanie przydzielona na stosie zarządzanym. A `byref`— takie jak struktura jest przydatne w przypadku programowania o wysokiej wydajności, jak są wymuszane za pomocą zestawu silne testów o okresie istnienia i -capture. Dostępne są następujące reguły:

* One może służyć jako parametry funkcji, parametrów metody, zmienne lokalne, metoda zwraca wartość.
* Nie mogą one być statyczne lub wystąpieniami elementów członkowskich klasy lub struktury normalne.
* Nie można przechwycić według konstrukcji zamknięcia (`async` metod lub wyrażenia lambda).
* Nie mogą one służyć jako parametr ogólny.

Mimo że te reguły ograniczają bardzo silnie użycia, to zrobią do spełnienia obietnicy o wysokiej wydajności obliczeniowej w bezpieczny sposób.

## <a name="readonly-structs"></a>Struktur tylko do odczytu

Możesz dodawać adnotacje do struktury za pomocą <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> atrybutu. Na przykład:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly` nie oznacza `Struct`. Musisz dodać oba mieć `IsReadOnly` struktury.

Użyj tego atrybutu emituje metadane, umożliwiając F # i C#, aby traktować jako `inref<'T>` i `in ref`, odpowiednio.

Definiowanie wartości modyfikowalne wewnątrz struktury tylko do odczytu powoduje błąd.

## <a name="struct-records-and-discriminated-unions"></a>Rekordy struktury i związki dyskryminowane

Może reprezentować [rekordów](records.md) i [sumy rozłączne](discriminated-unions.md) jako struktury za pomocą `[<Struct>]` atrybutu.  Zobacz poszczególnymi artykułami, aby dowiedzieć się więcej.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Klasy](classes.md)
- [Rekordy](records.md)
- [Elementy członkowskie](members/index.md)
