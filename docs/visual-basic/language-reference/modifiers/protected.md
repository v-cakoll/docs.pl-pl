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
ms.openlocfilehash: a80e504cc8e88dfc8968f70fee2c17991b28aff5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929454"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="753a5-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="753a5-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="753a5-103">Modyfikator dostępu składowej, który określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie swojej klasy lub z klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="753a5-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="753a5-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="753a5-104">Remarks</span></span>  
 <span data-ttu-id="753a5-105">Czasami element programowania zadeklarowany w klasie zawiera dane poufne lub ograniczony kod i chcesz ograniczyć dostęp do elementu.</span><span class="sxs-lookup"><span data-stu-id="753a5-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="753a5-106">Jeśli jednak Klasa jest dziedziczona i oczekiwana jest hierarchia klas pochodnych, może być konieczne, aby te klasy pochodne miały dostęp do danych lub kodu.</span><span class="sxs-lookup"><span data-stu-id="753a5-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="753a5-107">W takim przypadku element ma być dostępny zarówno z klasy podstawowej, jak i ze wszystkich klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="753a5-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="753a5-108">Aby ograniczyć dostęp do elementu w ten sposób, można go zadeklarować za pomocą `Protected`.</span><span class="sxs-lookup"><span data-stu-id="753a5-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  

> [!NOTE]
> <span data-ttu-id="753a5-109">Modyfikator `Protected` dostępu można łączyć z dwoma innymi modyfikatorami:</span><span class="sxs-lookup"><span data-stu-id="753a5-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
>
> - <span data-ttu-id="753a5-110">Modyfikator [Protected Friend](protected-friend.md) sprawia, że element członkowski klasy jest dostępny z tej klasy, z klas pochodnych i z tego samego zestawu, w którym jest zdefiniowana Klasa.</span><span class="sxs-lookup"><span data-stu-id="753a5-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> 
> - <span data-ttu-id="753a5-111">Modyfikator [Private Protected](private-protected.md) umożliwia członkom klasy dostęp do typów pochodnych, ale tylko w obrębie zawierającego go zestawu.</span><span class="sxs-lookup"><span data-stu-id="753a5-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>
  
## <a name="rules"></a><span data-ttu-id="753a5-112">Przepisy</span><span class="sxs-lookup"><span data-stu-id="753a5-112">Rules</span></span>  
  
- <span data-ttu-id="753a5-113">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="753a5-113">**Declaration Context.**</span></span> <span data-ttu-id="753a5-114">Można używać `Protected` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="753a5-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="753a5-115">Oznacza to, że kontekst deklaracji dla `Protected` elementu musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, modułem, strukturą ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="753a5-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  

## <a name="behavior"></a><span data-ttu-id="753a5-116">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="753a5-116">Behavior</span></span>  
  
- <span data-ttu-id="753a5-117">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="753a5-117">**Access Level.**</span></span> <span data-ttu-id="753a5-118">Cały kod w klasie ma dostęp do jego elementów.</span><span class="sxs-lookup"><span data-stu-id="753a5-118">All code in a class can access its elements.</span></span> <span data-ttu-id="753a5-119">Kod w dowolnej klasie, która dziedziczy z klasy bazowej, może uzyskać dostęp `Protected` do wszystkich elementów klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="753a5-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="753a5-120">Jest to prawdziwe dla wszystkich generacji wyprowadzania.</span><span class="sxs-lookup"><span data-stu-id="753a5-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="753a5-121">Oznacza to, że Klasa może uzyskać `Protected` dostęp do elementów klasy podstawowej klasy podstawowej i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="753a5-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="753a5-122">Chroniony dostęp nie jest nadzbiorem lub podzbiorem przyjaznego dostępu.</span><span class="sxs-lookup"><span data-stu-id="753a5-122">Protected access is not a superset or subset of friend access.</span></span>  
  
- <span data-ttu-id="753a5-123">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="753a5-123">**Access Modifiers.**</span></span> <span data-ttu-id="753a5-124">Słowa kluczowe określające poziom dostępu są nazywane *modyfikatorami dostępu*.</span><span class="sxs-lookup"><span data-stu-id="753a5-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="753a5-125">Aby porównać Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="753a5-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="753a5-126">`Protected` Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="753a5-126">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="753a5-127">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="753a5-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="753a5-128">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="753a5-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="753a5-129">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="753a5-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="753a5-130">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="753a5-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="753a5-131">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="753a5-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="753a5-132">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="753a5-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="753a5-133">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="753a5-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="753a5-134">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="753a5-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="753a5-135">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="753a5-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="753a5-136">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="753a5-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="753a5-137">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="753a5-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="753a5-138">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="753a5-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="753a5-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="753a5-139">See also</span></span>

- [<span data-ttu-id="753a5-140">Public</span><span class="sxs-lookup"><span data-stu-id="753a5-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="753a5-141">Friend</span><span class="sxs-lookup"><span data-stu-id="753a5-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="753a5-142">Private</span><span class="sxs-lookup"><span data-stu-id="753a5-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="753a5-143">Private Protected</span><span class="sxs-lookup"><span data-stu-id="753a5-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="753a5-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="753a5-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="753a5-145">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="753a5-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="753a5-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="753a5-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="753a5-147">Struktury</span><span class="sxs-lookup"><span data-stu-id="753a5-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="753a5-148">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="753a5-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
