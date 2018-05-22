---
title: Chronione Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: b72cbee0394043620e792d1c014bfe55121e175e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2018
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="41c60-102">Chronione Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41c60-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="41c60-103">`Protected Friend` Kombinacja słów kluczowych jest modyfikator dostępu elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="41c60-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="41c60-104">Wiąże się zarówno [Friend](friend.md) dostępu i [chronione](protected.md) dostępu na zadeklarowane elementy, dzięki czemu są one dostępne z dowolnej lokalizacji w tym samym zestawie, swojej klasy oraz klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="41c60-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="41c60-105">Można określić `Protected Friend` tylko w elementach członkowskich klas; nie można zastosować `Protected Friend` do elementów członkowskich struktury ponieważ struktur nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="41c60-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="41c60-106">W programie Visual Studio, wybierając pomocy F1 w `protected friend` zawiera informacje pomocne w obu [chronione](protected.md) lub [friend](friend.md).</span><span class="sxs-lookup"><span data-stu-id="41c60-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="41c60-107">IDE wybiera jeden token pod kursorem zamiast wyraz złożony.</span><span class="sxs-lookup"><span data-stu-id="41c60-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="41c60-108">Reguły</span><span class="sxs-lookup"><span data-stu-id="41c60-108">Rules</span></span>

- <span data-ttu-id="41c60-109">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="41c60-109">**Declaration Context.**</span></span> <span data-ttu-id="41c60-110">Można użyć `Protected Friend` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="41c60-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="41c60-111">Oznacza to, że w kontekście deklaracji `Protected` elementu musi być klasą i nie może być plik źródłowy, przestrzeni nazw, interfejsu, modułu, struktury lub procedury.</span><span class="sxs-lookup"><span data-stu-id="41c60-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span> 


## <a name="see-also"></a><span data-ttu-id="41c60-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41c60-112">See Also</span></span>

[<span data-ttu-id="41c60-113">Public</span><span class="sxs-lookup"><span data-stu-id="41c60-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
[<span data-ttu-id="41c60-114">Protected</span><span class="sxs-lookup"><span data-stu-id="41c60-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
<span data-ttu-id="41c60-115">[Friend](friend.md) </span><span class="sxs-lookup"><span data-stu-id="41c60-115">[Friend](friend.md) </span></span>  
[<span data-ttu-id="41c60-116">Private</span><span class="sxs-lookup"><span data-stu-id="41c60-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
<span data-ttu-id="41c60-117">[Prywatne chronione](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="41c60-117">[Private Protected](./private-protected.md) </span></span>  
[<span data-ttu-id="41c60-118">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="41c60-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[<span data-ttu-id="41c60-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="41c60-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[<span data-ttu-id="41c60-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="41c60-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[<span data-ttu-id="41c60-121">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="41c60-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
