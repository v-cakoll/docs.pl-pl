---
title: MustOverride (Visual Basic)
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
ms.openlocfilehash: 0ddd7d0d2a57afc02aa7483ba5e83b65c48af534
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822820"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="71081-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71081-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="71081-103">Określa, że właściwość lub procedura nie jest zaimplementowana w tej klasie i musi zostać zastąpiona w klasie pochodnej, zanim będzie można jej używać.</span><span class="sxs-lookup"><span data-stu-id="71081-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71081-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71081-104">Remarks</span></span>  
 <span data-ttu-id="71081-105">Możesz użyć `MustOverride` tylko w instrukcji deklaracji właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="71081-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="71081-106">Właściwość lub procedura, która określa `MustOverride` musi należeć do klasy, a klasy muszą być oznaczone jako [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="71081-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="71081-107">reguły</span><span class="sxs-lookup"><span data-stu-id="71081-107">Rules</span></span>  
  
-   <span data-ttu-id="71081-108">**Deklaracja niekompletne.**</span><span class="sxs-lookup"><span data-stu-id="71081-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="71081-109">Po określeniu `MustOverride`, nie trzeba dostarczać żadnych dodatkowych wierszy kodu właściwość lub procedura, nie nawet `End Function`, `End Property`, lub `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="71081-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="71081-110">**Modyfikatory połączone.**</span><span class="sxs-lookup"><span data-stu-id="71081-110">**Combined Modifiers.**</span></span> <span data-ttu-id="71081-111">Nie można określić `MustOverride` wraz z `NotOverridable`, `Overridable`, lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="71081-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
-   <span data-ttu-id="71081-112">**Przesłanianiem i zastępowaniem.**</span><span class="sxs-lookup"><span data-stu-id="71081-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="71081-113">Zarówno przesłanianiem i zastępowaniem przedefiniować dziedziczonego elementu, ale istnieją znaczne różnice między dwa podejścia.</span><span class="sxs-lookup"><span data-stu-id="71081-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="71081-114">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="71081-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
-   <span data-ttu-id="71081-115">**Alternatywne warunki.**</span><span class="sxs-lookup"><span data-stu-id="71081-115">**Alternate Terms.**</span></span> <span data-ttu-id="71081-116">Element, którego nie można użyć z wyjątkiem w zastąpieniu jest czasami nazywane *czystej wirtualnej* elementu.</span><span class="sxs-lookup"><span data-stu-id="71081-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="71081-117">`MustOverride` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="71081-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="71081-118">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="71081-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="71081-119">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="71081-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="71081-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="71081-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="71081-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71081-121">See also</span></span>

- [<span data-ttu-id="71081-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="71081-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="71081-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="71081-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="71081-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="71081-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="71081-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="71081-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="71081-126">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="71081-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="71081-127">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71081-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
