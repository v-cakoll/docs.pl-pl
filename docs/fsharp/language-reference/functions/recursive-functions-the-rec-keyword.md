---
title: 'Funkcje rekursywne: rec — Słowo kluczowe (F#)'
description: 'Dowiedz się, jak użyć słowa kluczowego "rec" F # za pomocą słowa kluczowego "let", do definiowania funkcji recursive.'
ms.date: 05/16/2016
ms.openlocfilehash: 5aab6ed8ab0fc3c0f0bcfc93c3ce6518ec53254f
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44336514"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="1789a-103">Funkcje rekursywne: rec — Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="1789a-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="1789a-104">`rec` — Słowo kluczowe jest używany razem z `let` — słowo kluczowe do definiowania funkcji recursive.</span><span class="sxs-lookup"><span data-stu-id="1789a-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="1789a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1789a-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="1789a-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1789a-106">Remarks</span></span>

<span data-ttu-id="1789a-107">Funkcje rekursywne, funkcje, które wywołują się, są identyfikowane jawnie w języku F #.</span><span class="sxs-lookup"><span data-stu-id="1789a-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="1789a-108">Spowoduje to udostępnienie identyfikator, który jest definiowany w zakresie funkcji.</span><span class="sxs-lookup"><span data-stu-id="1789a-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="1789a-109">Poniższy kod ilustruje funkcji recursive, które oblicza *n*<sup>th</sup> Fibonacci numer.</span><span class="sxs-lookup"><span data-stu-id="1789a-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="1789a-110">W praktyce tak jak w powyższym kodzie jest marnotrawstwa czasu pamięci i procesora, ponieważ spowodowałoby to przeprowadzanie ponownego obliczania wcześniej obliczanej wartości.</span><span class="sxs-lookup"><span data-stu-id="1789a-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>

<span data-ttu-id="1789a-111">Metody są niejawnie cykliczne w obrębie typu; nie ma potrzeby można dodać `rec` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1789a-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="1789a-112">Powiązania Let w klasach nie są niejawnie cykliczne.</span><span class="sxs-lookup"><span data-stu-id="1789a-112">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="1789a-113">Funkcje wzajemnie rekursywne</span><span class="sxs-lookup"><span data-stu-id="1789a-113">Mutually Recursive Functions</span></span>

<span data-ttu-id="1789a-114">Funkcje są czasami *wzajemnie cyklicznego*, co oznacza, że wywołania tworzą koła, gdzie jedna funkcja wywołuje drugą która z kolei wywołuje pierwsza strona, z dowolnej liczby wywołań między.</span><span class="sxs-lookup"><span data-stu-id="1789a-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="1789a-115">Takie funkcje, należy zdefiniować razem do jednej `let` powiązania, za pomocą `and` — słowo kluczowe, aby połączyć je ze sobą.</span><span class="sxs-lookup"><span data-stu-id="1789a-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="1789a-116">W poniższym przykładzie przedstawiono dwóch wzajemnie funkcji rekursywnych.</span><span class="sxs-lookup"><span data-stu-id="1789a-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="1789a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1789a-117">See also</span></span>

- [<span data-ttu-id="1789a-118">Funkcje</span><span class="sxs-lookup"><span data-stu-id="1789a-118">Functions</span></span>](index.md)
