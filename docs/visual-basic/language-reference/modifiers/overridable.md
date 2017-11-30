---
title: Overridable (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f7d5dd33f8591be1b4305e954e55e035882626c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="e739c-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e739c-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="e739c-103">Określa, że właściwość lub procedura może być zastąpiona przez o identycznej nazwie właściwość lub procedura w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="e739c-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e739c-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e739c-104">Remarks</span></span>  
 <span data-ttu-id="e739c-105">`Overridable` Modyfikator umożliwia właściwości lub metody w klasie do zastąpienia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="e739c-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="e739c-106">[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modyfikator zapobiega zastępowaniu w klasie pochodnej właściwości lub metody.</span><span class="sxs-lookup"><span data-stu-id="e739c-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="e739c-107">Aby uzyskać więcej informacji, zobacz [podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="e739c-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="e739c-108">Jeśli `Overridable` lub `NotOverridable` modyfikator nie zostanie określony, domyślnie zależy od tego, czy właściwości lub metody zastępuje właściwości klasy podstawowej lub metody.</span><span class="sxs-lookup"><span data-stu-id="e739c-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="e739c-109">Jeśli właściwość lub metoda zastępuje właściwości klasy podstawowej lub metody, ustawienie domyślne to `Overridable`; w przeciwnym razie jest `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="e739c-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="e739c-110">Można w tle lub zastąpienie do ponownego zdefiniowania odziedziczonego elementu, ale są istotne różnice między dwa podejścia.</span><span class="sxs-lookup"><span data-stu-id="e739c-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="e739c-111">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="e739c-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="e739c-112">Element, który może zostać zastąpiona jest czasami nazywany *wirtualnego* elementu.</span><span class="sxs-lookup"><span data-stu-id="e739c-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="e739c-113">Jeśli może zostać zastąpiona, ale nie musi być, czasem nazywana jest również *konkretnych* elementu.</span><span class="sxs-lookup"><span data-stu-id="e739c-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="e739c-114">Można użyć `Overridable` tylko w instrukcji deklaracji właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="e739c-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="e739c-115">Modyfikatory połączone</span><span class="sxs-lookup"><span data-stu-id="e739c-115">Combined Modifiers</span></span>  
 <span data-ttu-id="e739c-116">Nie można określić `Overridable` lub `NotOverridable` dla `Private` metody.</span><span class="sxs-lookup"><span data-stu-id="e739c-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="e739c-117">Nie można określić `Overridable` razem z `MustOverride`, `NotOverridable`, lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="e739c-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="e739c-118">Zastępowanie elementu jest niejawnie możliwym do zastąpienia, nie można łączyć `Overridable` z `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="e739c-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="e739c-119">Użycie</span><span class="sxs-lookup"><span data-stu-id="e739c-119">Usage</span></span>  
 <span data-ttu-id="e739c-120">`Overridable` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="e739c-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e739c-121">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e739c-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="e739c-122">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e739c-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="e739c-123">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e739c-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e739c-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e739c-124">See Also</span></span>  
 [<span data-ttu-id="e739c-125">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="e739c-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)  
 [<span data-ttu-id="e739c-126">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="e739c-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="e739c-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="e739c-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="e739c-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="e739c-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="e739c-129">Zastąpienia</span><span class="sxs-lookup"><span data-stu-id="e739c-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="e739c-130">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e739c-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="e739c-131">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e739c-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
