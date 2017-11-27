---
title: "Fixed — słowo kluczowe (F #)"
description: "Dowiedz się, jak można \"przypiąć\" lokalnie na stosie zapobiegające kolekcji F # \"fixed\" — słowo kluczowe."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5795ce1f-11bf-4798-9f1f-6e44ffa1477e
ms.openlocfilehash: ac6be2bb9df8da1b6d0a29c2e27f777eade07cb9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="the-fixed-keyword"></a>Fixed — słowo kluczowe

F # 4.1 wprowadza `fixed` — słowo kluczowe, dzięki czemu można "numer pin" lokalnej na stosie, aby zapobiec jej zebrane lub przenieść podczas wyrzucania elementów bezużytecznych.  Jest używany dla niskiego poziomu scenariuszy programowania.

## <a name="syntax"></a>Składnia

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Uwagi

Spowoduje to rozszerzenie składni wyrażeń umożliwia wyodrębnianie wskaźnik i powiązania jej nazwę, który uniemożliwił zebrane lub przenieść podczas wyrzucania elementów bezużytecznych.  

Wskaźnik z wyrażenia został rozwiązany za pomocą `fixed` — słowo kluczowe jest powiązana z identyfikatorem za pośrednictwem `use` — słowo kluczowe.  Semantyka tego są podobne do zarządzania zasobami za pośrednictwem `use` — słowo kluczowe.  Wskaźnik myszy zostanie rozwiązany, gdy znajduje się w zakresie, a po jest spoza zakresu, nie zostanie rozwiązany.  `fixed`Nie można użyć poza kontekstem `use` powiązania.  Wskaźnik musi powiązać nazwę zawierającą `use`.

Użycie `fixed` musi wystąpić w wyrażeniu w funkcji lub metody.  Nie można używać w zakresie poziomu skryptów lub poziom modułu.

Podobnie jak cały kod wskaźnika jest niebezpieczne feature i będzie emitować ostrzeżenia, gdy jest używany.

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

## <a name="see-also"></a>Zobacz też

[Nativeptr — moduł](https://msdn.microsoft.com/en-us/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
