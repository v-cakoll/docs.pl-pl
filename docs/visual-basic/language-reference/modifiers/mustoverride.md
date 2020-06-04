---
title: MustOverride
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: 1b20108a2d42e82c0af7598fde8d60a08fea28ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396197"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="e911f-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e911f-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="e911f-103">Określa, że właściwość lub procedura nie jest zaimplementowana w tej klasie i musi zostać przesłonięta w klasie pochodnej, zanim będzie mogła zostać użyta.</span><span class="sxs-lookup"><span data-stu-id="e911f-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e911f-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e911f-104">Remarks</span></span>  
 <span data-ttu-id="e911f-105">Można użyć `MustOverride` tylko w instrukcji deklaracji właściwości lub procedury.</span><span class="sxs-lookup"><span data-stu-id="e911f-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="e911f-106">Właściwość lub procedura, która określa, `MustOverride` musi być elementem członkowskim klasy, a Klasa musi być oznaczona jako [MustInherit](mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="e911f-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e911f-107">Reguły</span><span class="sxs-lookup"><span data-stu-id="e911f-107">Rules</span></span>  
  
- <span data-ttu-id="e911f-108">**Niekompletna deklaracja.**</span><span class="sxs-lookup"><span data-stu-id="e911f-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="e911f-109">Jeśli określisz `MustOverride` , nie podasz żadnych dodatkowych wierszy kodu dla właściwości lub procedury, a nie `End Function` `End Property` instrukcji, lub `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="e911f-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="e911f-110">**Połączone modyfikatory.**</span><span class="sxs-lookup"><span data-stu-id="e911f-110">**Combined Modifiers.**</span></span> <span data-ttu-id="e911f-111">Nie można określić `MustOverride` razem z `NotOverridable` , `Overridable` , lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="e911f-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="e911f-112">**Przesłanianie i zastępowanie.**</span><span class="sxs-lookup"><span data-stu-id="e911f-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="e911f-113">Zarówno przesłanianie, jak i przesłonięcie przedefiniują Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami.</span><span class="sxs-lookup"><span data-stu-id="e911f-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="e911f-114">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="e911f-114">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="e911f-115">**Alternatywne warunki.**</span><span class="sxs-lookup"><span data-stu-id="e911f-115">**Alternate Terms.**</span></span> <span data-ttu-id="e911f-116">Element, którego nie można użyć z wyjątkiem przesłonięcia, jest czasami nazywany *czystym elementem wirtualnym* .</span><span class="sxs-lookup"><span data-stu-id="e911f-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="e911f-117">`MustOverride`Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="e911f-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e911f-118">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e911f-118">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="e911f-119">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="e911f-119">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="e911f-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e911f-120">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e911f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e911f-121">See also</span></span>

- [<span data-ttu-id="e911f-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="e911f-122">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="e911f-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="e911f-123">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="e911f-124">Przesłonięcia</span><span class="sxs-lookup"><span data-stu-id="e911f-124">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="e911f-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="e911f-125">MustInherit</span></span>](mustinherit.md)
- [<span data-ttu-id="e911f-126">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e911f-126">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="e911f-127">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e911f-127">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
