---
title: Statycznie rozwiązywane parametry typu
description: Dowiedz się, jak F# używać statycznie rozpoznanego parametru typu, który jest zastępowany rzeczywistym typem w czasie kompilacji, a nie w czasie wykonywania.
ms.date: 05/16/2016
ms.openlocfilehash: 43ed79b6e5f43a499a27b05e26472b021c455e44
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630582"
---
# <a name="statically-resolved-type-parameters"></a>Statycznie rozwiązywane parametry typu

*Statycznie rozpoznany parametr typu* jest parametrem typu, który jest zastępowany rzeczywistym typem w czasie kompilacji, a nie w czasie wykonywania. Są poprzedzone symbolem karetki (^).

## <a name="syntax"></a>Składnia

```
ˆtype-parameter
```

## <a name="remarks"></a>Uwagi

W F# języku istnieją dwa odrębne rodzaje parametrów typu. Pierwszy rodzaj jest standardowym parametrem typu ogólnego. Są one wskazywane przez apostrof ('), jak w `'T` i `'U`. Są one odpowiednikami parametrów typu ogólnego w innych językach .NET Framework. Inny rodzaj jest statycznie rozpoznany i jest wskazywany przez symbol karetki, jak w `^T` i `^U`.

Statycznie rozpoznane parametry typu są szczególnie przydatne w połączeniu z ograniczeniami elementu członkowskiego, które są ograniczeniami, które umożliwiają określenie, że argument typu musi mieć określonego członka lub członków, aby można go było używać. Nie ma możliwości utworzenia tego rodzaju ograniczenia przy użyciu zwykłego parametru typu ogólnego.

W poniższej tabeli zestawiono podobieństwa i różnice między dwoma rodzajami parametrów typu.

|Funkcja|Ogólny|Statycznie rozwiązane|
|-------|-------|-------------------|
|Składnia|`'T`, `'U`|`^T`, `^U`|
|Czas rozwiązania|W czasie wykonywania|Czas kompilacji|
|Ograniczenia elementu członkowskiego|Nie można używać z ograniczeniami elementu członkowskiego.|Może być używany z ograniczeniami elementu członkowskiego.|
|Generowanie kodu|Typ (lub metoda) ze standardowymi parametrami typu ogólnego skutkuje generowaniem pojedynczego typu ogólnego lub metody.|Generowanych jest wiele wystąpień typów i metod, jeden dla każdego typu, który jest wymagany.|
|Używanie z typami|Może być używany w typach.|Nie można używać w typach.|
|Używanie z funkcjami wbudowanymi|Nie. Wbudowana funkcja nie może być sparametryzowana przy użyciu standardowego parametru typu ogólnego.|Tak. Parametry typu rozpoznane statycznie nie mogą być używane w funkcjach lub metodach, które nie są wbudowane.|

Wiele F# podstawowych funkcji biblioteki, w szczególności operatorów, ma statycznie rozwiązywane parametry typu. Te funkcje i operatory są wbudowane i powodują wydajne generowanie kodu dla obliczeń numerycznych.

Metody wbudowane i funkcje, które używają operatorów lub używają innych funkcji, które mają parametry typu statycznie rozpoznane, mogą również używać parametrów typu statycznie rozpoznanych. Często, wnioskowanie o typie wnioskuje, że funkcje wbudowane, które mają statycznie rozwiązywane parametry typu. Poniższy przykład ilustruje definicję operatora, który jest wywnioskowany, aby miał statycznie rozpoznany parametr typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

Rozpoznany typ `(+@)` jest oparty na użyciu obu `(+)` i `(*)`, obu, z których wynika, że wnioskowanie o typie do wnioskowania ograniczeń składowych na statycznie rozpoznanych parametrach typu. Rozpoznany typ, jak pokazano w F# interpreterze, jest następujący.

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

Począwszy od F# 4,1, można także określić konkretne nazwy typów w sygnaturach parametrów typu, które są rozpoznawane statycznie.  W poprzednich wersjach języka nazwa typu mogła zostać wywnioskowana przez kompilator, ale nie można jej było określić w podpisie.  Począwszy od F# 4,1, można także określić konkretne nazwy typów w sygnaturach parametrów typu, które są rozpoznawane statycznie. Oto przykład:

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
