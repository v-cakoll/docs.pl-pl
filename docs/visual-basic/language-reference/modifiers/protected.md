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
ms.openlocfilehash: 86758c68f0f3bfe214a695f656d3924eadd27e31
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642688"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="5959d-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5959d-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="5959d-103">Modyfikator dostępu elementu członkowskiego, który określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie swojej klasy lub z klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="5959d-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5959d-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5959d-104">Remarks</span></span>  
 <span data-ttu-id="5959d-105">Czasami elementu programistycznego, zadeklarowana w klasie zawiera dane poufne lub ograniczony kod, a użytkownik chce ograniczyć dostęp do elementu.</span><span class="sxs-lookup"><span data-stu-id="5959d-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="5959d-106">Jednakże jeśli klasa jest dziedziczone, które hierarchii klas pochodnych, może być konieczne dla tych klas pochodnych, uzyskać dostęp do danych lub kod.</span><span class="sxs-lookup"><span data-stu-id="5959d-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="5959d-107">W takim przypadku należy elementu, który ma być dostępne zarówno z klasy bazowej i wszystkie klasy pochodne.</span><span class="sxs-lookup"><span data-stu-id="5959d-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="5959d-108">Aby ograniczyć dostęp do elementu w ten sposób, można zadeklarować za pomocą `Protected`.</span><span class="sxs-lookup"><span data-stu-id="5959d-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  

> [!NOTE]
> <span data-ttu-id="5959d-109">`Protected` Modyfikator dostępu można łączyć z innymi modyfikatorów:</span><span class="sxs-lookup"><span data-stu-id="5959d-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
> - <span data-ttu-id="5959d-110">[Protected Friend](protected-friend.md) modyfikator sprawia, że element członkowski klasy jest dostępny w obrębie tej klasy z klas pochodnych i z tego samego zestawu, w którym klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="5959d-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> 
> - <span data-ttu-id="5959d-111">[Private Protected](private-protected.md) modyfikator sprawia, że element członkowski klasy dostępne przez typy pochodne, ale tylko w ramach własnego zestawu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="5959d-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>
  
## <a name="rules"></a><span data-ttu-id="5959d-112">reguły</span><span class="sxs-lookup"><span data-stu-id="5959d-112">Rules</span></span>  
  
- <span data-ttu-id="5959d-113">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="5959d-113">**Declaration Context.**</span></span> <span data-ttu-id="5959d-114">Możesz użyć `Protected` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="5959d-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="5959d-115">Oznacza to, że kontekst deklaracji `Protected` element musi być klasą i nie może być plik źródłowy, przestrzeń nazw, interfejsu, moduł, struktura lub procedury.</span><span class="sxs-lookup"><span data-stu-id="5959d-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  

## <a name="behavior"></a><span data-ttu-id="5959d-116">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="5959d-116">Behavior</span></span>  
  
- <span data-ttu-id="5959d-117">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="5959d-117">**Access Level.**</span></span> <span data-ttu-id="5959d-118">Cały kod w klasie mogą uzyskać dostęp do jego elementów.</span><span class="sxs-lookup"><span data-stu-id="5959d-118">All code in a class can access its elements.</span></span> <span data-ttu-id="5959d-119">Kod w dowolną klasę pochodzącą z klasy bazowej może uzyskać dostęp do wszystkich `Protected` elementów klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="5959d-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="5959d-120">Ta zasada obowiązuje dla wszystkich pokoleń pochodnym.</span><span class="sxs-lookup"><span data-stu-id="5959d-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="5959d-121">Oznacza to, że dostęp do klasy `Protected` elementy klasę bazową klasy bazowej i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="5959d-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="5959d-122">Chronionego dostępu nie jest nadzbiorem lub podzbiór dostęp zaprzyjaźniony.</span><span class="sxs-lookup"><span data-stu-id="5959d-122">Protected access is not a superset or subset of friend access.</span></span>  
  
- <span data-ttu-id="5959d-123">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="5959d-123">**Access Modifiers.**</span></span> <span data-ttu-id="5959d-124">Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorach dostępu*.</span><span class="sxs-lookup"><span data-stu-id="5959d-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="5959d-125">Dla porównania modyfikatory dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5959d-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="5959d-126">`Protected` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="5959d-126">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="5959d-127">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5959d-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="5959d-128">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5959d-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="5959d-129">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5959d-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="5959d-130">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5959d-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="5959d-131">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5959d-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="5959d-132">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5959d-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="5959d-133">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5959d-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="5959d-134">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5959d-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="5959d-135">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="5959d-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="5959d-136">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="5959d-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="5959d-137">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5959d-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="5959d-138">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5959d-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5959d-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5959d-139">See also</span></span>

- [<span data-ttu-id="5959d-140">Public</span><span class="sxs-lookup"><span data-stu-id="5959d-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="5959d-141">Friend</span><span class="sxs-lookup"><span data-stu-id="5959d-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="5959d-142">Private</span><span class="sxs-lookup"><span data-stu-id="5959d-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="5959d-143">Private Protected</span><span class="sxs-lookup"><span data-stu-id="5959d-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="5959d-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="5959d-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="5959d-145">Poziomy dostępu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5959d-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="5959d-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="5959d-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="5959d-147">Struktury</span><span class="sxs-lookup"><span data-stu-id="5959d-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="5959d-148">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="5959d-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
