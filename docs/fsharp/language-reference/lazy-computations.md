---
title: Obliczenia powolne (F#)
description: 'Dowiedz się, jak poprawić wydajność aplikacji i bibliotek obliczenia powolne F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 1c4eb6ab247c44a04a9d145185e2de7ec01b8e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563935"
---
# <a name="lazy-computations"></a><span data-ttu-id="addfa-103">Obliczenia powolne</span><span class="sxs-lookup"><span data-stu-id="addfa-103">Lazy Computations</span></span>

<span data-ttu-id="addfa-104">*Obliczenia powolne* są obliczenia, które nie są oceniane natychmiast, ale zamiast tego są oceniane, gdy potrzebny jest wynik.</span><span class="sxs-lookup"><span data-stu-id="addfa-104">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="addfa-105">To może pomóc zwiększyć wydajność kodu.</span><span class="sxs-lookup"><span data-stu-id="addfa-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="addfa-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="addfa-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="addfa-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="addfa-107">Remarks</span></span>

<span data-ttu-id="addfa-108">W poprzednich składni *wyrażenie* jest kod, który jest oceniane tylko wtedy, gdy wynik jest wymagana, i *identyfikator* to wartość, która zapisuje wynik.</span><span class="sxs-lookup"><span data-stu-id="addfa-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="addfa-109">Wartość jest typu [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), gdzie rzeczywisty typ, które służy do `'T` jest określana na podstawie wyniku wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="addfa-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="addfa-110">Obliczenia powolne pozwalają poprawić wydajność przez ograniczenie wykonywania obliczeń w sytuacjach, w których wynikiem jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="addfa-110">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="addfa-111">Aby wymusić obliczeń do wykonania, należy wywołać metodę `Force`.</span><span class="sxs-lookup"><span data-stu-id="addfa-111">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="addfa-112">`Force` powoduje wykonanie zostać wykonana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="addfa-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="addfa-113">Kolejne wywołania `Force` zwracać taki sam wyniku, ale nie wykonuje żadnego kodu.</span><span class="sxs-lookup"><span data-stu-id="addfa-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="addfa-114">Poniższy kod ilustruje korzystanie z opóźnieniem obliczania i stosowania `Force`.</span><span class="sxs-lookup"><span data-stu-id="addfa-114">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="addfa-115">W tym kodzie typ `result` jest `Lazy<int>`i `Force` metoda zwraca `int`.</span><span class="sxs-lookup"><span data-stu-id="addfa-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="addfa-116">Obliczanie leniwe, ale nie `Lazy` wpisz, służy także do sekwencji.</span><span class="sxs-lookup"><span data-stu-id="addfa-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="addfa-117">Aby uzyskać więcej informacji, zobacz [sekwencji](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="addfa-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="addfa-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="addfa-118">See Also</span></span>

[<span data-ttu-id="addfa-119">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="addfa-119">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="addfa-120">Lazyextensions — moduł</span><span class="sxs-lookup"><span data-stu-id="addfa-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
