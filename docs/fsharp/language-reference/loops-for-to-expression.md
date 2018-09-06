---
title: 'Pętle: for...to — Wyrażenie (F#)'
description: 'Zobacz jak F # for... wyrażenie jest używany do wykonywania iteracji w pętli zakresu wartości zmiennej pętli.'
ms.date: 05/16/2016
ms.openlocfilehash: 8160fd30c4f3afe8bb6b58f468802ef1c0ef32ee
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800472"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="a50e8-103">Pętle: for...to — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="a50e8-103">Loops: for...to Expression</span></span>

<span data-ttu-id="a50e8-104">`for...to` Wyrażenie jest używane do wykonywania iteracji w pętli zakresu wartości zmiennej pętli.</span><span class="sxs-lookup"><span data-stu-id="a50e8-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="a50e8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a50e8-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="a50e8-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a50e8-106">Remarks</span></span>

<span data-ttu-id="a50e8-107">Typ identyfikatora jest wnioskowany z typu *start* i *Zakończ* wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a50e8-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="a50e8-108">Typy te wyrażenia musi być 32-bitowych liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="a50e8-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="a50e8-109">Choć z technicznego punktu widzenia wyrażenie `for...to` przypomina tradycyjne instrukcji w języku programowania imperatywnego.</span><span class="sxs-lookup"><span data-stu-id="a50e8-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="a50e8-110">Typ zwracany dla *wyrażenie treści* musi być `unit`.</span><span class="sxs-lookup"><span data-stu-id="a50e8-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="a50e8-111">W poniższych przykładach pokazano różne przypadki użycia `for...to` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a50e8-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="a50e8-112">Dane wyjściowe poprzedniego kodu wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="a50e8-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="a50e8-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a50e8-113">See also</span></span>

- [<span data-ttu-id="a50e8-114">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="a50e8-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="a50e8-115">Pętle: `for...in` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="a50e8-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="a50e8-116">Pętle: `while...do` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="a50e8-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
