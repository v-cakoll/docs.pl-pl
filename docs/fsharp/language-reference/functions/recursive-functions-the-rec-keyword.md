---
title: 'Funkcje cykliczne: Rec — słowo kluczowe'
description: Dowiedz się F# , w jaki sposób słowo kluczowe "Rec" jest używane z słowem kluczowym "let" w celu zdefiniowania funkcji cyklicznej.
ms.date: 05/16/2016
ms.openlocfilehash: 7edaa7206b2109c7b1a405624b9b2330968f9c52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630651"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="7adb4-103">Funkcje cykliczne: Rec — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="7adb4-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="7adb4-104">Słowo kluczowe jest używane razem `let` ze słowem kluczowym w celu zdefiniowania funkcji cyklicznej. `rec`</span><span class="sxs-lookup"><span data-stu-id="7adb4-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="7adb4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7adb4-105">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="7adb4-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7adb4-106">Remarks</span></span>

<span data-ttu-id="7adb4-107">Funkcje cykliczne, funkcje, które wywołują siebie, są jawnie F# identyfikowane w języku.</span><span class="sxs-lookup"><span data-stu-id="7adb4-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="7adb4-108">Dzięki temu identyfikator jest definiowany w zakresie funkcji.</span><span class="sxs-lookup"><span data-stu-id="7adb4-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="7adb4-109">Poniższy kod ilustruje funkcję cykliczną, która oblicza n-<sup>ty</sup> numer Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="7adb4-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="7adb4-110">W praktyce kod taki jak powyżej to wasteful pamięci i czasu procesora, ponieważ obejmuje on ponownie obliczenie poprzednio obliczonych wartości.</span><span class="sxs-lookup"><span data-stu-id="7adb4-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>

<span data-ttu-id="7adb4-111">Metody są niejawnie cykliczne w obrębie typu; nie ma potrzeby dodawania `rec` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="7adb4-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="7adb4-112">Zezwól na powiązania w klasach niejawnie cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="7adb4-112">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="7adb4-113">Funkcje wzajemnie cykliczne</span><span class="sxs-lookup"><span data-stu-id="7adb4-113">Mutually Recursive Functions</span></span>

<span data-ttu-id="7adb4-114">Czasami funkcje są *wzajemnie cykliczne*, co oznacza, że wywołuje postać okręgu, w którym jedna funkcja wywołuje inną funkcję, która z kolei wywołuje pierwszy, z dowolną liczbą wywołań między.</span><span class="sxs-lookup"><span data-stu-id="7adb4-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="7adb4-115">Należy zdefiniować takie funkcje razem w jednym `let` powiązaniu, `and` używając słowa kluczowego, aby połączyć je ze sobą.</span><span class="sxs-lookup"><span data-stu-id="7adb4-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="7adb4-116">Poniższy przykład pokazuje dwie funkcje wzajemnie cykliczne.</span><span class="sxs-lookup"><span data-stu-id="7adb4-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="7adb4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7adb4-117">See also</span></span>

- [<span data-ttu-id="7adb4-118">Funkcje</span><span class="sxs-lookup"><span data-stu-id="7adb4-118">Functions</span></span>](index.md)
