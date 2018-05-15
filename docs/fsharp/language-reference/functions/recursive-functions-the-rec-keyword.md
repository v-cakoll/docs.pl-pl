---
title: 'Funkcje rekursywne: rec — Słowo kluczowe (F#)'
description: 'Dowiedz się, jak użyć słowa kluczowego "rec" F # przy użyciu słowa kluczowego "let", aby zdefiniować funkcję rekursywną.'
ms.date: 05/16/2016
ms.openlocfilehash: 6039a48eae2b16aa1d82617176460d727a878d87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="78167-103">Funkcje rekursywne: rec — Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="78167-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="78167-104">`rec` — Słowo kluczowe jest używany razem z `let` słowo kluczowe, aby zdefiniować funkcję rekursywną.</span><span class="sxs-lookup"><span data-stu-id="78167-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>


## <a name="syntax"></a><span data-ttu-id="78167-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="78167-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="78167-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78167-106">Remarks</span></span>
<span data-ttu-id="78167-107">Funkcje rekursywne, funkcje, które wywołują się, są identyfikowane jawnie w języku F #.</span><span class="sxs-lookup"><span data-stu-id="78167-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="78167-108">To udostępnienie identyfikatorem, który jest definiowany w zakresie funkcji.</span><span class="sxs-lookup"><span data-stu-id="78167-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="78167-109">Poniższy kod przedstawia funkcję rekursywną, który oblicza *n*th Fibonacci numer.</span><span class="sxs-lookup"><span data-stu-id="78167-109">The following code illustrates a recursive function that computes the *n*th Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="78167-110">W praktyce tak jak w powyższym kodzie jest niepotrzebne z pamięci i czasu procesora, ponieważ obejmuje ona więc ich ponownego obliczania wcześniej obliczanej wartości.</span><span class="sxs-lookup"><span data-stu-id="78167-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>


<span data-ttu-id="78167-111">Metody są niejawnie cykliczne w obrębie typu; nie istnieje potrzeba aby dodać `rec` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="78167-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="78167-112">Powiązania Let w klasach nie są niejawnie cyklicznego.</span><span class="sxs-lookup"><span data-stu-id="78167-112">Let bindings within classes are not implicitly recursive.</span></span>


## <a name="mutually-recursive-functions"></a><span data-ttu-id="78167-113">Funkcje wzajemnie rekurencyjne</span><span class="sxs-lookup"><span data-stu-id="78167-113">Mutually Recursive Functions</span></span>
<span data-ttu-id="78167-114">Czasami funkcje są *wzajemnie rekursywne*, co oznacza, że wywołania tworzą koło, gdzie jedna funkcja wywołuje inny, która z kolei wywołuje pierwsza strona, z dowolną liczbę wywołań między nimi.</span><span class="sxs-lookup"><span data-stu-id="78167-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="78167-115">Takie funkcje musi definiować razem w jednym `let` powiązanie, używając `and` — słowo kluczowe do nawiązania połączenia ze sobą.</span><span class="sxs-lookup"><span data-stu-id="78167-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="78167-116">Poniższy przykład przedstawia dwa wzajemnie funkcje rekursywne.</span><span class="sxs-lookup"><span data-stu-id="78167-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="78167-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78167-117">See Also</span></span>
[<span data-ttu-id="78167-118">Funkcje</span><span class="sxs-lookup"><span data-stu-id="78167-118">Functions</span></span>](index.md)
