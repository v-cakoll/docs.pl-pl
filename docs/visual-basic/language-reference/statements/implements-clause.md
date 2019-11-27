---
title: Implements, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: f114aee75356e59eafd9d3ba6af9c64402cb374f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345872"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="f9413-102">Implements — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9413-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="f9413-103">Wskazuje, że składowa klasy lub struktury dostarcza implementację dla składowej zdefiniowanej w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="f9413-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9413-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9413-104">Remarks</span></span>  
<span data-ttu-id="f9413-105">Słowo kluczowe `Implements` nie jest takie samo jak [instrukcja Implements](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f9413-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="f9413-106">Użyj instrukcji `Implements`, aby określić, że Klasa lub struktura implementuje jeden lub więcej interfejsów, a następnie dla każdego elementu członkowskiego Użyj słowa kluczowego `Implements`, aby określić, który interfejs i który element członkowski implementuje.</span><span class="sxs-lookup"><span data-stu-id="f9413-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="f9413-107">Jeśli klasa lub struktura implementuje interfejs, musi on zawierać instrukcję `Implements` bezpośrednio po [instrukcji Class](../../../visual-basic/language-reference/statements/class-statement.md) lub [instrukcji Structure](../../../visual-basic/language-reference/statements/structure-statement.md)i musi implementować wszystkie elementy członkowskie zdefiniowane przez interfejs.</span><span class="sxs-lookup"><span data-stu-id="f9413-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="f9413-108">Reimplementacja</span><span class="sxs-lookup"><span data-stu-id="f9413-108">Reimplementation</span></span>  
<span data-ttu-id="f9413-109">W klasie pochodnej można wykonać ponowną implementację elementu członkowskiego interfejsu, który został już zaimplementowany przez klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="f9413-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="f9413-110">Różni się to od przesłaniania składowej klasy bazowej w następujących aspektach:</span><span class="sxs-lookup"><span data-stu-id="f9413-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="f9413-111">Składowa klasy bazowej nie musi być zaimplementowana [, aby](../../../visual-basic/language-reference/modifiers/overridable.md) można ją było ponownie zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="f9413-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="f9413-112">Można wykonać ponowną implementację elementu członkowskiego z inną nazwą.</span><span class="sxs-lookup"><span data-stu-id="f9413-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="f9413-113">Słowo kluczowe `Implements` może być używane w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="f9413-113">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="f9413-114">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f9413-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="f9413-115">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f9413-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="f9413-116">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f9413-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="f9413-117">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f9413-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f9413-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9413-118">See also</span></span>

- [<span data-ttu-id="f9413-119">Implements, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f9413-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="f9413-120">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f9413-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="f9413-121">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f9413-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="f9413-122">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f9413-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
