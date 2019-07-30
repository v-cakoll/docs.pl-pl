---
title: 'Wyrażenia lambda: Zabawne słowo kluczowe'
description: Dowiedz się, jak F# za pomocą słowa kluczowego "zabawny" zdefiniować wyrażenie lambda, które jest funkcją anonimową.
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630663"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="502c4-103">Wyrażenia lambda: Zabawne słowo kluczowe (F#)</span><span class="sxs-lookup"><span data-stu-id="502c4-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="502c4-104">`fun` Słowo kluczowe jest używane do definiowania wyrażenia lambda, czyli funkcji anonimowej.</span><span class="sxs-lookup"><span data-stu-id="502c4-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>

## <a name="syntax"></a><span data-ttu-id="502c4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="502c4-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="502c4-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="502c4-106">Remarks</span></span>

<span data-ttu-id="502c4-107">*Lista parametrów* zwykle składa się z nazw i, opcjonalnie, typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="502c4-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="502c4-108">Ogólnie rzecz biorąc, *Lista parametrów* może składać się z jakichkolwiek F# wzorców.</span><span class="sxs-lookup"><span data-stu-id="502c4-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="502c4-109">Aby uzyskać pełną listę możliwych wzorców, zobacz [Dopasowanie wzorców](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="502c4-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="502c4-110">Lista prawidłowych parametrów zawiera następujące przykłady.</span><span class="sxs-lookup"><span data-stu-id="502c4-110">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="502c4-111">*Wyrażenie* jest treścią funkcji, ostatnim wyrażeniem generującym wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="502c4-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="502c4-112">Przykłady prawidłowych wyrażeń lambda są następujące:</span><span class="sxs-lookup"><span data-stu-id="502c4-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a><span data-ttu-id="502c4-113">Korzystając z wyrażenia Lambda</span><span class="sxs-lookup"><span data-stu-id="502c4-113">Using Lambda Expressions</span></span>

<span data-ttu-id="502c4-114">Wyrażenia lambda są szczególnie przydatne podczas wykonywania operacji na liście lub w innej kolekcji i chcą uniknąć dodatkowej pracy związanej z definiowaniem funkcji.</span><span class="sxs-lookup"><span data-stu-id="502c4-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="502c4-115">Wiele F# funkcji biblioteki przyjmuje wartości funkcji jako argumenty i może być szczególnie wygodne do użycia wyrażenia lambda w tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="502c4-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="502c4-116">Poniższy kod stosuje wyrażenie lambda do elementów listy.</span><span class="sxs-lookup"><span data-stu-id="502c4-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="502c4-117">W takim przypadku funkcja anonimowa dodaje 1 do każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="502c4-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a><span data-ttu-id="502c4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="502c4-118">See also</span></span>

- [<span data-ttu-id="502c4-119">Funkcje</span><span class="sxs-lookup"><span data-stu-id="502c4-119">Functions</span></span>](index.md)
