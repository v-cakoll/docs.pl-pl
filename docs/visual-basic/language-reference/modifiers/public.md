---
title: Public (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: a5e9161132ba6d571daa30ce82e1bfb1dd2b064f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="public-visual-basic"></a><span data-ttu-id="dda72-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dda72-102">Public (Visual Basic)</span></span>
<span data-ttu-id="dda72-103">Określa, że co najmniej jeden zadeklarowany element programistyczny nie ma ograniczeń dostępu.</span><span class="sxs-lookup"><span data-stu-id="dda72-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dda72-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dda72-104">Remarks</span></span>  
 <span data-ttu-id="dda72-105">W przypadku publikowania składnika lub zestaw składników, takich jak biblioteki klas, zazwyczaj mają programistyczny dostępu przez dowolny kod, który współdziała z tym zestawem.</span><span class="sxs-lookup"><span data-stu-id="dda72-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="dda72-106">Przyznanie takich nieograniczonego dostępu w elemencie, mogą zadeklarować go przy użyciu `Public`.</span><span class="sxs-lookup"><span data-stu-id="dda72-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="dda72-107">Dostępu publicznego jest normalnego poziomu dla elementu programistycznego, gdy jest konieczne ograniczenie dostępu do niego.</span><span class="sxs-lookup"><span data-stu-id="dda72-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="dda72-108">Należy pamiętać, że poziom dostępu do elementu zadeklarowany w interfejsie, modułu, klasy lub struktury domyślnie `Public` nie zadeklarowana w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="dda72-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="dda72-109">Reguły</span><span class="sxs-lookup"><span data-stu-id="dda72-109">Rules</span></span>  
  
-   <span data-ttu-id="dda72-110">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="dda72-110">**Declaration Context.**</span></span> <span data-ttu-id="dda72-111">Można użyć `Public` tylko na poziomie modułu, interfejsem lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="dda72-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="dda72-112">Oznacza to, że w kontekście deklaracji `Public` elementu musi być pliku źródłowego, przestrzeń nazw, interfejsu, modułu, klasy lub struktury i nie może być procedury.</span><span class="sxs-lookup"><span data-stu-id="dda72-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="dda72-113">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="dda72-113">Behavior</span></span>  
  
-   <span data-ttu-id="dda72-114">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="dda72-114">**Access Level.**</span></span> <span data-ttu-id="dda72-115">Cały kod, który można uzyskać dostępu do modułu, klasy lub struktury mogą uzyskiwać dostęp do jego `Public` elementów.</span><span class="sxs-lookup"><span data-stu-id="dda72-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
-   <span data-ttu-id="dda72-116">**Dostęp do domyślnej.**</span><span class="sxs-lookup"><span data-stu-id="dda72-116">**Default Access.**</span></span> <span data-ttu-id="dda72-117">Zmiennych lokalnych wewnątrz procedury domyślnie dostępu publicznego, a nie można użyć dowolnego modyfikatorów dostępu na nich.</span><span class="sxs-lookup"><span data-stu-id="dda72-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
-   <span data-ttu-id="dda72-118">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="dda72-118">**Access Modifiers.**</span></span> <span data-ttu-id="dda72-119">Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="dda72-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="dda72-120">Porównanie modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="dda72-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="dda72-121">`Public` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="dda72-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="dda72-122">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="dda72-123">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="dda72-124">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="dda72-125">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="dda72-126">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="dda72-127">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="dda72-128">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="dda72-129">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="dda72-130">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="dda72-131">Module, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="dda72-132">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="dda72-133">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="dda72-134">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="dda72-135">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dda72-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="dda72-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dda72-136">See Also</span></span>  
 [<span data-ttu-id="dda72-137">Protected</span><span class="sxs-lookup"><span data-stu-id="dda72-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="dda72-138">Friend</span><span class="sxs-lookup"><span data-stu-id="dda72-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="dda72-139">Private</span><span class="sxs-lookup"><span data-stu-id="dda72-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 <span data-ttu-id="dda72-140">[Prywatne chronione](private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="dda72-140">[Private Protected](private-protected.md) </span></span>  
 <span data-ttu-id="dda72-141">[Friend chronionych](protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="dda72-141">[Protected Friend](protected-friend.md) </span></span>  
 [<span data-ttu-id="dda72-142">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dda72-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="dda72-143">Procedury</span><span class="sxs-lookup"><span data-stu-id="dda72-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="dda72-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="dda72-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="dda72-145">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="dda72-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
