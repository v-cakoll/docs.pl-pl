---
title: Wyrażenia z opóźnieniem
description: Dowiedz się, jak F# z opóźnieniem wyrażeń może zwiększyć wydajność aplikacji i bibliotek.
ms.date: 03/13/2019
ms.openlocfilehash: 6d53d53093f4e93f53e1c956b94e2f1e4a1bbd55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904114"
---
# <a name="lazy-expressions"></a><span data-ttu-id="d31bd-103">Wyrażenia z opóźnieniem</span><span class="sxs-lookup"><span data-stu-id="d31bd-103">Lazy Expressions</span></span>

<span data-ttu-id="d31bd-104">*Wyrażenia z opóźnieniem* są wyrażeniami, które nie są oceniane natychmiast, ale zamiast tego są oceniane, gdy wynik jest potrzebny.</span><span class="sxs-lookup"><span data-stu-id="d31bd-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="d31bd-105">Może to pomóc poprawić wydajność kodu.</span><span class="sxs-lookup"><span data-stu-id="d31bd-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="d31bd-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d31bd-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="d31bd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d31bd-107">Remarks</span></span>

<span data-ttu-id="d31bd-108">W poprzedniej składni *wyrażenie* kodu, które jest oceniane tylko wtedy, gdy wynik jest wymagane, i *identyfikator* jest wartością, która zapisuje wynik.</span><span class="sxs-lookup"><span data-stu-id="d31bd-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="d31bd-109">Wartość jest typu [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), gdy faktyczny typ, które służy do `'T` jest określana na podstawie wynik wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d31bd-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="d31bd-110">Wyrażenia z opóźnieniem umożliwiają poprawianie wydajności poprzez ograniczenie wykonywania wyrażenia do sytuacji, w których wynikiem jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d31bd-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="d31bd-111">Aby wymusić wyrażenia do wykonania, należy wywołać metodę `Force`.</span><span class="sxs-lookup"><span data-stu-id="d31bd-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="d31bd-112">`Force` powoduje wykonanie można wykonać tylko jeden raz.</span><span class="sxs-lookup"><span data-stu-id="d31bd-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="d31bd-113">Kolejne wywołania `Force` zwracać taki sam wynik, ale nie wykonać żadnego kodu.</span><span class="sxs-lookup"><span data-stu-id="d31bd-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="d31bd-114">Poniższy kod ilustruje użycie wyrażenia z opóźnieniem i umożliwia korzystanie z `Force`.</span><span class="sxs-lookup"><span data-stu-id="d31bd-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="d31bd-115">W tym kodzie typ `result` jest `Lazy<int>`i `Force` metoda zwraca `int`.</span><span class="sxs-lookup"><span data-stu-id="d31bd-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="d31bd-116">Obliczanie z opóźnieniem, ale nie `Lazy` typu, jest również używany w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="d31bd-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="d31bd-117">Aby uzyskać więcej informacji, zobacz [sekwencje](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="d31bd-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d31bd-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d31bd-118">See also</span></span>

- [<span data-ttu-id="d31bd-119">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="d31bd-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="d31bd-120">Lazyextensions — moduł</span><span class="sxs-lookup"><span data-stu-id="d31bd-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
