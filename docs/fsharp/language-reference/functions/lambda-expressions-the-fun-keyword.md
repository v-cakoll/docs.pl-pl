---
title: 'Lambda Expressions: Fun — słowo kluczowe'
description: Dowiedz się, jak używać F# — słowo kluczowe "fun", aby zdefiniować wyrażenia lambda jest funkcją anonimową.
ms.date: 05/16/2016
ms.openlocfilehash: c59d32bd4226384213453f1a9d362209e68a6fb5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645391"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="2662e-103">Lambda Expressions: Fun — słowo kluczowe (F#)</span><span class="sxs-lookup"><span data-stu-id="2662e-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="2662e-104">`fun` — Słowo kluczowe jest używane do definiowania Wyrażenie lambda, oznacza to, że funkcja anonimowa.</span><span class="sxs-lookup"><span data-stu-id="2662e-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>

## <a name="syntax"></a><span data-ttu-id="2662e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2662e-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="2662e-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2662e-106">Remarks</span></span>

<span data-ttu-id="2662e-107">*Listy parametrów* zwykle składa się z nazwy i, opcjonalnie, typy parametrów.</span><span class="sxs-lookup"><span data-stu-id="2662e-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="2662e-108">Ogólnie rzecz biorąc *listy parametrów* może składać się z dowolnej F# wzorców.</span><span class="sxs-lookup"><span data-stu-id="2662e-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="2662e-109">Aby uzyskać pełną listę możliwości wzorców, zobacz [dopasowywania do wzorca](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="2662e-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="2662e-110">Listy prawidłowych parametrów zawierają następujące przykłady.</span><span class="sxs-lookup"><span data-stu-id="2662e-110">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="2662e-111">*Wyrażenie* treści funkcji ostatniego wyrażenia, które generuje wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="2662e-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="2662e-112">Przykłady wyrażeń lambda prawidłowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="2662e-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a><span data-ttu-id="2662e-113">Korzystając z wyrażenia Lambda</span><span class="sxs-lookup"><span data-stu-id="2662e-113">Using Lambda Expressions</span></span>

<span data-ttu-id="2662e-114">Wyrażenia lambda są szczególnie przydatne, jeśli chcesz wykonywać operacje na liście lub inna kolekcja i chcesz uniknąć dodatkowej pracy definiowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="2662e-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="2662e-115">Wiele F# funkcje biblioteki przyjmują wartości funkcji jako argumentów i może być szczególnie wygodne, można użyć wyrażenia lambda w tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="2662e-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="2662e-116">Następujący kod dotyczy elementów listy, wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="2662e-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="2662e-117">W takim przypadku funkcja anonimowa dodaje 1 dla każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="2662e-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a><span data-ttu-id="2662e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2662e-118">See also</span></span>

- [<span data-ttu-id="2662e-119">Funkcje</span><span class="sxs-lookup"><span data-stu-id="2662e-119">Functions</span></span>](index.md)
