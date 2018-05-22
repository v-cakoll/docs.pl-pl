---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 40b64b8d2b6306d458b7a9cc657c5b7dc4270eb2
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="private-visual-basic"></a><span data-ttu-id="7fa1d-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fa1d-102">Private (Visual Basic)</span></span>
<span data-ttu-id="7fa1d-103">Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie ich kontekście deklaracji, łącznie z wewnątrz żadnych typów zawartych w niej.</span><span class="sxs-lookup"><span data-stu-id="7fa1d-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fa1d-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7fa1d-104">Remarks</span></span>  
 <span data-ttu-id="7fa1d-105">Jeśli elementu programistycznego reprezentuje własnościowych funkcji lub zawiera dane poufne, mają zwykle jako ściśle ograniczyć do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="7fa1d-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="7fa1d-106">Ograniczenie maksymalnej można osiągnąć, zezwalając tylko modułu, klasy lub struktury, definiujący go do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="7fa1d-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="7fa1d-107">Aby ograniczyć dostęp do elementu w ten sposób, mogą zadeklarować za pomocą `Private`.</span><span class="sxs-lookup"><span data-stu-id="7fa1d-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="7fa1d-108">Można również użyć [prywatne chronione](private-protected.md) modyfikator dostępu, co sprawia, że element członkowski jest dostępny z tej klasy i z klas pochodnych znajduje się w jego zawierający zestaw.</span><span class="sxs-lookup"><span data-stu-id="7fa1d-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="7fa1d-109">Reguły</span><span class="sxs-lookup"><span data-stu-id="7fa1d-109">Rules</span></span>  

-   <span data-ttu-id="7fa1d-110">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="7fa1d-110">**Declaration Context.**</span></span> <span data-ttu-id="7fa1d-111">Można użyć `Private` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="7fa1d-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="7fa1d-112">Oznacza to, że w kontekście deklaracji `Private` elementu musi być modułu, klasy lub struktury i nie może być plik źródłowy, przestrzeń nazw, interfejsem lub procedury.</span><span class="sxs-lookup"><span data-stu-id="7fa1d-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="7fa1d-113">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="7fa1d-113">Behavior</span></span>  
  
-   <span data-ttu-id="7fa1d-114">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="7fa1d-114">**Access Level.**</span></span> <span data-ttu-id="7fa1d-115">Cały kod w kontekście deklaracji mogą uzyskiwać dostęp do jego `Private` elementów.</span><span class="sxs-lookup"><span data-stu-id="7fa1d-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="7fa1d-116">W tym kodu w ramach ograniczonego typu, na przykład klasa zagnieżdżona lub wyrażenie przypisania w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="7fa1d-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="7fa1d-117">Brak kodu poza kontekstem deklaracji mogą uzyskiwać dostęp do jego `Private` elementów.</span><span class="sxs-lookup"><span data-stu-id="7fa1d-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="7fa1d-118">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="7fa1d-118">**Access Modifiers.**</span></span> <span data-ttu-id="7fa1d-119">Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="7fa1d-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="7fa1d-120">Porównanie modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7fa1d-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="7fa1d-121">`Private` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="7fa1d-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="7fa1d-122">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7fa1d-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="7fa1d-123">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7fa1d-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="7fa1d-124">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7fa1d-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="7fa1d-125">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7fa1d-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="7fa1d-126">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7fa1d-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="7fa1d-127">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7fa1d-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="7fa1d-128">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7fa1d-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="7fa1d-129">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7fa1d-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="7fa1d-130">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7fa1d-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="7fa1d-131">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7fa1d-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="7fa1d-132">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7fa1d-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="7fa1d-133">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7fa1d-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7fa1d-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7fa1d-134">See Also</span></span>  
 [<span data-ttu-id="7fa1d-135">Public</span><span class="sxs-lookup"><span data-stu-id="7fa1d-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="7fa1d-136">Protected</span><span class="sxs-lookup"><span data-stu-id="7fa1d-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="7fa1d-137">Friend</span><span class="sxs-lookup"><span data-stu-id="7fa1d-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 <span data-ttu-id="7fa1d-138">[Prywatne chronione](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="7fa1d-138">[Private Protected](./private-protected.md) </span></span>  
 <span data-ttu-id="7fa1d-139">[Protected Friend](./protected-friend.md)[dostępu poziomy w języku Visual Basic    ](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="7fa1d-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>  
 [<span data-ttu-id="7fa1d-140">Procedury</span><span class="sxs-lookup"><span data-stu-id="7fa1d-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="7fa1d-141">Struktury</span><span class="sxs-lookup"><span data-stu-id="7fa1d-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="7fa1d-142">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="7fa1d-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
