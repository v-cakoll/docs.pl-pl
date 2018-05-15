---
title: 'Fixed — słowo kluczowe (F #)'
description: 'Dowiedz się, jak można "przypiąć" lokalnie na stosie zapobiegające kolekcji F # "fixed" — słowo kluczowe.'
ms.date: 04/24/2017
ms.openlocfilehash: 913ee4d7b0f6b2437793d4788e53556d6be6c4db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="63ed4-103">Fixed — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="63ed4-103">The Fixed Keyword</span></span>

<span data-ttu-id="63ed4-104">F # 4.1 wprowadza `fixed` — słowo kluczowe, dzięki czemu można "numer pin" lokalnej na stosie, aby zapobiec jej zebrane lub przenieść podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="63ed4-104">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="63ed4-105">Jest używany dla niskiego poziomu scenariuszy programowania.</span><span class="sxs-lookup"><span data-stu-id="63ed4-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="63ed4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="63ed4-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="63ed4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63ed4-107">Remarks</span></span>

<span data-ttu-id="63ed4-108">Spowoduje to rozszerzenie składni wyrażeń umożliwia wyodrębnianie wskaźnik i powiązania jej nazwę, który uniemożliwił zebrane lub przenieść podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="63ed4-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="63ed4-109">Wskaźnik z wyrażenia został rozwiązany za pomocą `fixed` — słowo kluczowe jest powiązana z identyfikatorem za pośrednictwem `use` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="63ed4-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="63ed4-110">Semantyka tego są podobne do zarządzania zasobami za pośrednictwem `use` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="63ed4-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="63ed4-111">Wskaźnik myszy zostanie rozwiązany, gdy znajduje się w zakresie, a po jest spoza zakresu, nie zostanie rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="63ed4-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="63ed4-112">`fixed` Nie można użyć poza kontekstem `use` powiązania.</span><span class="sxs-lookup"><span data-stu-id="63ed4-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="63ed4-113">Wskaźnik musi powiązać nazwę zawierającą `use`.</span><span class="sxs-lookup"><span data-stu-id="63ed4-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="63ed4-114">Użycie `fixed` musi wystąpić w wyrażeniu w funkcji lub metody.</span><span class="sxs-lookup"><span data-stu-id="63ed4-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="63ed4-115">Nie można używać w zakresie poziomu skryptów lub poziom modułu.</span><span class="sxs-lookup"><span data-stu-id="63ed4-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="63ed4-116">Podobnie jak cały kod wskaźnika jest niebezpieczne feature i będzie emitować ostrzeżenia, gdy jest używany.</span><span class="sxs-lookup"><span data-stu-id="63ed4-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="63ed4-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="63ed4-117">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="63ed4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63ed4-118">See Also</span></span>

[<span data-ttu-id="63ed4-119">Nativeptr — moduł</span><span class="sxs-lookup"><span data-stu-id="63ed4-119">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
