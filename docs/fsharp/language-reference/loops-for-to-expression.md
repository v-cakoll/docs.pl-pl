---
title: "Pętle: for...to — Wyrażenie (F#)"
description: "Zobacz jak F # for... wyrażenie służy do wykonywania iteracji w pętli zakres wartości zmiennej pętli."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e14c38d9-b1ef-4b7f-be9a-fb6ef6708e02
ms.openlocfilehash: 1a1d71d30b5e87e4691a78acd5032de9419399db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forto-expression"></a><span data-ttu-id="e3676-104">Pętle: for...to — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="e3676-104">Loops: for...to Expression</span></span>

<span data-ttu-id="e3676-105">`for...to` Wyrażenie jest używane w celu wykonania iteracji w pętli zakres wartości zmiennej pętli.</span><span class="sxs-lookup"><span data-stu-id="e3676-105">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>


## <a name="syntax"></a><span data-ttu-id="e3676-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3676-106">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="e3676-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3676-107">Remarks</span></span>
<span data-ttu-id="e3676-108">Typ identyfikatora jest wywnioskowany na podstawie typu *start* i *Zakończ* wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e3676-108">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="e3676-109">Typy wyrażeń te muszą być 32-bitowych liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e3676-109">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="e3676-110">Chociaż technicznie wyrażenie `for...to` przypomina tradycyjnych instrukcji w języku programowania nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="e3676-110">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="e3676-111">Typ zwracany dla *treść wyrażenia* musi być `unit`.</span><span class="sxs-lookup"><span data-stu-id="e3676-111">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="e3676-112">W poniższych przykładach pokazano różnych zastosowań `for...to` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e3676-112">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="e3676-113">Dane wyjściowe poprzedniego kodu wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="e3676-113">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="e3676-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3676-114">See Also</span></span>
[<span data-ttu-id="e3676-115">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="e3676-115">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="e3676-116">Pętle: `for...in` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="e3676-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="e3676-117">Pętle: `while...do` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="e3676-117">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
