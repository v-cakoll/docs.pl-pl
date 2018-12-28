---
title: 'Wyrażenie warunkowe: if... then... else'
description: Dowiedz się, jak napisać wyrażenie warunkowe F# do wykonywania różnych gałęzi kodu.
ms.date: 05/16/2016
ms.openlocfilehash: eade8c20c1b62a2e9a54700550d832798308f368
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614061"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="22d3c-103">Wyrażenie warunkowe: `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="22d3c-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="22d3c-104">`if...then...else` Wyrażenie uruchamia gałęziami kodu i oblicza również innej wartości w zależności od tego, wyrażenie logiczne, biorąc pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="22d3c-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="22d3c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="22d3c-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="22d3c-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22d3c-106">Remarks</span></span>

<span data-ttu-id="22d3c-107">W poprzedniej składni *wyrażenie1* jest uruchamiany, gdy wyrażenie logiczne, które daje w wyniku `true`; w przeciwnym razie *wyrażenie2* działa.</span><span class="sxs-lookup"><span data-stu-id="22d3c-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="22d3c-108">W przeciwieństwie do innych języków `if...then...else` konstrukcji, stanowi wyrażenie nie instrukcję.</span><span class="sxs-lookup"><span data-stu-id="22d3c-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="22d3c-109">Oznacza to generuje wartość, która jest wartością ostatniego wyrażenia w gałęzi, który jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="22d3c-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="22d3c-110">Typy wartości, utworzone w każdej gałęzi, muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="22d3c-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="22d3c-111">Jeśli nie jawne `else` gałęzi, jego typ jest `unit`.</span><span class="sxs-lookup"><span data-stu-id="22d3c-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="22d3c-112">W związku z tym jeśli typ `then` gałąź jest dowolnego typu innego niż `unit`, musi istnieć `else` gałęzi przy użyciu tego samego typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="22d3c-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="22d3c-113">Podczas tworzenia łańcucha `if...then...else` wyrażeń razem, można użyć słowa kluczowego `elif` zamiast `else if`; są one równoważne.</span><span class="sxs-lookup"><span data-stu-id="22d3c-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="22d3c-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="22d3c-114">Example</span></span>

<span data-ttu-id="22d3c-115">Poniższy przykład ilustruje sposób używania `if...then...else` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="22d3c-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="22d3c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22d3c-116">See also</span></span>

- [<span data-ttu-id="22d3c-117">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="22d3c-117">F# Language Reference</span></span>](index.md)