---
title: Overridable (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 7002589b303c41b26b611588f339fa70dd19f959
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537598"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="bd543-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd543-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="bd543-103">Określa, że właściwość lub procedura może być zastąpione o identycznej nazwie właściwość lub procedura w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="bd543-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd543-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd543-104">Remarks</span></span>  
 <span data-ttu-id="bd543-105">`Overridable` Modyfikator umożliwia właściwość lub metoda klasy został nadpisany w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="bd543-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="bd543-106">[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modyfikator zapobiega zastępowaniu w klasie pochodnej właściwości lub metody.</span><span class="sxs-lookup"><span data-stu-id="bd543-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="bd543-107">Aby uzyskać więcej informacji, zobacz [podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="bd543-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="bd543-108">Jeśli `Overridable` lub `NotOverridable` modyfikator nie zostanie określony, domyślnie zależy od tego, czy właściwość lub metoda zastępuje właściwości klasy bazowej lub metody.</span><span class="sxs-lookup"><span data-stu-id="bd543-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="bd543-109">Jeśli właściwość lub metoda zastępuje właściwości klasy bazowej lub metody, domyślne ustawienie to `Overridable`; w przeciwnym razie jest `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="bd543-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="bd543-110">Można w tle lub Przesłoń, aby zdefiniować dziedziczonego elementu, ale istnieją znaczne różnice między dwa podejścia.</span><span class="sxs-lookup"><span data-stu-id="bd543-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="bd543-111">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="bd543-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="bd543-112">Element, który może zostać przesłonięta jest czasami określane jako *wirtualnego* elementu.</span><span class="sxs-lookup"><span data-stu-id="bd543-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="bd543-113">Jeśli może zostać zastąpiona, ale nie musi być, niekiedy nazywanych również *konkretnych* elementu.</span><span class="sxs-lookup"><span data-stu-id="bd543-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="bd543-114">Możesz użyć `Overridable` tylko w instrukcji deklaracji właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="bd543-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="bd543-115">Modyfikatory połączone</span><span class="sxs-lookup"><span data-stu-id="bd543-115">Combined Modifiers</span></span>  
 <span data-ttu-id="bd543-116">Nie można określić `Overridable` lub `NotOverridable` dla `Private` metody.</span><span class="sxs-lookup"><span data-stu-id="bd543-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="bd543-117">Nie można określić `Overridable` wraz z `MustOverride`, `NotOverridable`, lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="bd543-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="bd543-118">Ponieważ element nadrzędnych jest niejawnie możliwym do zastąpienia, nie można połączyć `Overridable` z `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="bd543-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="bd543-119">Użycie</span><span class="sxs-lookup"><span data-stu-id="bd543-119">Usage</span></span>  
 <span data-ttu-id="bd543-120">`Overridable` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="bd543-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="bd543-121">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bd543-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="bd543-122">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="bd543-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="bd543-123">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bd543-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="bd543-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd543-124">See also</span></span>
- [<span data-ttu-id="bd543-125">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="bd543-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="bd543-126">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="bd543-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="bd543-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="bd543-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="bd543-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="bd543-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="bd543-129">Overrides</span><span class="sxs-lookup"><span data-stu-id="bd543-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="bd543-130">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="bd543-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="bd543-131">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd543-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
