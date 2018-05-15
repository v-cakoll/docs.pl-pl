---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: d7935cf691d961591ff5e3d2a290afb88de9165a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="private-visual-basic"></a><span data-ttu-id="cd882-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd882-102">Private (Visual Basic)</span></span>
<span data-ttu-id="cd882-103">Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie ich kontekście deklaracji, łącznie z wewnątrz żadnych typów zawartych w niej.</span><span class="sxs-lookup"><span data-stu-id="cd882-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd882-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd882-104">Remarks</span></span>  
 <span data-ttu-id="cd882-105">Jeśli elementu programistycznego reprezentuje własnościowych funkcji lub zawiera dane poufne, mają zwykle jako ściśle ograniczyć do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="cd882-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="cd882-106">Ograniczenie maksymalnej można osiągnąć, zezwalając tylko modułu, klasy lub struktury, definiujący go do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="cd882-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="cd882-107">Aby ograniczyć dostęp do elementu w ten sposób, mogą zadeklarować za pomocą `Private`.</span><span class="sxs-lookup"><span data-stu-id="cd882-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="cd882-108">Reguły</span><span class="sxs-lookup"><span data-stu-id="cd882-108">Rules</span></span>  
  
-   <span data-ttu-id="cd882-109">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="cd882-109">**Declaration Context.**</span></span> <span data-ttu-id="cd882-110">Można użyć `Private` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="cd882-110">You can use `Private` only at module level.</span></span> <span data-ttu-id="cd882-111">Oznacza to, że w kontekście deklaracji `Private` elementu musi być modułu, klasy lub struktury i nie może być plik źródłowy, przestrzeń nazw, interfejsem lub procedury.</span><span class="sxs-lookup"><span data-stu-id="cd882-111">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="cd882-112">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="cd882-112">Behavior</span></span>  
  
-   <span data-ttu-id="cd882-113">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="cd882-113">**Access Level.**</span></span> <span data-ttu-id="cd882-114">Cały kod w kontekście deklaracji mogą uzyskiwać dostęp do jego `Private` elementów.</span><span class="sxs-lookup"><span data-stu-id="cd882-114">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="cd882-115">W tym kodu w ramach ograniczonego typu, na przykład klasa zagnieżdżona lub wyrażenie przypisania w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="cd882-115">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="cd882-116">Brak kodu poza kontekstem deklaracji mogą uzyskiwać dostęp do jego `Private` elementów.</span><span class="sxs-lookup"><span data-stu-id="cd882-116">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="cd882-117">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="cd882-117">**Access Modifiers.**</span></span> <span data-ttu-id="cd882-118">Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="cd882-118">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="cd882-119">Porównanie modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cd882-119">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="cd882-120">`Private` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="cd882-120">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="cd882-121">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd882-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="cd882-122">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd882-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="cd882-123">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd882-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="cd882-124">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd882-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="cd882-125">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd882-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="cd882-126">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd882-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="cd882-127">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd882-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="cd882-128">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd882-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="cd882-129">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd882-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="cd882-130">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd882-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="cd882-131">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd882-131">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="cd882-132">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cd882-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cd882-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd882-133">See Also</span></span>  
 [<span data-ttu-id="cd882-134">Public</span><span class="sxs-lookup"><span data-stu-id="cd882-134">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="cd882-135">Protected</span><span class="sxs-lookup"><span data-stu-id="cd882-135">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="cd882-136">Friend</span><span class="sxs-lookup"><span data-stu-id="cd882-136">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="cd882-137">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cd882-137">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="cd882-138">Procedury</span><span class="sxs-lookup"><span data-stu-id="cd882-138">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="cd882-139">Struktury</span><span class="sxs-lookup"><span data-stu-id="cd882-139">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="cd882-140">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="cd882-140">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
