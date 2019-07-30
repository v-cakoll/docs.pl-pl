---
title: Interfejsy
description: Dowiedz F# się, jak interfejsy określają zestawy powiązanych elementów członkowskich, które są implementowane przez inne klasy.
ms.date: 05/16/2016
ms.openlocfilehash: 8f054a668ad0fbc2453a45883e8052471280eca3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627649"
---
# <a name="interfaces"></a>Interfejsy

*Interfejsy* określają zestawy powiązanych członków, które są implementowane przez inne klasy.

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

Deklaracje interfejsów przypominają deklaracje klas, z tą różnicą, że żaden element członkowski nie jest zaimplementowany. Zamiast tego wszystkie elementy członkowskie są abstrakcyjne, zgodnie ze wskazaniem `abstract`słowa kluczowego. Nie udostępniamy treści metody dla metod abstrakcyjnych. Można jednak podać domyślną implementację, uwzględniając także odrębną definicję elementu członkowskiego jako metodę razem ze `default` słowem kluczowym. Jest to równoznaczne z tworzeniem metody wirtualnej w klasie bazowej w innych językach .NET. Taka metoda wirtualna może zostać przesłonięta w klasach, które implementują interfejs.

Domyślnymi ułatwieniami dostępu dla `public`interfejsów są.

Opcjonalnie możesz nadać każdemu parametrowi metody nazwę przy użyciu F# standardowej składni:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

W powyższym `ISprintable` przykładzie `Print` Metoda ma jeden parametr typu `string` o nazwie `format`.

Istnieją dwa sposoby implementacji interfejsów: przy użyciu wyrażeń obiektów i typów klas. W obu przypadkach typ klasy lub wyrażenie obiektu zawiera treść metody dla abstrakcyjnych metod interfejsu. Implementacje są specyficzne dla każdego typu, który implementuje interfejs. W związku z tym metody interfejsu dla różnych typów mogą się różnić od siebie.

Słowa kluczowe `interface` i `end`, które oznaczają początek i koniec definicji, są opcjonalne w przypadku używania lekkiej składni. Jeśli nie używasz tych słów kluczowych, kompilator próbuje określić, czy typ jest klasą, czy interfejsem, analizując używane konstrukcje. Jeśli zdefiniujesz element członkowski lub użyjesz innej składni klasy, typ jest interpretowany jako Klasa.

Styl kodowania .NET polega na rozpoczęciu wszystkich interfejsów z stolicą `I`.

## <a name="implementing-interfaces-by-using-class-types"></a>Implementowanie interfejsów przy użyciu typów klas

Można zaimplementować jeden lub więcej interfejsów w typie klasy za pomocą `interface` słowa kluczowego, nazwy interfejsu `with` i słowa kluczowego, a następnie definicji elementu członkowskiego interfejsu, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Implementacje interfejsu są dziedziczone, więc wszystkie klasy pochodne nie muszą ponownie wdrażać.

## <a name="calling-interface-methods"></a>Wywoływanie metod interfejsu

Metody interfejsu można wywoływać tylko za pomocą interfejsu, a nie za pomocą dowolnego obiektu typu, który implementuje interfejs. W ten sposób może być konieczne przerzutowanie na typ interfejsu za pomocą `:>` operatora `upcast` lub operatora w celu wywołania tych metod.

Aby wywołać metodę interfejsu, gdy masz obiekt typu `SomeClass`, należy przerzutować obiekt na typ interfejsu, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Alternatywą jest zadeklarowanie metody na obiekcie, który rzutuje i wywołuje metodę interfejsu, jak w poniższym przykładzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>Implementowanie interfejsów przy użyciu wyrażeń obiektów

Wyrażenia obiektów zapewniają krótki sposób implementacji interfejsu. Są one przydatne, gdy nie trzeba tworzyć nazwanego typu, a ty chcesz tylko obiekt obsługujący metody interfejsu, bez żadnych dodatkowych metod. Wyrażenie obiektu jest zilustrowane w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>Dziedziczenie interfejsu

Interfejsy mogą dziedziczyć z jednego lub kilku interfejsów podstawowych.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Wyrażenia obiektów](object-expressions.md)
- [Klasy](classes.md)
