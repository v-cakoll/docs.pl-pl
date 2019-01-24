---
title: Implements — Klauzula (Visual Basic)
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
ms.openlocfilehash: cb0ea5ce52effad4df541e6a9196b1faf279262e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522517"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="4022c-102">Implements — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4022c-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="4022c-103">Wskazuje, że składowa klasy lub struktury dostarcza implementację dla składowej zdefiniowanej w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="4022c-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4022c-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4022c-104">Remarks</span></span>  
<span data-ttu-id="4022c-105">`Implements` — Słowo kluczowe nie jest taka sama jak [Implements — instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4022c-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="4022c-106">Możesz użyć `Implements` instrukcję, aby określić, że klasa lub struktura implementuje jeden lub więcej interfejsów, a następnie dla każdego elementu członkowskiego przy użyciu `Implements` — słowo kluczowe, aby określić, które interfejsu i członka, który implementuje.</span><span class="sxs-lookup"><span data-stu-id="4022c-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="4022c-107">Jeśli klasa lub struktura implementuje interfejs, musi on zawierać `Implements` instrukcji natychmiast po [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md) lub [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md), i musi on implementować wszystkie elementy członkowskie zdefiniowane przez interfejs.</span><span class="sxs-lookup"><span data-stu-id="4022c-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="4022c-108">Reimplementation</span><span class="sxs-lookup"><span data-stu-id="4022c-108">Reimplementation</span></span>  
<span data-ttu-id="4022c-109">W klasie pochodnej można ponownie składowej interfejsu, która klasa bazowa została już zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="4022c-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="4022c-110">To różni się od przesłanianie składowej klasy bazowej pod następującymi względami:</span><span class="sxs-lookup"><span data-stu-id="4022c-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="4022c-111">Składowej klasy bazowej nie musi być [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) do być reimplemented.</span><span class="sxs-lookup"><span data-stu-id="4022c-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="4022c-112">Można ponownie element członkowski o innej nazwie.</span><span class="sxs-lookup"><span data-stu-id="4022c-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="4022c-113">`Implements` — Słowo kluczowe może służyć w następujących okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="4022c-113">The `Implements` keyword can be used in the following contexts:</span></span>
- [<span data-ttu-id="4022c-114">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4022c-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="4022c-115">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4022c-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="4022c-116">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="4022c-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="4022c-117">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4022c-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="4022c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4022c-118">See also</span></span>
- [<span data-ttu-id="4022c-119">Implements, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4022c-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="4022c-120">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="4022c-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="4022c-121">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4022c-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="4022c-122">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4022c-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
