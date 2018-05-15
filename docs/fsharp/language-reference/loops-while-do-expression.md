---
title: 'Pętle: while...do — Wyrażenie (F#)'
description: Zobacz temat jak podczas... czy wyrażenie jest używana do wykonywania iteracji wykonywania (zapętlenia), podczas testu określony warunek jest spełniony.
ms.date: 05/16/2016
ms.openlocfilehash: e3198246e44bbb11b226f04da6795f3da22626e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="cc173-103">Pętle: while...do — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="cc173-103">Loops: while...do Expression</span></span>

<span data-ttu-id="cc173-104">`while...do` Wyrażenie służy do wykonywania iteracji wykonywania (zapętlenia), podczas testu określony warunek jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="cc173-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>


## <a name="syntax"></a><span data-ttu-id="cc173-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc173-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="cc173-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc173-106">Remarks</span></span>
<span data-ttu-id="cc173-107">*Testu wyrażenie* jest oceniany; Jeśli `true`, *treść wyrażenia* jest wykonywany i ponownie obliczyć wyrażenia testu.</span><span class="sxs-lookup"><span data-stu-id="cc173-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="cc173-108">*Treść wyrażenia* musi mieć typ `unit`.</span><span class="sxs-lookup"><span data-stu-id="cc173-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="cc173-109">Jeśli wyrażenie testu jest `false`, zakończenia iteracji.</span><span class="sxs-lookup"><span data-stu-id="cc173-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="cc173-110">Poniższy przykład przedstawia użycie `while...do` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cc173-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="cc173-111">Dane wyjściowe poprzedniego kodu jest strumień losowych liczb od 1 do 20, ostatni wynosi 10.</span><span class="sxs-lookup"><span data-stu-id="cc173-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
<span data-ttu-id="cc173-112">Można użyć `while...do` w wyrażeniach sekwencji i inne wyrażenia obliczeń, w którym to przypadku dostosowaną wersję `while...do` wyrażenie jest używane.</span><span class="sxs-lookup"><span data-stu-id="cc173-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="cc173-113">Aby uzyskać więcej informacji, zobacz [sekwencji](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia obliczeń](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="cc173-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="cc173-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc173-114">See Also</span></span>
[<span data-ttu-id="cc173-115">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="cc173-115">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="cc173-116">Pętle: `for...in` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="cc173-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="cc173-117">Pętle: `for...to` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="cc173-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
