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
ms.openlocfilehash: 0c85564503f3c83e436044cd92ee3014945f1ef3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818387"
---
# <a name="public-visual-basic"></a><span data-ttu-id="2af3b-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2af3b-102">Public (Visual Basic)</span></span>
<span data-ttu-id="2af3b-103">Określa, że co najmniej jeden zadeklarowany element programistyczny nie ma ograniczeń dostępu.</span><span class="sxs-lookup"><span data-stu-id="2af3b-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2af3b-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2af3b-104">Remarks</span></span>  
 <span data-ttu-id="2af3b-105">W przypadku publikowania składnika lub zestaw składników, takich jak biblioteki klas, ma zwykle programistyczny dostępu przez każdy kod, który współdziała z zestawu.</span><span class="sxs-lookup"><span data-stu-id="2af3b-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="2af3b-106">Przyznaje taki dostęp bez ograniczeń dla elementu, można zadeklarować za pomocą `Public`.</span><span class="sxs-lookup"><span data-stu-id="2af3b-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="2af3b-107">Dostęp publiczny jest normalnego poziomu dla elementu programistycznego, gdy jest konieczne ograniczanie dostępu do niego.</span><span class="sxs-lookup"><span data-stu-id="2af3b-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="2af3b-108">Należy pamiętać, poziom dostępu elementu jest zadeklarowany w obrębie interfejsu, modułu, klasy lub struktury wartość domyślna to `Public` nie zadeklarowana w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="2af3b-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2af3b-109">reguły</span><span class="sxs-lookup"><span data-stu-id="2af3b-109">Rules</span></span>  
  
-   <span data-ttu-id="2af3b-110">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="2af3b-110">**Declaration Context.**</span></span> <span data-ttu-id="2af3b-111">Możesz użyć `Public` tylko na poziomie modułu, interfejsu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2af3b-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="2af3b-112">Oznacza to, że kontekst deklaracji `Public` elementu musi być w pliku źródłowym, przestrzeń nazw, interfejsu, modułu, klasy lub struktury, a nie może być procedurą.</span><span class="sxs-lookup"><span data-stu-id="2af3b-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2af3b-113">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="2af3b-113">Behavior</span></span>  
  
-   <span data-ttu-id="2af3b-114">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="2af3b-114">**Access Level.**</span></span> <span data-ttu-id="2af3b-115">Cały kod, który mają dostęp do modułu, klasy lub struktury mogą uzyskiwać dostęp do jego `Public` elementów.</span><span class="sxs-lookup"><span data-stu-id="2af3b-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
-   <span data-ttu-id="2af3b-116">**Dostęp do domyślnej.**</span><span class="sxs-lookup"><span data-stu-id="2af3b-116">**Default Access.**</span></span> <span data-ttu-id="2af3b-117">Zmiennych lokalnych wewnątrz domyślną procedurę do publicznego dostępu, a nie można użyć dowolnego modyfikatory dostępu na nich.</span><span class="sxs-lookup"><span data-stu-id="2af3b-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
-   <span data-ttu-id="2af3b-118">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="2af3b-118">**Access Modifiers.**</span></span> <span data-ttu-id="2af3b-119">Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorach dostępu*.</span><span class="sxs-lookup"><span data-stu-id="2af3b-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="2af3b-120">Dla porównania modyfikatory dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2af3b-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="2af3b-121">`Public` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="2af3b-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="2af3b-122">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2af3b-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="2af3b-123">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2af3b-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="2af3b-124">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2af3b-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="2af3b-125">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2af3b-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="2af3b-126">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2af3b-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="2af3b-127">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2af3b-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="2af3b-128">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2af3b-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="2af3b-129">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2af3b-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="2af3b-130">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="2af3b-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="2af3b-131">Instrukcja Module</span><span class="sxs-lookup"><span data-stu-id="2af3b-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="2af3b-132">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2af3b-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="2af3b-133">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="2af3b-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="2af3b-134">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2af3b-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="2af3b-135">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2af3b-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2af3b-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2af3b-136">See also</span></span>

- [<span data-ttu-id="2af3b-137">Protected</span><span class="sxs-lookup"><span data-stu-id="2af3b-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="2af3b-138">Friend</span><span class="sxs-lookup"><span data-stu-id="2af3b-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="2af3b-139">Private</span><span class="sxs-lookup"><span data-stu-id="2af3b-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="2af3b-140">Private Protected</span><span class="sxs-lookup"><span data-stu-id="2af3b-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="2af3b-141">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="2af3b-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="2af3b-142">Poziomy dostępu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2af3b-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="2af3b-143">Procedury</span><span class="sxs-lookup"><span data-stu-id="2af3b-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="2af3b-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="2af3b-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="2af3b-145">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="2af3b-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
