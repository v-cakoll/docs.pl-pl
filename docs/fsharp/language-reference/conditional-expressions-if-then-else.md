---
title: 'Wyrażenie warunkowe: if... then...else (F#)'
description: Dowiedz się, jak napisać wyrażenie warunkowe w języku F# do wykonywania różnych gałęzi kodu.
ms.date: 05/16/2016
ms.openlocfilehash: 10e4224bef772f00520cf5a0fff2f2920147c2fc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "44177604"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="a0870-103">Wyrażenie warunkowe: `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="a0870-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="a0870-104">`if...then...else` Wyrażenie uruchamia gałęziami kodu i oblicza również innej wartości w zależności od tego, wyrażenie logiczne, biorąc pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="a0870-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="a0870-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0870-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="a0870-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0870-106">Remarks</span></span>

<span data-ttu-id="a0870-107">W poprzedniej składni *wyrażenie1* jest uruchamiany, gdy wyrażenie logiczne, które daje w wyniku `true`; w przeciwnym razie *wyrażenie2* działa.</span><span class="sxs-lookup"><span data-stu-id="a0870-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="a0870-108">W przeciwieństwie do innych języków `if...then...else` konstrukcji, stanowi wyrażenie nie instrukcję.</span><span class="sxs-lookup"><span data-stu-id="a0870-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="a0870-109">Oznacza to generuje wartość, która jest wartością ostatniego wyrażenia w gałęzi, który jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="a0870-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="a0870-110">Typy wartości, utworzone w każdej gałęzi, muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="a0870-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="a0870-111">Jeśli nie jawne `else` gałęzi, jego typ jest `unit`.</span><span class="sxs-lookup"><span data-stu-id="a0870-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="a0870-112">W związku z tym jeśli typ `then` gałąź jest dowolnego typu innego niż `unit`, musi istnieć `else` gałęzi przy użyciu tego samego typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="a0870-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="a0870-113">Podczas tworzenia łańcucha `if...then...else` wyrażeń razem, można użyć słowa kluczowego `elif` zamiast `else if`; są one równoważne.</span><span class="sxs-lookup"><span data-stu-id="a0870-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="a0870-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0870-114">Example</span></span>

<span data-ttu-id="a0870-115">Poniższy przykład ilustruje sposób używania `if...then...else` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a0870-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="a0870-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0870-116">See also</span></span>

- [<span data-ttu-id="a0870-117">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="a0870-117">F# Language Reference</span></span>](index.md)
