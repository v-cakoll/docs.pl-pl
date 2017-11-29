---
title: "Funkcje rekursywne: rec — Słowo kluczowe (F#)"
description: "Dowiedz się, jak użyć słowa kluczowego \"rec\" F # przy użyciu słowa kluczowego \"let\", aby zdefiniować funkcję rekursywną."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1a95639f-9bfe-4f1d-a5e2-246d1d37776e
ms.openlocfilehash: b837d2c0f8e2b1d28980620103097ccc8345c098
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="58bb5-104">Funkcje rekursywne: rec — Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="58bb5-104">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="58bb5-105">`rec` — Słowo kluczowe jest używany razem z `let` słowo kluczowe, aby zdefiniować funkcję rekursywną.</span><span class="sxs-lookup"><span data-stu-id="58bb5-105">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>


## <a name="syntax"></a><span data-ttu-id="58bb5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="58bb5-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="58bb5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58bb5-107">Remarks</span></span>
<span data-ttu-id="58bb5-108">Funkcje rekursywne, funkcje, które wywołują się, są identyfikowane jawnie w języku F #.</span><span class="sxs-lookup"><span data-stu-id="58bb5-108">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="58bb5-109">To udostępnienie identyfikatorem, który jest definiowany w zakresie funkcji.</span><span class="sxs-lookup"><span data-stu-id="58bb5-109">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="58bb5-110">Poniższy kod przedstawia funkcję rekursywną, który oblicza  *n* th Fibonacci numer.</span><span class="sxs-lookup"><span data-stu-id="58bb5-110">The following code illustrates a recursive function that computes the *n*th Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="58bb5-111">W praktyce tak jak w powyższym kodzie jest niepotrzebne z pamięci i czasu procesora, ponieważ obejmuje ona więc ich ponownego obliczania wcześniej obliczanej wartości.</span><span class="sxs-lookup"><span data-stu-id="58bb5-111">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>


<span data-ttu-id="58bb5-112">Metody są niejawnie cykliczne w obrębie typu; nie istnieje potrzeba aby dodać `rec` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="58bb5-112">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="58bb5-113">Powiązania Let w klasach nie są niejawnie cyklicznego.</span><span class="sxs-lookup"><span data-stu-id="58bb5-113">Let bindings within classes are not implicitly recursive.</span></span>


## <a name="mutually-recursive-functions"></a><span data-ttu-id="58bb5-114">Funkcje wzajemnie rekurencyjne</span><span class="sxs-lookup"><span data-stu-id="58bb5-114">Mutually Recursive Functions</span></span>
<span data-ttu-id="58bb5-115">Czasami funkcje są *wzajemnie rekursywne*, co oznacza, że wywołania tworzą koło, gdzie jedna funkcja wywołuje inny, która z kolei wywołuje pierwsza strona, z dowolną liczbę wywołań między nimi.</span><span class="sxs-lookup"><span data-stu-id="58bb5-115">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="58bb5-116">Takie funkcje musi definiować razem w jednym `let` powiązanie, używając `and` — słowo kluczowe do nawiązania połączenia ze sobą.</span><span class="sxs-lookup"><span data-stu-id="58bb5-116">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="58bb5-117">Poniższy przykład przedstawia dwa wzajemnie funkcje rekursywne.</span><span class="sxs-lookup"><span data-stu-id="58bb5-117">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="58bb5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58bb5-118">See Also</span></span>
[<span data-ttu-id="58bb5-119">Funkcje</span><span class="sxs-lookup"><span data-stu-id="58bb5-119">Functions</span></span>](index.md)
