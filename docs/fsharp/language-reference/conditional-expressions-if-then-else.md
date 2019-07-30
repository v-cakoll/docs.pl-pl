---
title: 'Wyrażenia warunkowe: IF... następnie... Przejmi'
description: Dowiedz się, jak napisać wyrażenia F# warunkowe w programie, aby wykonać różne gałęzie kodu.
ms.date: 05/16/2016
ms.openlocfilehash: 825149bf296eded3cc2b4d8847ba4d82bea40cdc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630389"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="939e8-103">Wyrażenia warunkowe:`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="939e8-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="939e8-104">`if...then...else` Wyrażenie uruchamia różne gałęzie kodu, a także oblicza inną wartość w zależności od danego wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="939e8-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="939e8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="939e8-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="939e8-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="939e8-106">Remarks</span></span>

<span data-ttu-id="939e8-107">W poprzedniej składni *wyrażenie1* działa, gdy wyrażenie logiczne zwraca `true`wartość; w przeciwnym razie jest uruchamiany *wyrażenie2* .</span><span class="sxs-lookup"><span data-stu-id="939e8-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="939e8-108">W przeciwieństwie do innych języków `if...then...else` konstrukcja jest wyrażeniem, a nie instrukcją.</span><span class="sxs-lookup"><span data-stu-id="939e8-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="939e8-109">Oznacza to, że produkuje wartość, która jest wartością ostatniego wyrażenia w gałęzi, która wykonuje.</span><span class="sxs-lookup"><span data-stu-id="939e8-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="939e8-110">Typy wartości w każdej gałęzi muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="939e8-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="939e8-111">Jeśli nie istnieje jawne `else` rozgałęzienie, jego typem jest. `unit`</span><span class="sxs-lookup"><span data-stu-id="939e8-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="939e8-112">W związku z tym, jeśli typ `then` gałęzi jest dowolnego typu innego niż `unit` `else` , musi istnieć gałąź z tym samym typem zwracanym.</span><span class="sxs-lookup"><span data-stu-id="939e8-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="939e8-113">W przypadku łączenia `elif` `else if`wyrażeń ze sobą można użyć słowa kluczowego zamiast; są `if...then...else` one równoważne.</span><span class="sxs-lookup"><span data-stu-id="939e8-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="939e8-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="939e8-114">Example</span></span>

<span data-ttu-id="939e8-115">Poniższy przykład ilustruje sposób użycia `if...then...else` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="939e8-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="939e8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="939e8-116">See also</span></span>

- [<span data-ttu-id="939e8-117">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="939e8-117">F# Language Reference</span></span>](index.md)
