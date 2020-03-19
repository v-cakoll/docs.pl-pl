---
title: Struktury
description: Dowiedz się więcej o Strukturze F#, typ obiektu kompaktowego często bardziej wydajne niż klasy dla typów z niewielką ilością danych i proste zachowanie.
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400282"
---
# <a name="structures"></a>Struktury

*Struktura* jest typem obiektu kompaktowego, który może być bardziej efektywne niż klasy dla typów, które mają niewielką ilość danych i proste zachowanie.

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

Struktury są *typy wartości*, co oznacza, że są one przechowywane bezpośrednio na stosie lub, gdy są one używane jako pola lub elementy tablicy, w wierszu typu nadrzędnego. W przeciwieństwie do klas i rekordów struktury mają semantykę przekazywania według wartości. Oznacza to, że są one przydatne głównie dla małych agregatów danych, które są często dostępne i kopiowane.

W poprzedniej składni wyświetlane są dwie formy. Pierwszym z nich nie jest składnia lekka, ale mimo `struct` to `end` jest często używany, `StructAttribute` ponieważ podczas korzystania z i słów kluczowych, można pominąć atrybut, który pojawia się w drugim formularzu. Możesz `StructAttribute` skrócić do po `Struct`prostu .

*Typ-definition-elements-and-members* w poprzedniej składni reprezentuje deklaracje elementów członkowskich i definicje. Struktury mogą mieć konstruktorów i pola zmienne i niezmienne i mogą deklarować implementacje członków i interfejsu. Aby uzyskać więcej informacji, zobacz [Członkowie](./members/index.md).

Struktury nie mogą uczestniczyć w `let` `do` dziedziczeniu, nie mogą zawierać ani powiązać i nie mogą zawierać cyklicznie pól własnego typu (chociaż mogą zawierać komórki referencyjne, które odwołują się do własnego typu).

Ponieważ struktury nie `let` zezwalają na powiązania, należy zadeklarować `val` pola w strukturach przy użyciu słowa kluczowego. Słowo `val` kluczowe definiuje pole i jego typ, ale nie zezwala na inicjowanie. Zamiast `val` tego deklaracje są inicjowane do zera lub null. Z tego powodu struktury, które mają niejawny konstruktor (czyli parametry, które są podane `val` bezpośrednio po nazwie struktury w `DefaultValue` deklaracji) wymagają, aby deklaracje były adnotowane z atrybutem. Struktury, które mają zdefiniowany konstruktor nadal obsługują zero-inicjowania. W związku `DefaultValue` z tym atrybut jest deklaracją, że taka wartość zero jest prawidłowa dla pola. Niejawnych konstruktorów dla struktur nie `let` `do` wykonują żadnych akcji, ponieważ i powiązania nie są dozwolone na typ, ale niejawne wartości parametrów konstruktora przekazywane są dostępne jako pola prywatne.

Jawne konstruktory mogą obejmować inicjowanie wartości pól. Gdy masz strukturę, która ma jawny konstruktora, nadal obsługuje zero-inicjowania; jednak nie należy używać `DefaultValue` atrybutu `val` na deklaracje, ponieważ jest w konflikcie z konstruktora jawnego. Aby uzyskać `val` więcej informacji o deklaracjach, zobacz [Jawne pola: `val` Słowo kluczowe](./members/explicit-fields-the-val-keyword.md).

Atrybuty i modyfikatory ułatwień dostępu są dozwolone w strukturach i postępuj zgodnie z tymi samymi regułami, co w przypadku innych typów. Aby uzyskać więcej informacji, zobacz [Atrybuty](attributes.md) i [kontrola dostępu](access-control.md).

Poniższe przykłady kodu ilustrują definicje struktury.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>Struktury ByRefLike

Można zdefiniować własne struktury, które mogą `byref`przylegać do semantyki -like: zobacz [Byrefs](byrefs.md) aby uzyskać więcej informacji. Odbywa się to <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> za pomocą atrybutu:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`nie oznacza `Struct`. Oba muszą być obecne na typie.

Struktura`byref`"-like" w języku F# jest typem wartości powiązanym ze stosem. Nigdy nie jest przydzielany na zarządzanym stercie. Struktura `byref`-like jest przydatna w programowaniu o wysokiej wydajności, ponieważ jest wymuszana z zestawem silnych kontroli dotyczących okresu istnienia i braku przechwytywania. Zasady są następujące:

- Mogą być używane jako parametry funkcji, parametry metody, zmienne lokalne, zwraca metoda.
- Nie mogą być statyczne lub wystąpienia elementów członkowskich klasy lub normalnej struktury.
- Nie mogą być przechwytywane`async` przez dowolną konstrukcję zamknięcia (metody lub wyrażenia lambda).
- Nie można ich używać jako parametru ogólnego.

Chociaż te reguły bardzo silnie ograniczają użycie, robią to, aby spełnić obietnicę obliczeń o wysokiej wydajności w bezpieczny sposób.

## <a name="readonly-structs"></a>Struktury tylko do odczytu

Można adnotować struktury z <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> atrybutem. Przykład:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly`nie oznacza `Struct`. Należy dodać oba, `IsReadOnly` aby mieć strukturę.

Użycie tego atrybutu emituje metadane pozwalając F# i `inref<'T>` C# wiedzieć, aby traktować go jako i `in ref`, odpowiednio.

Definiowanie wartości zmiennej wewnątrz struktury tylko do odczytu powoduje błąd.

## <a name="struct-records-and-discriminated-unions"></a>Ewidencja struktur i związki dyskryminowane

Można reprezentować [rekordy](records.md) i [związki dyskryminowane](discriminated-unions.md) jako struktury z atrybutem. `[<Struct>]`  Zobacz każdy artykuł, aby dowiedzieć się więcej.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka F#](index.md)
- [Klasy](classes.md)
- [Rekordy](records.md)
- [Elementy członkowskie](./members/index.md)
