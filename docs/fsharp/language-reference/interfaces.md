---
title: Interfejsy
description: Dowiedz się, jak F# interfejsy określają zestawy pokrewnych elementów członkowskich, które implementują innych klas.
ms.date: 05/16/2016
ms.openlocfilehash: 5b57769af6c05b83b3a112635033abf4efaca772
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645377"
---
# <a name="interfaces"></a>Interfejsy

*Interfejsy* określić zestawy pokrewnych elementów członkowskich, które implementują innych klas.

## <a name="syntax"></a>Składnia

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a>Uwagi

Deklaracje interfejsu przypominają deklaracji klasy, z tą różnicą, że żadne składowe są implementowane. Zamiast tego wszystkie elementy członkowskie są abstrakcyjne, wskazane przez słowo kluczowe `abstract`. Nie udostępniają treści metody metody abstrakcyjne. Jednak udostępnia domyślną implementację, umieszczając również oddzielne definicji elementu członkowskiego jako metoda wraz z `default` — słowo kluczowe. To jest odpowiednikiem tworzenie wirtualnej metody w klasie bazowej, w innych językach .NET. Metoda wirtualna może być zastąpiona w klasach, które implementują interfejs.

Wartość domyślna dostępu dla interfejsów `public`.

Użytkownik może opcjonalnie nazwij każdego parametru metody przy użyciu normalnych F# składni:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

W powyższych `ISprintable` przykład `Print` metoda ma jeden parametr typu `string` o nazwie `format`.

Istnieją dwa sposoby, aby zaimplementować interfejsów: przy użyciu wyrażeń obiektów i za pomocą typu klasy. W obu przypadkach wyrażenie typu lub obiektu klasy zawiera treści metod dla metody abstrakcyjne interfejsu. Implementacje są właściwe dla każdego typu, który implementuje interfejs. W związku z tym metod interfejsu w różnych typach może się różnić od siebie nawzajem.

Słowa kluczowe `interface` i `end`, które oznaczania początku i końca definicji, są opcjonalne, jeśli używasz składni lekkiej. Jeśli nie używasz tych słów kluczowych, kompilator próbuje rozpoznać, czy typ jest klasą lub interfejs, analizując konstrukcje, których używasz. Jeśli możesz definiować element członkowski lub inną składnię klasy, typ jest interpretowany jako klasa.

Styl kodowania platformy .NET jest rozpoczęcie wszystkie interfejsy z wielkiej litery `I`.

## <a name="implementing-interfaces-by-using-class-types"></a>Implementacja interfejsów przy użyciu typów klas

Można wdrożyć jeden lub więcej interfejsów w typie klasy przy użyciu `interface` — słowo kluczowe, nazwy interfejsu, a `with` — słowo kluczowe, a następnie definicji składowej interfejsu, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Implementacje interfejsu są dziedziczone, dzięki czemu nie trzeba ich ponownie wszystkie klasy pochodne.

## <a name="calling-interface-methods"></a>Wywoływanie metody interfejsu

Metody interfejsu może być wywoływana tylko za pośrednictwem interfejsu, a nie przy użyciu dowolnego obiektu typu, który implementuje interfejs. W związku z tym, może być konieczne rozszerzające typ interfejsu za pomocą `:>` operatora lub `upcast` operatora w celu wywołania tych metod.

Aby wywołać metodę interfejsu, w przypadku obiektu o typie `SomeClass`, należy najpierw rozszerzające obiektu do typu interfejsu, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Alternatywą jest do deklarowania metody dla obiektu tego upcasts i wywołuje metodę interfejsu, jak w poniższym przykładzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>Implementacja interfejsów przy użyciu wyrażeń obiektów

Wyrażenia obiektów umożliwiają krótki do implementacji interfejsu. Są one przydatne, gdy nie trzeba tworzyć nazwany typ, a Ty chcesz po prostu obiekt, który obsługuje metody interfejsu, bez żadnych dodatkowych metod. Wyrażenie obiektu to zilustrowane w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>Dziedziczenia interfejsu

Interfejsy mogą dziedziczyć jeden lub więcej podstawowych interfejsów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Wyrażenia obiektów](object-expressions.md)
- [Klasy](classes.md)
