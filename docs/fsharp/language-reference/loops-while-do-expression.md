---
title: "Pętle: while...do — Wyrażenie (F#)"
description: "Zobacz temat jak while... czy wyrażenie jest używana do wykonywania iteracji wykonywania (zapętlenia), podczas testu określony warunek jest spełniony."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0416ffca-7ed9-4aff-9493-e001fdba8c9b
ms.openlocfilehash: 6a186d75dcda383764949c2cd3b09bc9e3d1080a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="439ae-104">Pętle: while...do — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="439ae-104">Loops: while...do Expression</span></span>

<span data-ttu-id="439ae-105">`while...do` Wyrażenie służy do wykonywania iteracji wykonywania (zapętlenia), podczas testu określony warunek jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="439ae-105">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>


## <a name="syntax"></a><span data-ttu-id="439ae-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="439ae-106">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="439ae-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="439ae-107">Remarks</span></span>
<span data-ttu-id="439ae-108">*Testu wyrażenie* jest oceniany; Jeśli `true`, *treść wyrażenia* jest wykonywany i ponownie obliczyć wyrażenia testu.</span><span class="sxs-lookup"><span data-stu-id="439ae-108">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="439ae-109">*Treść wyrażenia* musi mieć typ `unit`.</span><span class="sxs-lookup"><span data-stu-id="439ae-109">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="439ae-110">Jeśli wyrażenie testu jest `false`, zakończenia iteracji.</span><span class="sxs-lookup"><span data-stu-id="439ae-110">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="439ae-111">Poniższy przykład przedstawia użycie `while...do` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="439ae-111">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="439ae-112">Dane wyjściowe poprzedniego kodu jest strumień losowych liczb od 1 do 20, ostatni wynosi 10.</span><span class="sxs-lookup"><span data-stu-id="439ae-112">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
<span data-ttu-id="439ae-113">Można użyć `while...do` w wyrażeniach sekwencji i inne wyrażenia obliczeń, w którym to przypadku dostosowaną wersję `while...do` wyrażenie jest używane.</span><span class="sxs-lookup"><span data-stu-id="439ae-113">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="439ae-114">Aby uzyskać więcej informacji, zobacz [sekwencji](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia obliczeń](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="439ae-114">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="439ae-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="439ae-115">See Also</span></span>
[<span data-ttu-id="439ae-116">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="439ae-116">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="439ae-117">Pętle: `for...in` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="439ae-117">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="439ae-118">Pętle: `for...to` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="439ae-118">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
