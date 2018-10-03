---
title: Statycznie rozwiązywane parametry typu (F#)
description: 'Dowiedz się, jak używać języka F # statystycznie rozpoznany typ parametru, który jest zastępowany rzeczywistym typem w czasie kompilacji, a nie w czasie wykonywania.'
ms.date: 05/16/2016
ms.openlocfilehash: 747917fef2746dcbf363ef4b717ace5e47229800
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032780"
---
# <a name="statically-resolved-type-parameters"></a>Statycznie rozwiązywane parametry typu

A *statystycznie rozpoznany typ parametru* jest parametrem typu, który jest zastępowany rzeczywistym typem w czasie kompilacji, a nie w czasie wykonywania. Są poprzedzone symbolem, daszek (^).

## <a name="syntax"></a>Składnia

```
ˆtype-parameter
```

## <a name="remarks"></a>Uwagi

W języku F # istnieją dwa odrębne rodzaje parametrów typu. Pierwszy rodzaj jest parametrem standardowym typu rodzajowego. Te są oznaczane apostrofem ('), podobnie jak w `'T` i `'U`. Są one równoważnymi parametrami typu rodzajowego w innych językach .NET Framework. Inny rodzaj jest statycznie rozwiązany i jest oznaczany symbolem daszka, podobnie jak w `^T` i `^U`.

Statycznie rozwiązywane parametry typu są szczególnie przydatne w połączeniu z ograniczeniami elementu członkowskiego, które są ograniczeniami, które pozwalają na określenie, że argument typu musi mieć danego członka lub członków, aby możliwe było użycie. Nie ma możliwości do utworzenia tego rodzaju ograniczenia przy użyciu parametru regularnego typu rodzajowego.

W poniższej tabeli podsumowano podobieństwa i różnice między dwoma rodzajami parametrów typu.

|Funkcja|Ogólny|Statycznie rozwiązane|
|-------|-------|-------------------|
|Składnia|`'T`, `'U`|`^T`, `^U`|
|Czas rozpoznawania nazw|Czas wykonywania|Czas kompilacji|
|Ograniczenia elementu członkowskiego|Nie można używać z ograniczeniami elementu członkowskiego.|Może być używany z ograniczeniami elementu członkowskiego.|
|Generowanie kodu|Typ (lub metoda) ze standardowymi parametrami ogólnego typu powoduje generowanie jednego ogólnego typu lub metody.|Wiele wystąpień typów i metod jest generowanych, po jednym dla każdego typu, który jest potrzebny.|
|Za pomocą typów|Może być stosowany na typach.|Nie może być stosowany na typach.|
|Za pomocą wbudowanej funkcji|Nie. Funkcja śródwierszowa nie mogą być parametryzowane ze standardowym parametrem typu ogólnego.|Tak. Statycznie rozwiązywane parametry typu nie można używać na funkcje lub metody, które nie są wbudowane.|

Wiele F # funkcji biblioteki podstawowej, zwłaszcza operatory, ma statycznie rozwiązywane parametry typu. Te funkcje i operatory są wbudowane i powodują skuteczne generowanie kodu do obliczeń numerycznych.

Wbudowane metody i funkcje, które używają operatorów lub innych funkcji, które mają statycznie rozwiązywane parametry typu, można również użyć parametrów typu statycznie rozpoznanych, samodzielnie. Często wnioskowanie o typie wnioskuje takie wbudowane funkcje, aby mieć statycznie rozwiązywane parametry typu. Poniższy przykład przedstawia definicję operatora która została wywnioskowana, ma parametr typu statycznie rozpoznanych.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

Rozpoznać typ `(+@)` opiera się na wykorzystaniu obu `(+)` i `(*)`, z którym spowodować, że wniosek typu wywnioskowuje ograniczenia Członkowskie na statycznie rozwiązywane parametry typu. Rozwiązany typ, jak pokazano w interpretera F # jest w następujący sposób.

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

Dane wyjściowe są następujące:

```
2
1.500000
```

Począwszy od F # 4.1, można również określić konkretny typ nazwy w podpisach parametrów typu statycznie rozpoznanych.  W poprzednich wersjach języka nazwę typu można wywnioskować faktycznie przez kompilator, ale faktycznie nie można określić w podpisie.  Począwszy od F # 4.1 możesz również określić konkretny typ nazwy w podpisach parametrów typu statycznie rozpoznanych. Oto przykład:

```fsharp
let inline konst x _ = x

type CFunctor() = 
    static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
    static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

    // default implementation of replace
    static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

    // call overridden replace if present
    static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
        ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a>Zobacz także

- [Typy ogólne](index.md)
- [Wnioskowanie o typie](../type-inference.md)
- [Automatyczna generalizacja](automatic-generalization.md)
- [Ograniczenia](constraints.md)
- [Funkcje śródwierszowe](../functions/inline-functions.md)
