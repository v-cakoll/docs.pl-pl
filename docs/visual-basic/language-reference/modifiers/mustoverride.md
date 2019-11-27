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
ms.openlocfilehash: dc6a153a604fd0e5cee9d7d46ebcd63294f33628
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351485"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="5263b-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5263b-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="5263b-103">Określa, że właściwość lub procedura nie jest zaimplementowana w tej klasie i musi zostać przesłonięta w klasie pochodnej, zanim będzie mogła zostać użyta.</span><span class="sxs-lookup"><span data-stu-id="5263b-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5263b-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5263b-104">Remarks</span></span>  
 <span data-ttu-id="5263b-105">`MustOverride` można użyć tylko w instrukcji deklaracji właściwości lub procedury.</span><span class="sxs-lookup"><span data-stu-id="5263b-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="5263b-106">Właściwość lub procedura, która określa `MustOverride` musi być elementem członkowskim klasy, a Klasa musi być oznaczona jako [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="5263b-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5263b-107">Reguły</span><span class="sxs-lookup"><span data-stu-id="5263b-107">Rules</span></span>  
  
- <span data-ttu-id="5263b-108">**Niekompletna deklaracja.**</span><span class="sxs-lookup"><span data-stu-id="5263b-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="5263b-109">Po określeniu `MustOverride`nie są dostarczane żadne dodatkowe wiersze kodu dla właściwości lub procedury, a nie nawet instrukcji `End Function`, `End Property`lub `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="5263b-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="5263b-110">**Połączone modyfikatory.**</span><span class="sxs-lookup"><span data-stu-id="5263b-110">**Combined Modifiers.**</span></span> <span data-ttu-id="5263b-111">Nie można określić `MustOverride` razem z `NotOverridable`, `Overridable`lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="5263b-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="5263b-112">**Przesłanianie i zastępowanie.**</span><span class="sxs-lookup"><span data-stu-id="5263b-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="5263b-113">Zarówno przesłanianie, jak i przesłonięcie przedefiniują Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami.</span><span class="sxs-lookup"><span data-stu-id="5263b-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="5263b-114">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="5263b-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="5263b-115">**Alternatywne warunki.**</span><span class="sxs-lookup"><span data-stu-id="5263b-115">**Alternate Terms.**</span></span> <span data-ttu-id="5263b-116">Element, którego nie można użyć z wyjątkiem przesłonięcia, jest czasami nazywany *czystym elementem wirtualnym* .</span><span class="sxs-lookup"><span data-stu-id="5263b-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="5263b-117">Modyfikator `MustOverride` może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="5263b-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="5263b-118">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5263b-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="5263b-119">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5263b-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="5263b-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5263b-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5263b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5263b-121">See also</span></span>

- [<span data-ttu-id="5263b-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="5263b-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="5263b-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="5263b-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="5263b-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="5263b-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="5263b-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="5263b-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="5263b-126">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="5263b-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="5263b-127">Obserwowanie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5263b-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
