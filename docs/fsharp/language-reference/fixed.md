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
ms.openlocfilehash: 1605603bc35941e21c798600140036fb678869b5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="d9019-104">Fixed — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="d9019-104">The Fixed Keyword</span></span>

<span data-ttu-id="d9019-105">F # 4.1 wprowadza `fixed` — słowo kluczowe, dzięki czemu można "numer pin" lokalnej na stosie, aby zapobiec jej zebrane lub przenieść podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d9019-105">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="d9019-106">Jest używany dla niskiego poziomu scenariuszy programowania.</span><span class="sxs-lookup"><span data-stu-id="d9019-106">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="d9019-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9019-107">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="d9019-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9019-108">Remarks</span></span>

<span data-ttu-id="d9019-109">Spowoduje to rozszerzenie składni wyrażeń umożliwia wyodrębnianie wskaźnik i powiązania jej nazwę, który uniemożliwił zebrane lub przenieść podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d9019-109">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="d9019-110">Wskaźnik z wyrażenia został rozwiązany za pomocą `fixed` — słowo kluczowe jest powiązana z identyfikatorem za pośrednictwem `use` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d9019-110">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="d9019-111">Semantyka tego są podobne do zarządzania zasobami za pośrednictwem `use` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d9019-111">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="d9019-112">Wskaźnik myszy zostanie rozwiązany, gdy znajduje się w zakresie, a po jest spoza zakresu, nie zostanie rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="d9019-112">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="d9019-113">`fixed`Nie można użyć poza kontekstem `use` powiązania.</span><span class="sxs-lookup"><span data-stu-id="d9019-113">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="d9019-114">Wskaźnik musi powiązać nazwę zawierającą `use`.</span><span class="sxs-lookup"><span data-stu-id="d9019-114">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="d9019-115">Użycie `fixed` musi wystąpić w wyrażeniu w funkcji lub metody.</span><span class="sxs-lookup"><span data-stu-id="d9019-115">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="d9019-116">Nie można używać w zakresie poziomu skryptów lub poziom modułu.</span><span class="sxs-lookup"><span data-stu-id="d9019-116">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="d9019-117">Podobnie jak cały kod wskaźnika jest niebezpieczne feature i będzie emitować ostrzeżenia, gdy jest używany.</span><span class="sxs-lookup"><span data-stu-id="d9019-117">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="d9019-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9019-118">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d9019-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9019-119">See Also</span></span>

[<span data-ttu-id="d9019-120">NativePtr Module</span><span class="sxs-lookup"><span data-stu-id="d9019-120">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
