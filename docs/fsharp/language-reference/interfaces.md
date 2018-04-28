---
title: Interfejsy (F#)
description: 'Dowiedz się, jak F # interfejsy określić zestawy pokrewnych elementów członkowskich, które implementują innych klas.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: fa299a7e37d4e1e3800a02bf5a77831db9146daf
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="interfaces"></a>Interfejsy

*Interfejsy* określić zestawy pokrewnych elementów członkowskich, które implementują innych klas.

## <a name="syntax"></a>Składnia

```fsharp
// Interface declaration:
[ attributes ]
type interface-name =
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
Deklaracji interfejsów przypominać deklaracji klasy, z wyjątkiem tego, czy nie elementy członkowskie są wykonywane. Zamiast tego, wszystkie elementy członkowskie są abstrakcyjnego, wskazywany przez słowo kluczowe `abstract`. Dla metody abstrakcyjne nie podawaj treści metody. Jednak udostępnia domyślną implementację dołączenie oddzielnych definicji elementu członkowskiego jako metoda razem z `default` — słowo kluczowe. W ten sposób jest odpowiednikiem tworzenia wirtualnej metody w klasie podstawowej w innych językach .NET. Metoda wirtualna może zostać przesłonięta klas implementujących interfejs.

Każdy parametr metody można opcjonalnie nadaj nazwę przy użyciu normalnego F # składni:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

W powyższych `ISprintable` przykład `Print` metoda ma jeden parametr typu `string` o nazwie `format`.

Istnieją dwa sposoby implementować interfejsów: przy użyciu wyrażeń obiektów i przy użyciu typu klasy. W obu przypadkach wyrażenie typu lub obiekt klasy zawiera treść metody dla metody abstrakcyjne interfejsu. Implementacje są specyficzne dla każdego typu, który implementuje interfejs. W związku z tym metody interfejsu w różnych typów mogą się różnić od siebie.

Słowa kluczowe `interface` i `end`, którego oznaczenie początek i koniec definicji, są opcjonalne, gdy używasz lightweight — składnia. Jeśli nie używasz słowa kluczowe, kompilator próbuje rozpoznać, czy typ jest klasą lub interfejsem, analizując konstrukcje, których używasz. Jeśli zdefiniować elementu członkowskiego lub użyj składni inne klasy, typ jest interpretowana jako klasa.

Styl kodowania platformy .NET jest rozpoczęcie wszystkie interfejsy z wielką `I`.


## <a name="implementing-interfaces-by-using-class-types"></a>Implementowanie interfejsów przy użyciu typu klasy
Można wdrożyć jeden lub więcej interfejsów w typie klasy przy użyciu `interface` — słowo kluczowe, nazwę interfejsu i `with` — słowo kluczowe, a następnie definicji elementu członkowskiego interfejsu, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Implementacje interfejsu są dziedziczone, więc nie trzeba ich reimplement żadnych klas pochodnych.


## <a name="calling-interface-methods"></a>Wywołanie metody interfejsu
Metody interfejsu można wywołać tylko za pośrednictwem interfejsu, nie za pomocą dowolnego obiektu typu, który implementuje interfejs. W związku z tym może być konieczne rozszerzające typ interfejsu za pomocą `:>` operator lub `upcast` operatora w celu wywołania tych metod.

Aby wywołać metodę interfejsu, gdy obiekt typu `SomeClass`, należy najpierw rozszerzające obiektu na typ interfejsu, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Alternatywą jest Zadeklaruj metodę dla obiektu z tym upcasts i wywołuje metodę interfejsu, jak w poniższym przykładzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]
    
## <a name="implementing-interfaces-by-using-object-expressions"></a>Implementowanie interfejsów przy użyciu wyrażeń obiektów
Wyrażenia obiektów podaj krótki sposób implementowania interfejsu. Są one przydatne, gdy jest konieczne tworzenie typu nazwanego, i chcesz obiekt, który obsługuje metod interfejsu, bez żadnych dodatkowych metod. Poniższy kod przedstawia wyrażenie obiektu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]
    
## <a name="interface-inheritance"></a>Dziedziczenie — interfejs
Interfejsy może dziedziczyć z jednego lub więcej interfejsach podstawowych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]
    
## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Wyrażenia obiektów](object-expressions.md)

[Klasy](classes.md)
