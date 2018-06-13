---
title: 'Pętle: for...to — Wyrażenie (F#)'
description: 'Zobacz jak F # for... wyrażenie służy do wykonywania iteracji w pętli zakres wartości zmiennej pętli.'
ms.date: 05/16/2016
ms.openlocfilehash: 841c7d557abc11e0253cb87ab8081cc77671b44b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563405"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="4ff3d-103">Pętle: for...to — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="4ff3d-103">Loops: for...to Expression</span></span>

<span data-ttu-id="4ff3d-104">`for...to` Wyrażenie jest używane w celu wykonania iteracji w pętli zakres wartości zmiennej pętli.</span><span class="sxs-lookup"><span data-stu-id="4ff3d-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>


## <a name="syntax"></a><span data-ttu-id="4ff3d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ff3d-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="4ff3d-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ff3d-106">Remarks</span></span>
<span data-ttu-id="4ff3d-107">Typ identyfikatora jest wywnioskowany na podstawie typu *start* i *Zakończ* wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="4ff3d-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="4ff3d-108">Typy wyrażeń te muszą być 32-bitowych liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="4ff3d-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="4ff3d-109">Chociaż technicznie wyrażenie `for...to` przypomina tradycyjnych instrukcji w języku programowania nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4ff3d-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="4ff3d-110">Typ zwracany dla *treść wyrażenia* musi być `unit`.</span><span class="sxs-lookup"><span data-stu-id="4ff3d-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="4ff3d-111">W poniższych przykładach pokazano różnych zastosowań `for...to` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="4ff3d-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="4ff3d-112">Dane wyjściowe poprzedniego kodu wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="4ff3d-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="4ff3d-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ff3d-113">See Also</span></span>
[<span data-ttu-id="4ff3d-114">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="4ff3d-114">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="4ff3d-115">Pętle: `for...in` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="4ff3d-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="4ff3d-116">Pętle: `while...do` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="4ff3d-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
