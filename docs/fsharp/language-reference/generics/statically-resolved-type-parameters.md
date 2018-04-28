---
title: Statycznie rozwiązywane parametry typu (F#)
description: 'Dowiedz się, jak używać F # statycznie rozwiązywane typ parametru, który zostanie zastąpiony rzeczywisty typ w czasie kompilacji zamiast w czasie wykonywania.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: da730014f1c40b6c79d72e4f46a18ef36f50de36
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="statically-resolved-type-parameters"></a>Statycznie rozwiązywane parametry typu

A *parametr typu statycznie rozwiązywane* jest parametrem typu, który jest zastępowany rzeczywisty typ w czasie kompilacji zamiast w czasie wykonywania. Są one poprzedzone symbolem daszek (^).


## <a name="syntax"></a>Składnia

```
ˆtype-parameter
```

## <a name="remarks"></a>Uwagi
W języku F # istnieją dwa różne typy parametrów typu. Rodzaj pierwszy jest parametr standardowa typu ogólnego. Te są oznaczeni apostrof ('), podobnie jak w `'T` i `'U`. Są one równoważne parametry typu ogólnego w innych językach .NET Framework. Innego typu jest statycznie rozwiązane i jest określane przez symbol karetki, podobnie jak w `^T` i `^U`.

Statycznie rozwiązywane parametry typu są szczególnie przydatne w połączeniu z ograniczenia elementu członkowskiego, które są ograniczenia, które pozwalają określić, że typem argumentu musi być określonego elementu członkowskiego lub elementy członkowskie, aby mogły być używane. Nie istnieje sposób tworzenia tego rodzaju ograniczenia za pomocą parametru typu ogólnego regularne.

W poniższej tabeli przedstawiono podobieństwa i różnice między dwa rodzaje parametrów typu.

|Funkcja|Ogólny|Statycznie rozwiązywane|
|-------|-------|-------------------|
|Składnia|`'T`, `'U`|`^T`, `^U`|
|Czas rozpoznawania nazw|Czas wykonywania|Czas kompilacji|
|Ograniczenia elementu członkowskiego|Nie można używać z ograniczenia elementu członkowskiego.|Można z ograniczenia elementu członkowskiego.|
|Generowanie kodu|Typu (lub metody) z parametry typu ogólnego standardowe powoduje generowanie jednego typu ogólnego lub metody.|Wiele wystąpień typów i metod są generowane, jeden dla każdego typu, który jest potrzebny.|
|Za pomocą typów|Można na typach.|Nie można używać typów.|
|Za pomocą funkcji śródwierszowych|Nie. Nie mogą być parametryczne wbudowanej funkcji z parametrem standardowa typu ogólnego.|Tak. Statycznie rozwiązywane parametry typu nie można używać na funkcje i metody, które nie są wbudowane.|

Wiele F # biblioteka funkcji podstawowych, szczególnie operatory ma statycznie rozwiązywane parametry typu. Te funkcje i operatory są wbudowane i spowodować generowanie kodu wydajne w obliczeniach liczbowych.

Wbudowane metody i funkcje, które operatory lub innych funkcji, które mają statycznie rozwiązywane parametry typu można również użyć statycznie rozwiązywane parametry typu samodzielnie. Wnioskowanie o typie wnioskuje często takich funkcji śródwierszowych, aby mieć statycznie rozwiązywane parametry typu. Poniższy przykład przedstawia definicję operatora, która jest wartością parametru typu statycznie rozwiązywane.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

Rozpoznać typu `(+@)` opiera się na korzystanie z obu `(+)` i `(*)`, z którego spowodować wnioskowanie o typie w celu uwzględnienia ograniczenia elementu członkowskiego na statycznie rozwiązywane parametry typu. Rozpoznać typu, jak pokazano w F # interpretera ma następującą składnię.

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

Począwszy od 4.1 F #, można również określić nazwy typu konkretnego w podpisach parametru typu statycznie rozwiązane.  W poprzednich wersjach językowych Nazwa typu faktycznie można wywnioskować przez kompilator, ale faktycznie nie można określić w podpisie.  Począwszy od F # 4.1 należy także określić nazwy typów konkretnych w podpisach parametru typu statycznie rozwiązywane. Oto przykład:

```fsharp
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

## <a name="see-also"></a>Zobacz też
[Typy ogólne](index.md)

[Wnioskowanie o typie](../type-inference.md)

[Automatyczna generalizacja](automatic-generalization.md)

[Ograniczenia](constraints.md)

[Funkcje śródwierszowe](../functions/inline-functions.md)
