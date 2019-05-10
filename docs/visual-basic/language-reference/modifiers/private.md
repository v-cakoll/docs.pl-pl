---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: ddb2d165de330758f58fbbcb5872e820e639808f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642781"
---
# <a name="private-visual-basic"></a><span data-ttu-id="5a99f-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a99f-102">Private (Visual Basic)</span></span>
<span data-ttu-id="5a99f-103">Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie ich kontekst deklaracji, łącznie z w obrębie wszystkich typów zawartych.</span><span class="sxs-lookup"><span data-stu-id="5a99f-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a99f-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a99f-104">Remarks</span></span>  
 <span data-ttu-id="5a99f-105">Jeśli elementu programistycznego reprezentuje własnościowych funkcji lub zawiera dane poufne, zazwyczaj chcesz ograniczyć dostęp do niego jako ściśle.</span><span class="sxs-lookup"><span data-stu-id="5a99f-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="5a99f-106">Ograniczenie maksymalnej można osiągnąć, zezwalając tylko modułu, klasy lub struktury, który definiuje go do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="5a99f-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="5a99f-107">Aby ograniczyć dostęp do elementu w ten sposób, można zadeklarować za pomocą `Private`.</span><span class="sxs-lookup"><span data-stu-id="5a99f-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="5a99f-108">Można również użyć [Private Protected](private-protected.md) modyfikator dostępu, co sprawia, że członek jest dostępny z tej klasy i znajduje się w jego zawierające zestaw klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="5a99f-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="5a99f-109">reguły</span><span class="sxs-lookup"><span data-stu-id="5a99f-109">Rules</span></span>  

- <span data-ttu-id="5a99f-110">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="5a99f-110">**Declaration Context.**</span></span> <span data-ttu-id="5a99f-111">Możesz użyć `Private` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="5a99f-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="5a99f-112">Oznacza to, że kontekst deklaracji `Private` elementu musi być modułu, klasy lub struktury, a nie może być plikiem źródłowym, przestrzeń nazw, interfejs lub procedury.</span><span class="sxs-lookup"><span data-stu-id="5a99f-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="5a99f-113">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="5a99f-113">Behavior</span></span>  
  
- <span data-ttu-id="5a99f-114">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="5a99f-114">**Access Level.**</span></span> <span data-ttu-id="5a99f-115">Cały kod w kontekście deklaracji mogą uzyskiwać dostęp do jego `Private` elementów.</span><span class="sxs-lookup"><span data-stu-id="5a99f-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="5a99f-116">W tym kodu w ramach zamkniętego typu, na przykład klasa zagnieżdżona lub wyrażenia przypisania w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="5a99f-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="5a99f-117">Żaden kod poza kontekstem deklaracji mogą uzyskiwać dostęp do jego `Private` elementów.</span><span class="sxs-lookup"><span data-stu-id="5a99f-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="5a99f-118">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="5a99f-118">**Access Modifiers.**</span></span> <span data-ttu-id="5a99f-119">Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorach dostępu*.</span><span class="sxs-lookup"><span data-stu-id="5a99f-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="5a99f-120">Dla porównania modyfikatory dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5a99f-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="5a99f-121">`Private` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="5a99f-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="5a99f-122">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a99f-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="5a99f-123">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a99f-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="5a99f-124">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a99f-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="5a99f-125">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a99f-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="5a99f-126">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a99f-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="5a99f-127">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a99f-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="5a99f-128">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a99f-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="5a99f-129">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a99f-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="5a99f-130">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="5a99f-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="5a99f-131">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="5a99f-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="5a99f-132">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a99f-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="5a99f-133">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a99f-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5a99f-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a99f-134">See also</span></span>

- [<span data-ttu-id="5a99f-135">Public</span><span class="sxs-lookup"><span data-stu-id="5a99f-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="5a99f-136">Protected</span><span class="sxs-lookup"><span data-stu-id="5a99f-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="5a99f-137">Friend</span><span class="sxs-lookup"><span data-stu-id="5a99f-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="5a99f-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="5a99f-138">Private Protected</span></span>](./private-protected.md)
- <span data-ttu-id="5a99f-139">[Protected Friend](./protected-friend.md)[dostęp do poziomów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="5a99f-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>
- [<span data-ttu-id="5a99f-140">Procedury</span><span class="sxs-lookup"><span data-stu-id="5a99f-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="5a99f-141">Struktury</span><span class="sxs-lookup"><span data-stu-id="5a99f-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="5a99f-142">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="5a99f-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
