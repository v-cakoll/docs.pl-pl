---
title: 'Wyrażenie warunkowe: if... then... else'
description: Dowiedz się, jak napisać wyrażenie warunkowe F# do wykonywania różnych gałęzi kodu.
ms.date: 05/16/2016
ms.openlocfilehash: db2d5ce5b75ecda171f2623c986878dcee1cf4d9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641991"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="b7a6f-103">Wyrażenie warunkowe: `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="b7a6f-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="b7a6f-104">`if...then...else` Wyrażenie uruchamia gałęziami kodu i oblicza również innej wartości w zależności od tego, wyrażenie logiczne, biorąc pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="b7a6f-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7a6f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7a6f-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="b7a6f-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7a6f-106">Remarks</span></span>

<span data-ttu-id="b7a6f-107">W poprzedniej składni *wyrażenie1* jest uruchamiany, gdy wyrażenie logiczne, które daje w wyniku `true`; w przeciwnym razie *wyrażenie2* działa.</span><span class="sxs-lookup"><span data-stu-id="b7a6f-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="b7a6f-108">W przeciwieństwie do innych języków `if...then...else` konstrukcji, stanowi wyrażenie nie instrukcję.</span><span class="sxs-lookup"><span data-stu-id="b7a6f-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="b7a6f-109">Oznacza to generuje wartość, która jest wartością ostatniego wyrażenia w gałęzi, który jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="b7a6f-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="b7a6f-110">Typy wartości, utworzone w każdej gałęzi, muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="b7a6f-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="b7a6f-111">Jeśli nie jawne `else` gałęzi, jego typ jest `unit`.</span><span class="sxs-lookup"><span data-stu-id="b7a6f-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="b7a6f-112">W związku z tym jeśli typ `then` gałąź jest dowolnego typu innego niż `unit`, musi istnieć `else` gałęzi przy użyciu tego samego typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="b7a6f-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="b7a6f-113">Podczas tworzenia łańcucha `if...then...else` wyrażeń razem, można użyć słowa kluczowego `elif` zamiast `else if`; są one równoważne.</span><span class="sxs-lookup"><span data-stu-id="b7a6f-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="b7a6f-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7a6f-114">Example</span></span>

<span data-ttu-id="b7a6f-115">Poniższy przykład ilustruje sposób używania `if...then...else` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b7a6f-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="b7a6f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7a6f-116">See also</span></span>

- [<span data-ttu-id="b7a6f-117">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="b7a6f-117">F# Language Reference</span></span>](index.md)
