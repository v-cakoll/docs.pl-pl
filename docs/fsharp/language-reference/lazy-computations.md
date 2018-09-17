---
title: Obliczenia powolne (F#)
description: 'Dowiedz się, jak poprawić wydajność aplikacji i bibliotek obliczenia powolne F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 8afe815f26978de96291a52973d54a9dbcc5eaf2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698213"
---
# <a name="lazy-computations"></a><span data-ttu-id="c55f4-103">Obliczenia powolne</span><span class="sxs-lookup"><span data-stu-id="c55f4-103">Lazy Computations</span></span>

<span data-ttu-id="c55f4-104">*Obliczenia powolne* są obliczeń, które nie są oceniane natychmiast, ale zamiast tego są oceniane, gdy wynik jest potrzebny.</span><span class="sxs-lookup"><span data-stu-id="c55f4-104">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="c55f4-105">Może to pomóc poprawić wydajność kodu.</span><span class="sxs-lookup"><span data-stu-id="c55f4-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="c55f4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c55f4-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="c55f4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c55f4-107">Remarks</span></span>

<span data-ttu-id="c55f4-108">W poprzedniej składni *wyrażenie* kodu, które jest oceniane tylko wtedy, gdy wynik jest wymagane, i *identyfikator* jest wartością, która zapisuje wynik.</span><span class="sxs-lookup"><span data-stu-id="c55f4-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="c55f4-109">Wartość jest typu [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), gdy faktyczny typ, które służy do `'T` jest określana na podstawie wynik wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c55f4-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="c55f4-110">Obliczenia powolne pozwalają zwiększyć wydajność przez ograniczenie możliwości wykonywania wykonywania obliczeń do sytuacji, w których wynikiem jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="c55f4-110">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="c55f4-111">Aby wymusić obliczenie, które mają zostać wykonane, należy wywołać metodę `Force`.</span><span class="sxs-lookup"><span data-stu-id="c55f4-111">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="c55f4-112">`Force` powoduje wykonanie można wykonać tylko jeden raz.</span><span class="sxs-lookup"><span data-stu-id="c55f4-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="c55f4-113">Kolejne wywołania `Force` zwracać taki sam wynik, ale nie wykonać żadnego kodu.</span><span class="sxs-lookup"><span data-stu-id="c55f4-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="c55f4-114">Poniższy kod ilustruje użycie obliczanie z opóźnieniem i umożliwia korzystanie z `Force`.</span><span class="sxs-lookup"><span data-stu-id="c55f4-114">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="c55f4-115">W tym kodzie typ `result` jest `Lazy<int>`i `Force` metoda zwraca `int`.</span><span class="sxs-lookup"><span data-stu-id="c55f4-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="c55f4-116">Obliczanie z opóźnieniem, ale nie `Lazy` typu, jest również używany w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c55f4-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="c55f4-117">Aby uzyskać więcej informacji, zobacz [sekwencje](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="c55f4-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c55f4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c55f4-118">See also</span></span>

- [<span data-ttu-id="c55f4-119">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="c55f4-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c55f4-120">Lazyextensions — moduł</span><span class="sxs-lookup"><span data-stu-id="c55f4-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
