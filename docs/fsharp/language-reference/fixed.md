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
# <a name="the-fixed-keyword"></a><span data-ttu-id="68081-103">Fixed — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="68081-103">The fixed keyword</span></span>

<span data-ttu-id="68081-104">F#wprowadza 4.1 `fixed` — słowo kluczowe, co pozwala na "przypinając" lokalnej na stosie, aby uniemożliwić jej zebrane lub przeniesione podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="68081-104">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="68081-105">Jest używany w scenariuszach programowania niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="68081-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="68081-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="68081-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="68081-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68081-107">Remarks</span></span>

<span data-ttu-id="68081-108">Spowoduje to rozszerzenie składni wyrażenia, aby umożliwić wyodrębnianie wskaźnik i powiązywanie nazwy, który uniemożliwił są zbierane lub przeniesione podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="68081-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="68081-109">Wskaźnik z wyrażenia został rozwiązany za pośrednictwem `fixed` — słowo kluczowe jest powiązany z odpowiadającym za pośrednictwem `use` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="68081-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="68081-110">Semantyka tego są podobne do zarządzania zasobami za pomocą `use` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="68081-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="68081-111">Wskaźnik jest stała, natomiast znajduje się w zakresie, gdy jest poza zakresem, już nie zostanie rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="68081-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="68081-112">`fixed` Nie można używać poza kontekstem `use` powiązania.</span><span class="sxs-lookup"><span data-stu-id="68081-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="68081-113">Wskaźnik musi być powiązany z nazwą za pomocą `use`.</span><span class="sxs-lookup"><span data-stu-id="68081-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="68081-114">Korzystanie z `fixed` musi wystąpić w wyrażeniu w funkcji lub metody.</span><span class="sxs-lookup"><span data-stu-id="68081-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="68081-115">Nie można używać w zakresie poziomu skryptów lub poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="68081-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="68081-116">Podobnie jak cały kod wskaźnika jest funkcją niebezpieczne i wyemitują ostrzeżenia, gdy jest używana.</span><span class="sxs-lookup"><span data-stu-id="68081-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="68081-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="68081-117">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="68081-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68081-118">See also</span></span>

- [<span data-ttu-id="68081-119">Nativeptr — moduł</span><span class="sxs-lookup"><span data-stu-id="68081-119">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
