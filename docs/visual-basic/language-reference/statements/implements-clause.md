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
ms.openlocfilehash: dcd20f21a989c327dcfcf27d5638d500b6e4b6da
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929318"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="bc9d9-102">Implements — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc9d9-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="bc9d9-103">Wskazuje, że składowa klasy lub struktury dostarcza implementację dla składowej zdefiniowanej w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc9d9-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc9d9-104">Remarks</span></span>  
<span data-ttu-id="bc9d9-105">Słowo kluczowe nie jest takie samo jak [instrukcja Implements.](../../../visual-basic/language-reference/statements/implements-statement.md) `Implements`</span><span class="sxs-lookup"><span data-stu-id="bc9d9-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="bc9d9-106">Możesz użyć `Implements` instrukcji, aby określić, że Klasa lub struktura implementuje jeden lub więcej interfejsów, a następnie dla każdego elementu członkowskiego `Implements` używa słowa kluczowego, aby określić, który interfejs i który element członkowski implementuje.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="bc9d9-107">Jeśli klasa lub struktura implementuje interfejs, musi zawierać `Implements` instrukcję bezpośrednio po [instrukcji klasy](../../../visual-basic/language-reference/statements/class-statement.md) lub [instrukcji struktury](../../../visual-basic/language-reference/statements/structure-statement.md)i musi zaimplementować wszystkie elementy członkowskie zdefiniowane przez interfejs.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="bc9d9-108">Reimplementacja</span><span class="sxs-lookup"><span data-stu-id="bc9d9-108">Reimplementation</span></span>  
<span data-ttu-id="bc9d9-109">W klasie pochodnej można wykonać ponowną implementację elementu członkowskiego interfejsu, który został już zaimplementowany przez klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="bc9d9-110">Różni się to od przesłaniania składowej klasy bazowej w następujących aspektach:</span><span class="sxs-lookup"><span data-stu-id="bc9d9-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="bc9d9-111">Składowa klasy bazowej nie musi być zaimplementowana [, aby](../../../visual-basic/language-reference/modifiers/overridable.md) można ją było ponownie zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="bc9d9-112">Można wykonać ponowną implementację elementu członkowskiego z inną nazwą.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="bc9d9-113">`Implements` Słowo kluczowe może być używane w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="bc9d9-113">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="bc9d9-114">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bc9d9-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="bc9d9-115">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bc9d9-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="bc9d9-116">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="bc9d9-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="bc9d9-117">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bc9d9-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="bc9d9-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc9d9-118">See also</span></span>

- [<span data-ttu-id="bc9d9-119">Implements, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bc9d9-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="bc9d9-120">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="bc9d9-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="bc9d9-121">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bc9d9-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="bc9d9-122">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bc9d9-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
