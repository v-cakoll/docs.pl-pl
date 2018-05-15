---
title: 'Wyrażenia lambda: fun — Słowo kluczowe (F#)'
description: 'Dowiedz się, jak używać słowa kluczowego "fun" F # do definiowania wyrażenia lambda, czyli funkcji anonimowej.'
ms.date: 05/16/2016
ms.openlocfilehash: 433451fb9bf89bfabdcd8e71560105317771d251
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="6fa45-103">Wyrażenia lambda: fun — Słowo kluczowe (F#)</span><span class="sxs-lookup"><span data-stu-id="6fa45-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="6fa45-104">`fun` — Słowo kluczowe jest używane do definiowania wyrażenia lambda, oznacza to, że funkcja anonimowa.</span><span class="sxs-lookup"><span data-stu-id="6fa45-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>


## <a name="syntax"></a><span data-ttu-id="6fa45-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fa45-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="6fa45-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6fa45-106">Remarks</span></span>
<span data-ttu-id="6fa45-107">*Listy parametrów* zazwyczaj składa się z nazwy i, opcjonalnie, typy parametrów.</span><span class="sxs-lookup"><span data-stu-id="6fa45-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="6fa45-108">Ogólnie rzecz biorąc *listy parametrów* może składać się z dowolnym wzorce F #.</span><span class="sxs-lookup"><span data-stu-id="6fa45-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="6fa45-109">Aby uzyskać pełną listę wzorców możliwe, zobacz [dopasowanie wzorca](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="6fa45-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="6fa45-110">Listę prawidłowych parametrów obejmują następujące przykłady.</span><span class="sxs-lookup"><span data-stu-id="6fa45-110">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="6fa45-111">*Wyrażenie* treść funkcji ostatniego wyrażenia generuje wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="6fa45-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="6fa45-112">Przykłady wyrażeń lambda prawidłowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="6fa45-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a><span data-ttu-id="6fa45-113">Korzystając z wyrażenia Lambda</span><span class="sxs-lookup"><span data-stu-id="6fa45-113">Using Lambda Expressions</span></span>
<span data-ttu-id="6fa45-114">Wyrażenia lambda są szczególnie przydatne, jeśli chcesz wykonywać operacje na listę lub innych kolekcji i aby uniknąć dodatkowej pracy definiowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="6fa45-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="6fa45-115">Wartości funkcji jako argumenty zająć wiele funkcji biblioteki F # i może być szczególnie łatwe w użyciu wyrażenia lambda w takich przypadkach.</span><span class="sxs-lookup"><span data-stu-id="6fa45-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="6fa45-116">Poniższy kod dotyczy elementów listy wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="6fa45-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="6fa45-117">W takim przypadku funkcja anonimowa dodaje 1 do każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="6fa45-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="6fa45-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6fa45-118">See Also</span></span>
[<span data-ttu-id="6fa45-119">Funkcje</span><span class="sxs-lookup"><span data-stu-id="6fa45-119">Functions</span></span>](index.md)
