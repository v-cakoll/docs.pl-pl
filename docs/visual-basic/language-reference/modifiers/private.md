---
title: Private
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 5600744aeca79a54f51a1f9ecd0ef00fed4b00fd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351328"
---
# <a name="private-visual-basic"></a><span data-ttu-id="2a926-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a926-102">Private (Visual Basic)</span></span>
<span data-ttu-id="2a926-103">Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie ich kontekstu deklaracji, łącznie z zawartymi w zawartych typach.</span><span class="sxs-lookup"><span data-stu-id="2a926-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a926-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a926-104">Remarks</span></span>  
 <span data-ttu-id="2a926-105">Jeśli element programistyczny reprezentuje funkcje własnościowe lub zawiera dane poufne, zazwyczaj trzeba ograniczyć dostęp do niego tak samo jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="2a926-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="2a926-106">Maksymalne ograniczenie można osiągnąć, zezwalając tylko na moduł, klasę lub strukturę, która je definiuje, aby uzyskać do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="2a926-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="2a926-107">Aby ograniczyć dostęp do elementu w ten sposób, można zadeklarować go przy użyciu `Private`.</span><span class="sxs-lookup"><span data-stu-id="2a926-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="2a926-108">Można również użyć modyfikatora [Private Protected](private-protected.md) Access, który umożliwia członkom dostęp z tej klasy i z klas pochodnych znajdujących się w jego zestawie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="2a926-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="2a926-109">Reguły</span><span class="sxs-lookup"><span data-stu-id="2a926-109">Rules</span></span>  

- <span data-ttu-id="2a926-110">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="2a926-110">**Declaration Context.**</span></span> <span data-ttu-id="2a926-111">`Private` można używać tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="2a926-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="2a926-112">Oznacza to, że kontekst deklaracji dla elementu `Private` musi być modułem, klasą lub strukturą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="2a926-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2a926-113">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="2a926-113">Behavior</span></span>  
  
- <span data-ttu-id="2a926-114">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="2a926-114">**Access Level.**</span></span> <span data-ttu-id="2a926-115">Cały kod w kontekście deklaracji może uzyskać dostęp do jego elementów `Private`.</span><span class="sxs-lookup"><span data-stu-id="2a926-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="2a926-116">Obejmuje to kod w obrębie zawartego typu, taki jak Klasa zagnieżdżona lub wyrażenie przypisania w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="2a926-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="2a926-117">Żaden kod spoza kontekstu deklaracji nie może uzyskać dostępu do jego `Private` elementów.</span><span class="sxs-lookup"><span data-stu-id="2a926-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="2a926-118">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="2a926-118">**Access Modifiers.**</span></span> <span data-ttu-id="2a926-119">Słowa kluczowe określające poziom dostępu są nazywane *modyfikatorami dostępu*.</span><span class="sxs-lookup"><span data-stu-id="2a926-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="2a926-120">Aby porównać Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2a926-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="2a926-121">Modyfikator `Private` może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="2a926-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="2a926-122">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a926-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="2a926-123">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a926-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="2a926-124">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a926-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="2a926-125">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a926-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="2a926-126">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a926-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="2a926-127">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a926-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="2a926-128">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a926-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="2a926-129">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a926-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="2a926-130">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a926-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="2a926-131">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a926-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="2a926-132">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a926-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="2a926-133">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a926-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2a926-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a926-134">See also</span></span>

- [<span data-ttu-id="2a926-135">Public</span><span class="sxs-lookup"><span data-stu-id="2a926-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="2a926-136">Protected</span><span class="sxs-lookup"><span data-stu-id="2a926-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="2a926-137">Friend</span><span class="sxs-lookup"><span data-stu-id="2a926-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="2a926-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="2a926-138">Private Protected</span></span>](./private-protected.md)
- <span data-ttu-id="2a926-139">[](./protected-friend.md)[Poziomy dostępu do chronionych znajomych w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="2a926-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>
- [<span data-ttu-id="2a926-140">Procedury</span><span class="sxs-lookup"><span data-stu-id="2a926-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="2a926-141">Struktury</span><span class="sxs-lookup"><span data-stu-id="2a926-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="2a926-142">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="2a926-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
