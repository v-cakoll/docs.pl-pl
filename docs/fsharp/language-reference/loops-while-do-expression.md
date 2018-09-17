---
title: 'Pętle: while...do — Wyrażenie (F#)'
description: Zobacz jak podczas... zrobić wyrażenie jest używany do wykonywania iteracji wykonywanie (pętli), gdy spełniony jest warunek określony test.
ms.date: 05/16/2016
ms.openlocfilehash: 5cf4461669221f91cb50e238c25494f03a10bbc2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664712"
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="e5ca0-103">Pętle: while...do — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="e5ca0-103">Loops: while...do Expression</span></span>

<span data-ttu-id="e5ca0-104">`while...do` Wyrażenie jest używany do wykonywania iteracji wykonywanie (pętli), gdy spełniony jest warunek określony test.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5ca0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5ca0-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="e5ca0-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5ca0-106">Remarks</span></span>

<span data-ttu-id="e5ca0-107">*Wyrażeniu testowym* jest oceniany; Jeśli `true`, *wyrażenie treści* jest wykonywane i ponownie obliczone wyrażenie testu.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="e5ca0-108">*Wyrażenie treści* musi mieć typ `unit`.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="e5ca0-109">Jeśli wyrażenie testu jest `false`, zakończenia iteracji.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="e5ca0-110">Poniższy przykład ilustruje użycie `while...do` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="e5ca0-111">Dane wyjściowe poprzedniego kodu jest strumienia liczb losowych z zakresu od 1 do 20, za ostatni wynosi 10.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE]
<span data-ttu-id="e5ca0-112">Możesz użyć `while...do` w sekwencji, wyrażenia i inne wyrażenia obliczeń, w którym to przypadku dostosowaną wersję `while...do` wyrażenie jest używane.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="e5ca0-113">Aby uzyskać więcej informacji, zobacz [sekwencje](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia obliczeń](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e5ca0-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5ca0-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5ca0-114">See also</span></span>

- [<span data-ttu-id="e5ca0-115">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="e5ca0-115">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="e5ca0-116">Pętle: `for...in` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="e5ca0-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="e5ca0-117">Pętle: `for...to` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="e5ca0-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
