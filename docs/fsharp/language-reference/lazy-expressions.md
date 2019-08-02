---
title: Wyrażenia z opóźnionym obliczaniem
description: Dowiedz F# się, jak wyrażenia z opóźnieniem mogą zwiększyć wydajność aplikacji i bibliotek.
ms.date: 03/13/2019
ms.openlocfilehash: 97429e9a4c3838cbaa2ead197db4443e0820e8b3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630741"
---
# <a name="lazy-expressions"></a><span data-ttu-id="38107-103">Wyrażenia z opóźnionym obliczaniem</span><span class="sxs-lookup"><span data-stu-id="38107-103">Lazy Expressions</span></span>

<span data-ttu-id="38107-104">*Wyrażenia* z opóźnieniem to wyrażenia, które nie są obliczane natychmiast, ale zamiast tego są oceniane, gdy wynik jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="38107-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="38107-105">Może to pomóc poprawić wydajność kodu.</span><span class="sxs-lookup"><span data-stu-id="38107-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="38107-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="38107-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="38107-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38107-107">Remarks</span></span>

<span data-ttu-id="38107-108">W poprzedniej składni *wyrażenie* ma kod, który jest oceniany tylko wtedy, gdy wynik jest wymagany, a *Identyfikator* jest wartością, która przechowuje wynik.</span><span class="sxs-lookup"><span data-stu-id="38107-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="38107-109">Wartość jest typu [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), gdzie rzeczywisty typ, który jest używany dla `'T` , jest określany na podstawie wyniku wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="38107-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="38107-110">Wyrażenia z opóźnieniem umożliwiają poprawienie wydajności przez ograniczenie wykonywania wyrażeń tylko do tych sytuacji, w których jest wymagany wynik.</span><span class="sxs-lookup"><span data-stu-id="38107-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="38107-111">Aby wymusić wykonywanie wyrażeń, należy wywołać metodę `Force`.</span><span class="sxs-lookup"><span data-stu-id="38107-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="38107-112">`Force`powoduje, że wykonywanie wykonuje się tylko jeden raz.</span><span class="sxs-lookup"><span data-stu-id="38107-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="38107-113">Kolejne wywołania `Force` zwracają ten sam wynik, ale nie wykonują żadnego kodu.</span><span class="sxs-lookup"><span data-stu-id="38107-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="38107-114">Poniższy kod ilustruje użycie wyrażeń z opóźnieniem i użycie `Force`.</span><span class="sxs-lookup"><span data-stu-id="38107-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="38107-115">W tym kodzie `result` typ jest `Lazy<int>`, `Force` a metoda zwraca. `int`</span><span class="sxs-lookup"><span data-stu-id="38107-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="38107-116">Ocena z opóźnieniem, ale `Lazy` nie typ, jest również używana dla sekwencji.</span><span class="sxs-lookup"><span data-stu-id="38107-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="38107-117">Aby uzyskać więcej informacji, [](sequences.md)Zobacz sekwencje.</span><span class="sxs-lookup"><span data-stu-id="38107-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38107-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38107-118">See also</span></span>

- [<span data-ttu-id="38107-119">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="38107-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="38107-120">Moduł LazyExtensions</span><span class="sxs-lookup"><span data-stu-id="38107-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
