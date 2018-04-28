---
title: 'Wyrażenie warunkowe: if... then...else (F#)'
description: 'Dowiedz się, jak napisać wyrażenia warunkowe w języku F # do wykonywania różnych gałęziach kodu.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bfb985f09be91034894e1d3eba88cebef6bb3fd4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="2debc-103">Wyrażenie warunkowe: `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="2debc-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="2debc-104">`if...then...else` Wyrażenie uruchamia różnych gałęziach kodu i oblicza również innej wartości w zależności od danego wyrażenie warunkowe.</span><span class="sxs-lookup"><span data-stu-id="2debc-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>


## <a name="syntax"></a><span data-ttu-id="2debc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2debc-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="2debc-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2debc-106">Remarks</span></span>
<span data-ttu-id="2debc-107">W poprzednich składni *wyrażenie1* jest uruchamiany, gdy wyrażenie warunkowe daje w wyniku `true`; w przeciwnym razie *wyrażenie2* działa.</span><span class="sxs-lookup"><span data-stu-id="2debc-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="2debc-108">W przeciwieństwie do innych języków `if...then...else` konstrukcja jest wyrażenie nie instrukcję.</span><span class="sxs-lookup"><span data-stu-id="2debc-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="2debc-109">Oznacza to, że generuje wartość, która jest wartością ostatniego wyrażenia w gałęzi, która wykonuje.</span><span class="sxs-lookup"><span data-stu-id="2debc-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="2debc-110">Typy wartości wygenerowane w każdej gałęzi muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="2debc-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="2debc-111">Jeśli nie jawne `else` gałęzi, jego typ jest `unit`.</span><span class="sxs-lookup"><span data-stu-id="2debc-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="2debc-112">W związku z tym jeśli typ `then` gałęzi jest dowolny typ innych niż `unit`, musi być `else` gałąź o taki sam typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="2debc-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="2debc-113">Gdy łańcucha `if...then...else` wyrażenia razem, można użyć słowa kluczowego `elif` zamiast `else if`; są równoważne.</span><span class="sxs-lookup"><span data-stu-id="2debc-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="2debc-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="2debc-114">Example</span></span>
<span data-ttu-id="2debc-115">Poniższy przykład przedstawia sposób użycia `if...then...else` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2debc-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="2debc-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2debc-116">See Also</span></span>
[<span data-ttu-id="2debc-117">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="2debc-117">F# Language Reference</span></span>](index.md)

