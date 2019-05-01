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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920760"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="51bd6-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51bd6-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="51bd6-103">Określa, że właściwość lub procedura nie jest zaimplementowana w tej klasie i musi zostać zastąpiona w klasie pochodnej, zanim będzie można jej używać.</span><span class="sxs-lookup"><span data-stu-id="51bd6-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51bd6-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51bd6-104">Remarks</span></span>  
 <span data-ttu-id="51bd6-105">Możesz użyć `MustOverride` tylko w instrukcji deklaracji właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="51bd6-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="51bd6-106">Właściwość lub procedura, która określa `MustOverride` musi należeć do klasy, a klasy muszą być oznaczone jako [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="51bd6-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="51bd6-107">reguły</span><span class="sxs-lookup"><span data-stu-id="51bd6-107">Rules</span></span>  
  
- <span data-ttu-id="51bd6-108">**Deklaracja niekompletne.**</span><span class="sxs-lookup"><span data-stu-id="51bd6-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="51bd6-109">Po określeniu `MustOverride`, nie trzeba dostarczać żadnych dodatkowych wierszy kodu właściwość lub procedura, nie nawet `End Function`, `End Property`, lub `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="51bd6-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="51bd6-110">**Modyfikatory połączone.**</span><span class="sxs-lookup"><span data-stu-id="51bd6-110">**Combined Modifiers.**</span></span> <span data-ttu-id="51bd6-111">Nie można określić `MustOverride` wraz z `NotOverridable`, `Overridable`, lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="51bd6-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="51bd6-112">**Przesłanianiem i zastępowaniem.**</span><span class="sxs-lookup"><span data-stu-id="51bd6-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="51bd6-113">Zarówno przesłanianiem i zastępowaniem przedefiniować dziedziczonego elementu, ale istnieją znaczne różnice między dwa podejścia.</span><span class="sxs-lookup"><span data-stu-id="51bd6-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="51bd6-114">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="51bd6-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="51bd6-115">**Alternatywne warunki.**</span><span class="sxs-lookup"><span data-stu-id="51bd6-115">**Alternate Terms.**</span></span> <span data-ttu-id="51bd6-116">Element, którego nie można użyć z wyjątkiem w zastąpieniu jest czasami nazywane *czystej wirtualnej* elementu.</span><span class="sxs-lookup"><span data-stu-id="51bd6-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="51bd6-117">`MustOverride` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="51bd6-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="51bd6-118">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="51bd6-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="51bd6-119">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="51bd6-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="51bd6-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="51bd6-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="51bd6-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51bd6-121">See also</span></span>

- [<span data-ttu-id="51bd6-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="51bd6-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="51bd6-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="51bd6-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="51bd6-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="51bd6-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="51bd6-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="51bd6-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="51bd6-126">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="51bd6-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="51bd6-127">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="51bd6-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
