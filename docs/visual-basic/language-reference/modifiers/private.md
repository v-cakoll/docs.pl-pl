---
title: Private
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 524f03e77e075bef08a1b41b563985de41baacb6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404813"
---
# <a name="private-visual-basic"></a><span data-ttu-id="5a6dd-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a6dd-102">Private (Visual Basic)</span></span>
<span data-ttu-id="5a6dd-103">Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie ich kontekstu deklaracji, łącznie z zawartymi w zawartych typach.</span><span class="sxs-lookup"><span data-stu-id="5a6dd-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a6dd-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a6dd-104">Remarks</span></span>  
 <span data-ttu-id="5a6dd-105">Jeśli element programistyczny reprezentuje funkcje własnościowe lub zawiera dane poufne, zazwyczaj trzeba ograniczyć dostęp do niego tak samo jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="5a6dd-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="5a6dd-106">Maksymalne ograniczenie można osiągnąć, zezwalając tylko na moduł, klasę lub strukturę, która je definiuje, aby uzyskać do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="5a6dd-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="5a6dd-107">Aby ograniczyć dostęp do elementu w ten sposób, można go zadeklarować za pomocą `Private` .</span><span class="sxs-lookup"><span data-stu-id="5a6dd-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="5a6dd-108">Można również użyć modyfikatora [Private Protected](private-protected.md) Access, który umożliwia członkom dostęp z tej klasy i z klas pochodnych znajdujących się w jego zestawie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="5a6dd-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="5a6dd-109">Reguły</span><span class="sxs-lookup"><span data-stu-id="5a6dd-109">Rules</span></span>  

- <span data-ttu-id="5a6dd-110">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="5a6dd-110">**Declaration Context.**</span></span> <span data-ttu-id="5a6dd-111">Można używać `Private` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="5a6dd-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="5a6dd-112">Oznacza to, że kontekst deklaracji dla `Private` elementu musi być modułem, klasą lub strukturą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="5a6dd-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="5a6dd-113">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="5a6dd-113">Behavior</span></span>  
  
- <span data-ttu-id="5a6dd-114">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="5a6dd-114">**Access Level.**</span></span> <span data-ttu-id="5a6dd-115">Cały kod w kontekście deklaracji może uzyskać dostęp do jego `Private` elementów.</span><span class="sxs-lookup"><span data-stu-id="5a6dd-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="5a6dd-116">Obejmuje to kod w obrębie zawartego typu, taki jak Klasa zagnieżdżona lub wyrażenie przypisania w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="5a6dd-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="5a6dd-117">Żaden kod spoza kontekstu deklaracji nie może uzyskać dostępu do jego `Private` elementów.</span><span class="sxs-lookup"><span data-stu-id="5a6dd-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="5a6dd-118">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="5a6dd-118">**Access Modifiers.**</span></span> <span data-ttu-id="5a6dd-119">Słowa kluczowe określające poziom dostępu są nazywane *modyfikatorami dostępu*.</span><span class="sxs-lookup"><span data-stu-id="5a6dd-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="5a6dd-120">Aby porównać Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5a6dd-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="5a6dd-121">`Private`Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="5a6dd-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="5a6dd-122">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a6dd-122">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="5a6dd-123">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a6dd-123">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="5a6dd-124">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a6dd-124">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="5a6dd-125">Delegate — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a6dd-125">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="5a6dd-126">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a6dd-126">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="5a6dd-127">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a6dd-127">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="5a6dd-128">Event — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a6dd-128">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="5a6dd-129">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a6dd-129">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="5a6dd-130">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a6dd-130">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="5a6dd-131">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a6dd-131">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="5a6dd-132">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a6dd-132">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="5a6dd-133">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a6dd-133">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5a6dd-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a6dd-134">See also</span></span>

- [<span data-ttu-id="5a6dd-135">Społeczeństwo</span><span class="sxs-lookup"><span data-stu-id="5a6dd-135">Public</span></span>](public.md)
- [<span data-ttu-id="5a6dd-136">Chronione</span><span class="sxs-lookup"><span data-stu-id="5a6dd-136">Protected</span></span>](protected.md)
- [<span data-ttu-id="5a6dd-137">Osoby</span><span class="sxs-lookup"><span data-stu-id="5a6dd-137">Friend</span></span>](friend.md)
- [<span data-ttu-id="5a6dd-138">Prywatne chronione</span><span class="sxs-lookup"><span data-stu-id="5a6dd-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="5a6dd-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="5a6dd-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="5a6dd-140">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a6dd-140">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="5a6dd-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="5a6dd-141">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="5a6dd-142">Struktury</span><span class="sxs-lookup"><span data-stu-id="5a6dd-142">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="5a6dd-143">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="5a6dd-143">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
