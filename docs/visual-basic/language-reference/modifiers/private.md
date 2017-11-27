---
title: Private (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07450c2a5443bf6bc147cad2cfc779072bfc363b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="private-visual-basic"></a><span data-ttu-id="565ed-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="565ed-102">Private (Visual Basic)</span></span>
<span data-ttu-id="565ed-103">Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie ich kontekście deklaracji, łącznie z wewnątrz żadnych typów zawartych w niej.</span><span class="sxs-lookup"><span data-stu-id="565ed-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="565ed-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="565ed-104">Remarks</span></span>  
 <span data-ttu-id="565ed-105">Jeśli elementu programistycznego reprezentuje własnościowych funkcji lub zawiera dane poufne, mają zwykle jako ściśle ograniczyć do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="565ed-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="565ed-106">Ograniczenie maksymalnej można osiągnąć, zezwalając tylko modułu, klasy lub struktury, definiujący go do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="565ed-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="565ed-107">Aby ograniczyć dostęp do elementu w ten sposób, mogą zadeklarować za pomocą `Private`.</span><span class="sxs-lookup"><span data-stu-id="565ed-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="565ed-108">Reguły</span><span class="sxs-lookup"><span data-stu-id="565ed-108">Rules</span></span>  
  
-   <span data-ttu-id="565ed-109">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="565ed-109">**Declaration Context.**</span></span> <span data-ttu-id="565ed-110">Można użyć `Private` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="565ed-110">You can use `Private` only at module level.</span></span> <span data-ttu-id="565ed-111">Oznacza to, że w kontekście deklaracji `Private` elementu musi być modułu, klasy lub struktury i nie może być plik źródłowy, przestrzeń nazw, interfejsem lub procedury.</span><span class="sxs-lookup"><span data-stu-id="565ed-111">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="565ed-112">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="565ed-112">Behavior</span></span>  
  
-   <span data-ttu-id="565ed-113">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="565ed-113">**Access Level.**</span></span> <span data-ttu-id="565ed-114">Cały kod w kontekście deklaracji mogą uzyskiwać dostęp do jego `Private` elementów.</span><span class="sxs-lookup"><span data-stu-id="565ed-114">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="565ed-115">W tym kodu w ramach ograniczonego typu, na przykład klasa zagnieżdżona lub wyrażenie przypisania w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="565ed-115">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="565ed-116">Brak kodu poza kontekstem deklaracji mogą uzyskiwać dostęp do jego `Private` elementów.</span><span class="sxs-lookup"><span data-stu-id="565ed-116">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="565ed-117">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="565ed-117">**Access Modifiers.**</span></span> <span data-ttu-id="565ed-118">Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="565ed-118">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="565ed-119">Porównanie modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="565ed-119">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="565ed-120">`Private` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="565ed-120">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="565ed-121">Class — instrukcja</span><span class="sxs-lookup"><span data-stu-id="565ed-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="565ed-122">Const — instrukcja</span><span class="sxs-lookup"><span data-stu-id="565ed-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="565ed-123">DECLARE — instrukcja</span><span class="sxs-lookup"><span data-stu-id="565ed-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="565ed-124">Delegate — instrukcja</span><span class="sxs-lookup"><span data-stu-id="565ed-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="565ed-125">Dim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="565ed-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="565ed-126">Enum — instrukcja</span><span class="sxs-lookup"><span data-stu-id="565ed-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="565ed-127">Event — instrukcja</span><span class="sxs-lookup"><span data-stu-id="565ed-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="565ed-128">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="565ed-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="565ed-129">Interface — instrukcja</span><span class="sxs-lookup"><span data-stu-id="565ed-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="565ed-130">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="565ed-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="565ed-131">Structure — instrukcja</span><span class="sxs-lookup"><span data-stu-id="565ed-131">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="565ed-132">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="565ed-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="565ed-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="565ed-133">See Also</span></span>  
 [<span data-ttu-id="565ed-134">Publiczna</span><span class="sxs-lookup"><span data-stu-id="565ed-134">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="565ed-135">Chronione</span><span class="sxs-lookup"><span data-stu-id="565ed-135">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="565ed-136">Friend</span><span class="sxs-lookup"><span data-stu-id="565ed-136">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="565ed-137">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="565ed-137">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="565ed-138">Procedury</span><span class="sxs-lookup"><span data-stu-id="565ed-138">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="565ed-139">Struktury</span><span class="sxs-lookup"><span data-stu-id="565ed-139">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="565ed-140">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="565ed-140">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
