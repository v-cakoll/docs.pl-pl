---
title: 'Pętle: for...to — Wyrażenie'
description: Zobacz, F# jak... do wyrażenia jest używany do iteracji w pętli względem zakresu wartości zmiennej pętli.
ms.date: 05/16/2016
ms.openlocfilehash: 882b6e48dd09efcb57f7ef2f419e68a6c43393a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283902"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="63c90-103">Pętle: for...to — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="63c90-103">Loops: for...to Expression</span></span>

<span data-ttu-id="63c90-104">Wyrażenie `for...to` służy do iteracji w pętli względem zakresu wartości zmiennej pętli.</span><span class="sxs-lookup"><span data-stu-id="63c90-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="63c90-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="63c90-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="63c90-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63c90-106">Remarks</span></span>

<span data-ttu-id="63c90-107">Typ identyfikatora jest wywnioskowany na podstawie typu wyrażeń *początkowych* i *końcowych* .</span><span class="sxs-lookup"><span data-stu-id="63c90-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="63c90-108">Typy tych wyrażeń muszą być 32-bitowymi liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="63c90-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="63c90-109">Choć technicznie wyrażenie `for...to` jest bardziej podobne do tradycyjnej instrukcji w bezwzględnym języku programowania.</span><span class="sxs-lookup"><span data-stu-id="63c90-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="63c90-110">Zwracany typ dla *wyrażenia Body* musi być `unit`.</span><span class="sxs-lookup"><span data-stu-id="63c90-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="63c90-111">W poniższych przykładach pokazano różne zastosowania wyrażenia `for...to`.</span><span class="sxs-lookup"><span data-stu-id="63c90-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="63c90-112">Dane wyjściowe poprzedniego kodu wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="63c90-112">The output of the previous code is as follows.</span></span>

```console
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="63c90-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63c90-113">See also</span></span>

- [<span data-ttu-id="63c90-114">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="63c90-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="63c90-115">Pętle: wyrażenie `for...in`</span><span class="sxs-lookup"><span data-stu-id="63c90-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="63c90-116">Pętle: wyrażenie `while...do`</span><span class="sxs-lookup"><span data-stu-id="63c90-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
