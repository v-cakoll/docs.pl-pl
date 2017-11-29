---
title: "Wyrażenie warunkowe: if... then...else (F#)"
description: "Dowiedz się, jak napisać wyrażenia warunkowe w języku F # do wykonywania różnych gałęziach kodu."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e1871c-4d4d-4691-9ab2-bd2c6f65589a
ms.openlocfilehash: 3531a112eb53657d5e9102d5e5f3be988360b76e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="7ae8e-104">Wyrażenie warunkowe:`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="7ae8e-104">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="7ae8e-105">`if...then...else` Wyrażenie uruchamia różnych gałęziach kodu i oblicza również innej wartości w zależności od danego wyrażenie warunkowe.</span><span class="sxs-lookup"><span data-stu-id="7ae8e-105">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>


## <a name="syntax"></a><span data-ttu-id="7ae8e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ae8e-106">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="7ae8e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ae8e-107">Remarks</span></span>
<span data-ttu-id="7ae8e-108">W poprzednich składni *wyrażenie1* jest uruchamiany, gdy wyrażenie warunkowe daje w wyniku `true`; w przeciwnym razie *wyrażenie2* działa.</span><span class="sxs-lookup"><span data-stu-id="7ae8e-108">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="7ae8e-109">W przeciwieństwie do innych języków `if...then...else` konstrukcja jest wyrażenie nie instrukcję.</span><span class="sxs-lookup"><span data-stu-id="7ae8e-109">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="7ae8e-110">Oznacza to, że generuje wartość, która jest wartością ostatniego wyrażenia w gałęzi, która wykonuje.</span><span class="sxs-lookup"><span data-stu-id="7ae8e-110">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="7ae8e-111">Typy wartości wygenerowane w każdej gałęzi muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="7ae8e-111">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="7ae8e-112">Jeśli nie jawne `else` gałęzi, jego typ jest `unit`.</span><span class="sxs-lookup"><span data-stu-id="7ae8e-112">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="7ae8e-113">W związku z tym jeśli typ `then` gałęzi jest dowolny typ innych niż `unit`, musi być `else` gałąź o taki sam typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="7ae8e-113">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="7ae8e-114">Gdy łańcucha `if...then...else` wyrażenia razem, można użyć słowa kluczowego `elif` zamiast `else if`; są równoważne.</span><span class="sxs-lookup"><span data-stu-id="7ae8e-114">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="7ae8e-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="7ae8e-115">Example</span></span>
<span data-ttu-id="7ae8e-116">Poniższy przykład przedstawia sposób użycia `if...then...else` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="7ae8e-116">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
John
910 is less than 20
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="7ae8e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ae8e-117">See Also</span></span>
[<span data-ttu-id="7ae8e-118">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="7ae8e-118">F# Language Reference</span></span>](index.md)

