---
title: Protected (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 5f279ed0a33840bb1f2321c17a1ffba412837c07
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="protected-visual-basic"></a><span data-ttu-id="abea1-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abea1-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="abea1-103">Modyfikator dostępu elementu członkowskiego, który określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie swojej klasy lub z klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="abea1-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abea1-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="abea1-104">Remarks</span></span>  
 <span data-ttu-id="abea1-105">Czasami elementu programistycznego zadeklarowana w klasie zawierają dane poufne lub ograniczone kod, a użytkownik chce ograniczyć dostęp do elementu.</span><span class="sxs-lookup"><span data-stu-id="abea1-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="abea1-106">Jednak jeśli oczekujesz hierarchii klas pochodnych klasy jest dziedziczona, może być konieczne dla tych klas pochodnych dostępu do danych lub kodu.</span><span class="sxs-lookup"><span data-stu-id="abea1-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="abea1-107">W takim przypadku ma element ma być dostępny zarówno z klasy podstawowej i wszystkich klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="abea1-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="abea1-108">Aby ograniczyć dostęp do elementu w ten sposób, mogą zadeklarować za pomocą `Protected`.</span><span class="sxs-lookup"><span data-stu-id="abea1-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  

> [!NOTE]
> <span data-ttu-id="abea1-109">`Protected` Modyfikator dostępu można łączyć z dwóch innych modyfikatorów:</span><span class="sxs-lookup"><span data-stu-id="abea1-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
> - <span data-ttu-id="abea1-110">[Protected Friend](protected-friend.md) modyfikator sprawia, że element członkowski klasy jest dostępny w obrębie klasy, z klasy pochodnej i z tego samego zestawu, w którym klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="abea1-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> 
> - <span data-ttu-id="abea1-111">[Prywatne chronione](private-protected.md) modyfikator sprawia, że element członkowski klasy dostępne przez typy pochodne, ale tylko w obrębie zawierający go zestaw.</span><span class="sxs-lookup"><span data-stu-id="abea1-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>
  
## <a name="rules"></a><span data-ttu-id="abea1-112">Reguły</span><span class="sxs-lookup"><span data-stu-id="abea1-112">Rules</span></span>  
  
-   <span data-ttu-id="abea1-113">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="abea1-113">**Declaration Context.**</span></span> <span data-ttu-id="abea1-114">Można użyć `Protected` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="abea1-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="abea1-115">Oznacza to, że w kontekście deklaracji `Protected` elementu musi być klasą i nie może być plik źródłowy, przestrzeni nazw, interfejsu, modułu, struktury lub procedury.</span><span class="sxs-lookup"><span data-stu-id="abea1-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  

## <a name="behavior"></a><span data-ttu-id="abea1-116">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="abea1-116">Behavior</span></span>  
  
-   <span data-ttu-id="abea1-117">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="abea1-117">**Access Level.**</span></span> <span data-ttu-id="abea1-118">Cały kod w klasie mogą uzyskiwać dostęp do swoich elementów.</span><span class="sxs-lookup"><span data-stu-id="abea1-118">All code in a class can access its elements.</span></span> <span data-ttu-id="abea1-119">Kod w dowolnej klasy, która pochodzi z klasy podstawowej można uzyskać dostęp do wszystkich `Protected` elementy klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="abea1-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="abea1-120">Jest to istotne dla wszystkich generacji pochodnym.</span><span class="sxs-lookup"><span data-stu-id="abea1-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="abea1-121">Oznacza to, że klasa może uzyskać dostęp `Protected` elementy klasy podstawowej klasy podstawowej i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="abea1-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="abea1-122">Chronionego dostępu nie jest nadzbiorem lub podzbiór przyjaznego dostępu.</span><span class="sxs-lookup"><span data-stu-id="abea1-122">Protected access is not a superset or subset of friend access.</span></span>  
  
-   <span data-ttu-id="abea1-123">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="abea1-123">**Access Modifiers.**</span></span> <span data-ttu-id="abea1-124">Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="abea1-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="abea1-125">Porównanie modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="abea1-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="abea1-126">`Protected` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="abea1-126">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="abea1-127">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="abea1-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="abea1-128">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="abea1-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="abea1-129">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="abea1-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="abea1-130">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="abea1-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="abea1-131">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="abea1-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="abea1-132">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="abea1-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="abea1-133">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="abea1-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="abea1-134">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="abea1-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="abea1-135">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="abea1-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="abea1-136">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="abea1-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="abea1-137">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="abea1-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="abea1-138">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="abea1-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="abea1-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abea1-139">See Also</span></span>  
 [<span data-ttu-id="abea1-140">Public</span><span class="sxs-lookup"><span data-stu-id="abea1-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="abea1-141">Friend</span><span class="sxs-lookup"><span data-stu-id="abea1-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="abea1-142">Private</span><span class="sxs-lookup"><span data-stu-id="abea1-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 <span data-ttu-id="abea1-143">[Prywatne chronione](private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="abea1-143">[Private Protected](private-protected.md) </span></span>  
 <span data-ttu-id="abea1-144">[Friend chronionych](protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="abea1-144">[Protected Friend](protected-friend.md) </span></span>  
 [<span data-ttu-id="abea1-145">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="abea1-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="abea1-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="abea1-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="abea1-147">Struktury</span><span class="sxs-lookup"><span data-stu-id="abea1-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="abea1-148">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="abea1-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
