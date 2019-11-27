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
ms.openlocfilehash: 35bf1a65e0b8f24a1263adc480719c69b95dff9b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351292"
---
# <a name="public-visual-basic"></a><span data-ttu-id="1b5c5-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b5c5-102">Public (Visual Basic)</span></span>
<span data-ttu-id="1b5c5-103">Określa, że co najmniej jeden zadeklarowany element programistyczny nie ma ograniczeń dostępu.</span><span class="sxs-lookup"><span data-stu-id="1b5c5-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b5c5-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b5c5-104">Remarks</span></span>  
 <span data-ttu-id="1b5c5-105">Jeśli publikujesz składnik lub zestaw składników, takich jak Biblioteka klas, zazwyczaj chcesz, aby elementy programistyczne były dostępne dla dowolnego kodu, który współdziała z Twoim zestawem.</span><span class="sxs-lookup"><span data-stu-id="1b5c5-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="1b5c5-106">Aby przyznać takie nieograniczone dostęp do elementu, można zadeklarować go za pomocą `Public`.</span><span class="sxs-lookup"><span data-stu-id="1b5c5-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="1b5c5-107">Dostęp publiczny jest normalnym poziomem dla elementu programistycznego, gdy nie trzeba ograniczać dostępu do niego.</span><span class="sxs-lookup"><span data-stu-id="1b5c5-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="1b5c5-108">Należy zauważyć, że poziom dostępu elementu zadeklarowanego w interfejsie, module, klasie lub strukturze domyślnie `Public`, jeśli nie zostanie zadeklarowany w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="1b5c5-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="1b5c5-109">Reguły</span><span class="sxs-lookup"><span data-stu-id="1b5c5-109">Rules</span></span>  
  
- <span data-ttu-id="1b5c5-110">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="1b5c5-110">**Declaration Context.**</span></span> <span data-ttu-id="1b5c5-111">`Public` można używać tylko na poziomie modułu, interfejsu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1b5c5-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="1b5c5-112">Oznacza to, że kontekst deklaracji dla elementu `Public` musi być plikiem źródłowym, przestrzenią nazw, interfejsem, modułem, klasą lub strukturą i nie może być procedurą.</span><span class="sxs-lookup"><span data-stu-id="1b5c5-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="1b5c5-113">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="1b5c5-113">Behavior</span></span>  
  
- <span data-ttu-id="1b5c5-114">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="1b5c5-114">**Access Level.**</span></span> <span data-ttu-id="1b5c5-115">Cały kod, który może uzyskać dostęp do modułu, klasy lub struktury, może uzyskać dostęp do swoich `Public`ych elementów.</span><span class="sxs-lookup"><span data-stu-id="1b5c5-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="1b5c5-116">**Dostęp domyślny.**</span><span class="sxs-lookup"><span data-stu-id="1b5c5-116">**Default Access.**</span></span> <span data-ttu-id="1b5c5-117">Zmienne lokalne wewnątrz procedury domyślnie mają dostęp publiczny i nie można używać żadnych modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="1b5c5-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="1b5c5-118">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="1b5c5-118">**Access Modifiers.**</span></span> <span data-ttu-id="1b5c5-119">Słowa kluczowe określające poziom dostępu są nazywane *modyfikatorami dostępu*.</span><span class="sxs-lookup"><span data-stu-id="1b5c5-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="1b5c5-120">Aby porównać Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1b5c5-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="1b5c5-121">Modyfikator `Public` może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="1b5c5-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="1b5c5-122">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="1b5c5-123">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="1b5c5-124">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="1b5c5-125">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="1b5c5-126">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="1b5c5-127">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="1b5c5-128">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="1b5c5-129">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="1b5c5-130">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="1b5c5-131">Module, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="1b5c5-132">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="1b5c5-133">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="1b5c5-134">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="1b5c5-135">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b5c5-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="1b5c5-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b5c5-136">See also</span></span>

- [<span data-ttu-id="1b5c5-137">Protected</span><span class="sxs-lookup"><span data-stu-id="1b5c5-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="1b5c5-138">Friend</span><span class="sxs-lookup"><span data-stu-id="1b5c5-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="1b5c5-139">Private</span><span class="sxs-lookup"><span data-stu-id="1b5c5-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="1b5c5-140">Private Protected</span><span class="sxs-lookup"><span data-stu-id="1b5c5-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="1b5c5-141">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="1b5c5-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="1b5c5-142">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1b5c5-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="1b5c5-143">Procedury</span><span class="sxs-lookup"><span data-stu-id="1b5c5-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="1b5c5-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="1b5c5-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="1b5c5-145">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="1b5c5-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
