---
title: Overridable
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
ms.openlocfilehash: 9c639665fd92a56de6fb6e5147cda873ef457b45
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351400"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="6bcb4-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bcb4-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="6bcb4-103">Określa, że właściwość lub procedura może być zastąpiona przez właściwość lub procedurę o identycznej nazwie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6bcb4-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bcb4-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6bcb4-104">Remarks</span></span>  
 <span data-ttu-id="6bcb4-105">Modyfikator `Overridable` pozwala na zastąpienie właściwości lub metody w klasie klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6bcb4-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="6bcb4-106">Modyfikator [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) uniemożliwia przesłanianie właściwości lub metody w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6bcb4-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="6bcb4-107">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="6bcb4-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="6bcb4-108">Jeśli nie określono modyfikatora `Overridable` lub `NotOverridable`, domyślne ustawienie zależy od tego, czy właściwość lub metoda przesłania właściwość lub metodę klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="6bcb4-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="6bcb4-109">Jeśli właściwość lub metoda przesłania właściwość lub metodę klasy bazowej, ustawienie domyślne to `Overridable`; w przeciwnym razie jest `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="6bcb4-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="6bcb4-110">Można wykonać cień lub przesłonięcie, aby ponownie zdefiniować Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami.</span><span class="sxs-lookup"><span data-stu-id="6bcb4-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="6bcb4-111">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="6bcb4-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="6bcb4-112">Element, który może być przesłonięty, jest czasami nazywany elementem *wirtualnym* .</span><span class="sxs-lookup"><span data-stu-id="6bcb4-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="6bcb4-113">Jeśli może być zastąpiony, ale nie musi być, jest również czasami nazywane *konkretnym* elementem.</span><span class="sxs-lookup"><span data-stu-id="6bcb4-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="6bcb4-114">`Overridable` można użyć tylko w instrukcji deklaracji właściwości lub procedury.</span><span class="sxs-lookup"><span data-stu-id="6bcb4-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="6bcb4-115">Połączone Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="6bcb4-115">Combined Modifiers</span></span>  
 <span data-ttu-id="6bcb4-116">Nie można określić `Overridable` lub `NotOverridable` dla metody `Private`.</span><span class="sxs-lookup"><span data-stu-id="6bcb4-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="6bcb4-117">Nie można określić `Overridable` razem z `MustOverride`, `NotOverridable`lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="6bcb4-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="6bcb4-118">Ponieważ przesłaniający element jest niejawnie możliwy do zastąpienia, nie można połączyć `Overridable` z `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="6bcb4-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="6bcb4-119">Sposób użycia</span><span class="sxs-lookup"><span data-stu-id="6bcb4-119">Usage</span></span>  
 <span data-ttu-id="6bcb4-120">Modyfikator `Overridable` może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="6bcb4-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="6bcb4-121">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6bcb4-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="6bcb4-122">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6bcb4-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="6bcb4-123">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6bcb4-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6bcb4-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6bcb4-124">See also</span></span>

- [<span data-ttu-id="6bcb4-125">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="6bcb4-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="6bcb4-126">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="6bcb4-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="6bcb4-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="6bcb4-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="6bcb4-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="6bcb4-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="6bcb4-129">Overrides</span><span class="sxs-lookup"><span data-stu-id="6bcb4-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="6bcb4-130">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="6bcb4-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="6bcb4-131">Obserwowanie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6bcb4-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
