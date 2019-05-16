---
title: 'Pętle: for...to — Wyrażenie'
description: Zobacz jak F# for... wyrażenie jest używany do wykonywania iteracji w pętli zakresu wartości zmiennej pętli.
ms.date: 05/16/2016
ms.openlocfilehash: 5b7bb9bac659ddf1d457be1ce17e90a2593666de
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645245"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="1539a-103">Pętle: for...to — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="1539a-103">Loops: for...to Expression</span></span>

<span data-ttu-id="1539a-104">`for...to` Wyrażenie jest używane do wykonywania iteracji w pętli zakresu wartości zmiennej pętli.</span><span class="sxs-lookup"><span data-stu-id="1539a-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="1539a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1539a-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="1539a-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1539a-106">Remarks</span></span>

<span data-ttu-id="1539a-107">Typ identyfikatora jest wnioskowany z typu *start* i *Zakończ* wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1539a-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="1539a-108">Typy te wyrażenia musi być 32-bitowych liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="1539a-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="1539a-109">Choć z technicznego punktu widzenia wyrażenie `for...to` przypomina tradycyjne instrukcji w języku programowania imperatywnego.</span><span class="sxs-lookup"><span data-stu-id="1539a-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="1539a-110">Typ zwracany dla *wyrażenie treści* musi być `unit`.</span><span class="sxs-lookup"><span data-stu-id="1539a-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="1539a-111">W poniższych przykładach pokazano różne przypadki użycia `for...to` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1539a-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="1539a-112">Dane wyjściowe poprzedniego kodu wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="1539a-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="1539a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1539a-113">See also</span></span>

- [<span data-ttu-id="1539a-114">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="1539a-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="1539a-115">Pętle: `for...in` Expression</span><span class="sxs-lookup"><span data-stu-id="1539a-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="1539a-116">Pętle: `while...do` Expression</span><span class="sxs-lookup"><span data-stu-id="1539a-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
