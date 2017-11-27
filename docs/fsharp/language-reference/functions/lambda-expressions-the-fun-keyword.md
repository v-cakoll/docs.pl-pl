---
title: "Wyrażenia lambda: fun — Słowo kluczowe (F#)"
description: "Dowiedz się, jak używać słowa kluczowego \"fun\" F # do definiowania wyrażenia lambda, czyli funkcji anonimowej."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e5d3565c-d7cc-433f-a619-886ed92523a7
ms.openlocfilehash: 09f1c1787bbb4b86ec40f9e973e08104919631aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="89c8a-104">Wyrażenia lambda: fun — Słowo kluczowe (F#)</span><span class="sxs-lookup"><span data-stu-id="89c8a-104">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="89c8a-105">`fun` — Słowo kluczowe jest używane do definiowania wyrażenia lambda, oznacza to, że funkcja anonimowa.</span><span class="sxs-lookup"><span data-stu-id="89c8a-105">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>


## <a name="syntax"></a><span data-ttu-id="89c8a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="89c8a-106">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="89c8a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89c8a-107">Remarks</span></span>
<span data-ttu-id="89c8a-108">*Listy parametrów* zazwyczaj składa się z nazwy i, opcjonalnie, typy parametrów.</span><span class="sxs-lookup"><span data-stu-id="89c8a-108">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="89c8a-109">Ogólnie rzecz biorąc *listy parametrów* może składać się z dowolnym wzorce F #.</span><span class="sxs-lookup"><span data-stu-id="89c8a-109">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="89c8a-110">Aby uzyskać pełną listę wzorców możliwe, zobacz [dopasowanie wzorca](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="89c8a-110">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="89c8a-111">Listę prawidłowych parametrów obejmują następujące przykłady.</span><span class="sxs-lookup"><span data-stu-id="89c8a-111">Lists of valid parameters include the following examples.</span></span>

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

<span data-ttu-id="89c8a-112">*Wyrażenie* treść funkcji ostatniego wyrażenia generuje wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="89c8a-112">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="89c8a-113">Przykłady wyrażeń lambda prawidłowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="89c8a-113">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a><span data-ttu-id="89c8a-114">Korzystając z wyrażenia Lambda</span><span class="sxs-lookup"><span data-stu-id="89c8a-114">Using Lambda Expressions</span></span>
<span data-ttu-id="89c8a-115">Wyrażenia lambda są szczególnie przydatne, jeśli chcesz wykonywać operacje na listę lub innych kolekcji i aby uniknąć dodatkowej pracy definiowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="89c8a-115">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="89c8a-116">Wartości funkcji jako argumenty zająć wiele funkcji biblioteki F # i może być szczególnie łatwe w użyciu wyrażenia lambda w takich przypadkach.</span><span class="sxs-lookup"><span data-stu-id="89c8a-116">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="89c8a-117">Poniższy kod dotyczy elementów listy wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="89c8a-117">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="89c8a-118">W takim przypadku funkcja anonimowa dodaje 1 do każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="89c8a-118">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="89c8a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89c8a-119">See Also</span></span>
[<span data-ttu-id="89c8a-120">Funkcje</span><span class="sxs-lookup"><span data-stu-id="89c8a-120">Functions</span></span>](index.md)
