---
title: operator-= — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 3b6890be4460a599a5d2f5f5f6ee1627be933f0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688686"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="f5328-102">-= — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="f5328-102">-= operator (C# Reference)</span></span>

<span data-ttu-id="f5328-103">Operator przypisania odejmowania.</span><span class="sxs-lookup"><span data-stu-id="f5328-103">The subtraction assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5328-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5328-104">Remarks</span></span>

<span data-ttu-id="f5328-105">Wyrażenie używające operatora przypisania `-=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="f5328-105">An expression using the `-=` assignment operator, such as</span></span>

```csharp
x -= y
```

 <span data-ttu-id="f5328-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="f5328-106">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="f5328-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="f5328-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f5328-108">Znaczenie [-operator](subtraction-operator.md) jest zależny od typów `x` i `y` (odejmowania w przypadku argumentów operacji numerycznych, delegowanie usuwania w przypadku argumentów operacji delegata i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="f5328-108">The meaning of the [- operator](subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>

<span data-ttu-id="f5328-109">`-=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [-operator](subtraction-operator.md) (zobacz [operator](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f5328-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](subtraction-operator.md) (see [operator](../keywords/operator.md)).</span></span>

<span data-ttu-id="f5328-110">-= Operator jest również używany w języku C# można anulować subskrypcję zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f5328-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="f5328-111">Aby uzyskać więcej informacji, zobacz [jak: Subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="f5328-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="f5328-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5328-112">Example</span></span>

[!code-csharp[csRefOperators#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#6)]

## <a name="see-also"></a><span data-ttu-id="f5328-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5328-113">See also</span></span>

- [<span data-ttu-id="f5328-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f5328-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f5328-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f5328-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f5328-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="f5328-116">C# operators</span></span>](index.md)
