---
title: Public
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 35332e50227cdef6386362df17c10b5b2cdaa689
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415352"
---
# <a name="public-visual-basic"></a><span data-ttu-id="cbd0f-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbd0f-102">Public (Visual Basic)</span></span>
<span data-ttu-id="cbd0f-103">Określa, że co najmniej jeden zadeklarowany element programistyczny nie ma ograniczeń dostępu.</span><span class="sxs-lookup"><span data-stu-id="cbd0f-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbd0f-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbd0f-104">Remarks</span></span>  
 <span data-ttu-id="cbd0f-105">Jeśli publikujesz składnik lub zestaw składników, takich jak Biblioteka klas, zazwyczaj chcesz, aby elementy programistyczne były dostępne dla dowolnego kodu, który współdziała z Twoim zestawem.</span><span class="sxs-lookup"><span data-stu-id="cbd0f-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="cbd0f-106">Aby przyznać takie nieograniczone dostęp do elementu, można zadeklarować go za pomocą `Public` .</span><span class="sxs-lookup"><span data-stu-id="cbd0f-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="cbd0f-107">Dostęp publiczny jest normalnym poziomem dla elementu programistycznego, gdy nie trzeba ograniczać dostępu do niego.</span><span class="sxs-lookup"><span data-stu-id="cbd0f-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="cbd0f-108">Należy zauważyć, że poziom dostępu elementu zadeklarowanego w interfejsie, module, klasie lub strukturze domyślnie nie jest `Public` deklarowany w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="cbd0f-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="cbd0f-109">Reguły</span><span class="sxs-lookup"><span data-stu-id="cbd0f-109">Rules</span></span>  
  
- <span data-ttu-id="cbd0f-110">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="cbd0f-110">**Declaration Context.**</span></span> <span data-ttu-id="cbd0f-111">Można używać `Public` tylko na poziomie modułu, interfejsu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cbd0f-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="cbd0f-112">Oznacza to, że kontekst deklaracji dla `Public` elementu musi być plikiem źródłowym, przestrzenią nazw, interfejsem, modułem, klasą lub strukturą i nie może być procedurą.</span><span class="sxs-lookup"><span data-stu-id="cbd0f-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="cbd0f-113">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="cbd0f-113">Behavior</span></span>  
  
- <span data-ttu-id="cbd0f-114">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="cbd0f-114">**Access Level.**</span></span> <span data-ttu-id="cbd0f-115">Cały kod, który może uzyskać dostęp do modułu, klasy lub struktury, może uzyskać dostęp do jego `Public` elementów.</span><span class="sxs-lookup"><span data-stu-id="cbd0f-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="cbd0f-116">**Dostęp domyślny.**</span><span class="sxs-lookup"><span data-stu-id="cbd0f-116">**Default Access.**</span></span> <span data-ttu-id="cbd0f-117">Zmienne lokalne wewnątrz procedury domyślnie mają dostęp publiczny i nie można używać żadnych modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="cbd0f-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="cbd0f-118">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="cbd0f-118">**Access Modifiers.**</span></span> <span data-ttu-id="cbd0f-119">Słowa kluczowe określające poziom dostępu są nazywane *modyfikatorami dostępu*.</span><span class="sxs-lookup"><span data-stu-id="cbd0f-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="cbd0f-120">Aby porównać Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cbd0f-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="cbd0f-121">`Public`Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="cbd0f-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="cbd0f-122">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-122">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="cbd0f-123">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-123">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="cbd0f-124">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-124">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="cbd0f-125">Delegate — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-125">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="cbd0f-126">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-126">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="cbd0f-127">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-127">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="cbd0f-128">Event — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-128">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="cbd0f-129">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-129">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="cbd0f-130">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-130">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="cbd0f-131">Module — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-131">Module Statement</span></span>](../statements/module-statement.md)  
  
 [<span data-ttu-id="cbd0f-132">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-132">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 [<span data-ttu-id="cbd0f-133">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-133">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="cbd0f-134">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-134">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="cbd0f-135">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbd0f-135">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cbd0f-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbd0f-136">See also</span></span>

- [<span data-ttu-id="cbd0f-137">Chronione</span><span class="sxs-lookup"><span data-stu-id="cbd0f-137">Protected</span></span>](protected.md)
- [<span data-ttu-id="cbd0f-138">Osoby</span><span class="sxs-lookup"><span data-stu-id="cbd0f-138">Friend</span></span>](friend.md)
- [<span data-ttu-id="cbd0f-139">Użytek</span><span class="sxs-lookup"><span data-stu-id="cbd0f-139">Private</span></span>](private.md)
- [<span data-ttu-id="cbd0f-140">Prywatne chronione</span><span class="sxs-lookup"><span data-stu-id="cbd0f-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="cbd0f-141">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="cbd0f-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="cbd0f-142">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cbd0f-142">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="cbd0f-143">Procedury</span><span class="sxs-lookup"><span data-stu-id="cbd0f-143">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="cbd0f-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="cbd0f-144">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="cbd0f-145">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="cbd0f-145">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
