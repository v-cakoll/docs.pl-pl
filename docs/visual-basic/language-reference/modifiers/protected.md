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
ms.openlocfilehash: 3866e7dd72b9e7145cf76f480bb5ffc6239a775e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="protected-visual-basic"></a><span data-ttu-id="c1b2a-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1b2a-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="c1b2a-103">Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie swojej klasy lub z klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-103">Specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1b2a-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1b2a-104">Remarks</span></span>  
 <span data-ttu-id="c1b2a-105">Czasami elementu programistycznego zadeklarowana w klasie zawierają dane poufne lub ograniczone kod, a użytkownik chce ograniczyć dostęp do elementu.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="c1b2a-106">Jednak jeśli oczekujesz hierarchii klas pochodnych klasy jest dziedziczona, może być konieczne dla tych klas pochodnych dostępu do danych lub kodu.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="c1b2a-107">W takim przypadku ma element ma być dostępny zarówno z klasy podstawowej i wszystkich klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="c1b2a-108">Aby ograniczyć dostęp do elementu w ten sposób, mogą zadeklarować za pomocą `Protected`.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c1b2a-109">Reguły</span><span class="sxs-lookup"><span data-stu-id="c1b2a-109">Rules</span></span>  
  
-   <span data-ttu-id="c1b2a-110">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="c1b2a-110">**Declaration Context.**</span></span> <span data-ttu-id="c1b2a-111">Można użyć `Protected` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-111">You can use `Protected` only at class level.</span></span> <span data-ttu-id="c1b2a-112">Oznacza to, że w kontekście deklaracji `Protected` elementu musi być klasą i nie może być plik źródłowy, przestrzeni nazw, interfejsu, modułu, struktury lub procedury.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-112">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
-   <span data-ttu-id="c1b2a-113">**Łączna modyfikatorów.**</span><span class="sxs-lookup"><span data-stu-id="c1b2a-113">**Combined Modifiers.**</span></span> <span data-ttu-id="c1b2a-114">Można użyć `Protected` modyfikator razem z [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modyfikator w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-114">You can use the `Protected` modifier together with the [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modifier in the same declaration.</span></span> <span data-ttu-id="c1b2a-115">Ta kombinacja sprawia, że zadeklarowane elementy jest dostępna z dowolnego miejsca w tym samym zestawie, swojej klasy oraz klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-115">This combination makes the declared elements accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="c1b2a-116">Można określić `Protected Friend` tylko w elementach członkowskich klas.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-116">You can specify `Protected Friend` only on members of classes.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="c1b2a-117">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="c1b2a-117">Behavior</span></span>  
  
-   <span data-ttu-id="c1b2a-118">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="c1b2a-118">**Access Level.**</span></span> <span data-ttu-id="c1b2a-119">Cały kod w klasie mogą uzyskiwać dostęp do swoich elementów.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-119">All code in a class can access its elements.</span></span> <span data-ttu-id="c1b2a-120">Kod w dowolnej klasy, która pochodzi z klasy podstawowej można uzyskać dostęp do wszystkich `Protected` elementy klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-120">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="c1b2a-121">Jest to istotne dla wszystkich generacji pochodnym.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-121">This is true for all generations of derivation.</span></span> <span data-ttu-id="c1b2a-122">Oznacza to, że klasa może uzyskać dostęp `Protected` elementy klasy podstawowej klasy podstawowej i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-122">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="c1b2a-123">Chronionego dostępu nie jest nadzbiorem lub podzbiór przyjaznego dostępu.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-123">Protected access is not a superset or subset of friend access.</span></span>  
  
-   <span data-ttu-id="c1b2a-124">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="c1b2a-124">**Access Modifiers.**</span></span> <span data-ttu-id="c1b2a-125">Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-125">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="c1b2a-126">Porównanie modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c1b2a-126">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="c1b2a-127">`Protected` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="c1b2a-127">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c1b2a-128">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1b2a-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="c1b2a-129">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1b2a-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="c1b2a-130">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1b2a-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="c1b2a-131">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1b2a-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="c1b2a-132">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1b2a-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="c1b2a-133">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1b2a-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="c1b2a-134">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1b2a-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="c1b2a-135">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1b2a-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="c1b2a-136">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1b2a-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="c1b2a-137">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1b2a-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="c1b2a-138">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1b2a-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="c1b2a-139">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1b2a-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c1b2a-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1b2a-140">See Also</span></span>  
 [<span data-ttu-id="c1b2a-141">Public</span><span class="sxs-lookup"><span data-stu-id="c1b2a-141">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="c1b2a-142">Friend</span><span class="sxs-lookup"><span data-stu-id="c1b2a-142">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="c1b2a-143">Private</span><span class="sxs-lookup"><span data-stu-id="c1b2a-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="c1b2a-144">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c1b2a-144">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="c1b2a-145">Procedury</span><span class="sxs-lookup"><span data-stu-id="c1b2a-145">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="c1b2a-146">Struktury</span><span class="sxs-lookup"><span data-stu-id="c1b2a-146">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="c1b2a-147">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="c1b2a-147">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
