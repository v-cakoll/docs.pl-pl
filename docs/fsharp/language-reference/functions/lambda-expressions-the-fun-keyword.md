---
title: 'Wyrażenia lambda: fun — Słowo kluczowe (F#)'
description: 'Dowiedz się, jak zdefiniować wyrażenia lambda jest funkcją anonimową przy użyciu słowa kluczowego "fun" F #.'
ms.date: 05/16/2016
ms.openlocfilehash: a37757f6b7328cd348bbf13f058a6dbc881769cf
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964250"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="21e3c-103">Wyrażenia lambda: fun — Słowo kluczowe (F#)</span><span class="sxs-lookup"><span data-stu-id="21e3c-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="21e3c-104">`fun` — Słowo kluczowe jest używane do definiowania Wyrażenie lambda, oznacza to, że funkcja anonimowa.</span><span class="sxs-lookup"><span data-stu-id="21e3c-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>

## <a name="syntax"></a><span data-ttu-id="21e3c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="21e3c-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="21e3c-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21e3c-106">Remarks</span></span>

<span data-ttu-id="21e3c-107">*Listy parametrów* zwykle składa się z nazwy i, opcjonalnie, typy parametrów.</span><span class="sxs-lookup"><span data-stu-id="21e3c-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="21e3c-108">Ogólnie rzecz biorąc *listy parametrów* może składać się z dowolnym wzorców F #.</span><span class="sxs-lookup"><span data-stu-id="21e3c-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="21e3c-109">Aby uzyskać pełną listę możliwości wzorców, zobacz [dopasowywania do wzorca](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="21e3c-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="21e3c-110">Listy prawidłowych parametrów zawierają następujące przykłady.</span><span class="sxs-lookup"><span data-stu-id="21e3c-110">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="21e3c-111">*Wyrażenie* treści funkcji ostatniego wyrażenia, które generuje wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="21e3c-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="21e3c-112">Przykłady wyrażeń lambda prawidłowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="21e3c-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a><span data-ttu-id="21e3c-113">Korzystając z wyrażenia Lambda</span><span class="sxs-lookup"><span data-stu-id="21e3c-113">Using Lambda Expressions</span></span>

<span data-ttu-id="21e3c-114">Wyrażenia lambda są szczególnie przydatne, jeśli chcesz wykonywać operacje na liście lub inna kolekcja i chcesz uniknąć dodatkowej pracy definiowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="21e3c-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="21e3c-115">Wiele funkcji biblioteki F # pobierają wartości funkcji jako argumentów i może być szczególnie wygodne, można użyć wyrażenia lambda w tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="21e3c-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="21e3c-116">Następujący kod dotyczy elementów listy, wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="21e3c-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="21e3c-117">W takim przypadku funkcja anonimowa dodaje 1 dla każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="21e3c-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a><span data-ttu-id="21e3c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21e3c-118">See also</span></span>

- [<span data-ttu-id="21e3c-119">Funkcje</span><span class="sxs-lookup"><span data-stu-id="21e3c-119">Functions</span></span>](index.md)
