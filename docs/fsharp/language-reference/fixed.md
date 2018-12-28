---
title: Fixed — słowo kluczowe
description: Dowiedz się, jak można przypiąć lokalnego na stosie, aby zapobiec kolekcji z F# — słowo kluczowe "fixed".
ms.date: 04/24/2017
ms.openlocfilehash: 7fdf66560f3e2ab7584b00c7e4584d7f6c161858
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614362"
---
# <a name="the-fixed-keyword"></a>Fixed — słowo kluczowe

F#wprowadza 4.1 `fixed` — słowo kluczowe, co pozwala na "przypinając" lokalnej na stosie, aby uniemożliwić jej zebrane lub przeniesione podczas wyrzucania elementów bezużytecznych.  Jest używany w scenariuszach programowania niskiego poziomu.

## <a name="syntax"></a>Składnia

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Uwagi

Spowoduje to rozszerzenie składni wyrażenia, aby umożliwić wyodrębnianie wskaźnik i powiązywanie nazwy, który uniemożliwił są zbierane lub przeniesione podczas wyrzucania elementów bezużytecznych.  

Wskaźnik z wyrażenia został rozwiązany za pośrednictwem `fixed` — słowo kluczowe jest powiązany z odpowiadającym za pośrednictwem `use` — słowo kluczowe.  Semantyka tego są podobne do zarządzania zasobami za pomocą `use` — słowo kluczowe.  Wskaźnik jest stała, natomiast znajduje się w zakresie, gdy jest poza zakresem, już nie zostanie rozwiązany.  `fixed` Nie można używać poza kontekstem `use` powiązania.  Wskaźnik musi być powiązany z nazwą za pomocą `use`.

Korzystanie z `fixed` musi wystąpić w wyrażeniu w funkcji lub metody.  Nie można używać w zakresie poziomu skryptów lub poziomie modułu.

Podobnie jak cały kod wskaźnika jest funkcją niebezpieczne i wyemitują ostrzeżenia, gdy jest używana.

## <a name="example"></a>Przykład

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a>Zobacz także

- [Nativeptr — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
