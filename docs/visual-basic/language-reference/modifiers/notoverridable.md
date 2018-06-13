---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: 3fae1a4b587c379dbc459cbc973982851e713785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600756"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="b41d0-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b41d0-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="b41d0-103">Określa, że właściwość lub procedura nie można zastąpić w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b41d0-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b41d0-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b41d0-104">Remarks</span></span>  
 <span data-ttu-id="b41d0-105">`NotOverridable` Modyfikator zapobiega zastępowaniu w klasie pochodnej właściwości lub metody.</span><span class="sxs-lookup"><span data-stu-id="b41d0-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="b41d0-106">[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modyfikator umożliwia właściwości lub metody w klasie do zastąpienia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b41d0-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="b41d0-107">Aby uzyskać więcej informacji, zobacz [podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="b41d0-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="b41d0-108">Jeśli `Overridable` lub `NotOverridable` modyfikator nie zostanie określony, domyślnie zależy od tego, czy właściwości lub metody zastępuje właściwości klasy podstawowej lub metody.</span><span class="sxs-lookup"><span data-stu-id="b41d0-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="b41d0-109">Jeśli właściwość lub metoda zastępuje właściwości klasy podstawowej lub metody, ustawienie domyślne to `Overridable`; w przeciwnym razie jest `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="b41d0-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="b41d0-110">Nie można zastąpić element jest czasami nazywany *zapieczętowanego* elementu.</span><span class="sxs-lookup"><span data-stu-id="b41d0-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="b41d0-111">Można użyć `NotOverridable` tylko w instrukcji deklaracji właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="b41d0-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="b41d0-112">Można określić `NotOverridable` tylko na właściwość lub procedura, która zastępuje inną właściwość lub procedura, oznacza to, że tylko w połączeniu z `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="b41d0-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="b41d0-113">Modyfikatory połączone</span><span class="sxs-lookup"><span data-stu-id="b41d0-113">Combined Modifiers</span></span>  
 <span data-ttu-id="b41d0-114">Nie można określić `Overridable` lub `NotOverridable` dla `Private` metody.</span><span class="sxs-lookup"><span data-stu-id="b41d0-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="b41d0-115">Nie można określić `NotOverridable` razem z `MustOverride`, `Overridable`, lub `Shared` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="b41d0-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="b41d0-116">Użycie</span><span class="sxs-lookup"><span data-stu-id="b41d0-116">Usage</span></span>  
 <span data-ttu-id="b41d0-117">`NotOverridable` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="b41d0-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="b41d0-118">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b41d0-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="b41d0-119">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b41d0-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="b41d0-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b41d0-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b41d0-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b41d0-121">See Also</span></span>  
 [<span data-ttu-id="b41d0-122">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="b41d0-122">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)  
 [<span data-ttu-id="b41d0-123">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="b41d0-123">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="b41d0-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="b41d0-124">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="b41d0-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="b41d0-125">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="b41d0-126">Overrides</span><span class="sxs-lookup"><span data-stu-id="b41d0-126">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="b41d0-127">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b41d0-127">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="b41d0-128">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b41d0-128">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
