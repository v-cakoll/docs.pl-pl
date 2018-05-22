---
title: Prywatne chronione (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 23fd6583182a1fee544d0458dc3fc390aed86b9f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="69536-102">Prywatne chronione (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69536-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="69536-103">`Private Protected` Kombinacja słów kluczowych jest modyfikator dostępu elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="69536-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="69536-104">A `Private Protected` element członkowski jest dostępny na wszystkich elementów członkowskich w zawierająca go klasa, a także typy pochodzące od klasy zawierające, ale tylko wtedy, gdy występują w zawierający go zestaw.</span><span class="sxs-lookup"><span data-stu-id="69536-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span> 

<span data-ttu-id="69536-105">Można określić `Private Protected` tylko w elementach członkowskich klas; nie można zastosować `Private Protected` do elementów członkowskich struktury ponieważ struktur nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="69536-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="69536-106">`Private Protected` Modyfikator dostępu jest obsługiwane przez 15,5 cala Visual Basic i nowszych.</span><span class="sxs-lookup"><span data-stu-id="69536-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="69536-107">Aby go użyć, można dodać następującego elementu w pliku projektu (\*.vbproj) języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="69536-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="69536-108">Jak długo jako 15,5 cala Visual Basic lub nowszy jest zainstalowany w systemie, umożliwia ona korzystać z funkcji języka obsługiwane w najnowszej wersji kompilatora Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="69536-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="69536-109">W programie Visual Studio, wybierając pomocy F1 w `private protected` zawiera informacje pomocne w obu [prywatnej](private.md) lub [chronione](protected.md).</span><span class="sxs-lookup"><span data-stu-id="69536-109">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="69536-110">IDE wybiera jeden token pod kursorem zamiast wyraz złożony.</span><span class="sxs-lookup"><span data-stu-id="69536-110">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="69536-111">Reguły</span><span class="sxs-lookup"><span data-stu-id="69536-111">Rules</span></span>

- <span data-ttu-id="69536-112">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="69536-112">**Declaration Context.**</span></span> <span data-ttu-id="69536-113">Można użyć `Private Protected` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="69536-113">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="69536-114">Oznacza to, że w kontekście deklaracji `Protected` elementu musi być klasą i nie może być plik źródłowy, przestrzeni nazw, interfejsu, modułu, struktury lub procedury.</span><span class="sxs-lookup"><span data-stu-id="69536-114">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="69536-115">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="69536-115">Behavior</span></span>

- <span data-ttu-id="69536-116">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="69536-116">**Access Level.**</span></span> <span data-ttu-id="69536-117">Cały kod w klasie mogą uzyskiwać dostęp do swoich elementów.</span><span class="sxs-lookup"><span data-stu-id="69536-117">All code in a class can access its elements.</span></span> <span data-ttu-id="69536-118">Kod w dowolnej klasy, która pochodzi z klasy podstawowej i znajduje się w tym samym zestawie mogą uzyskać dostęp do wszystkich `Private Protected` elementy klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="69536-118">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="69536-119">Jednak kod w dowolnej klasy, która pochodzi z klasy podstawowej i jest zawarty w innym zestawie nie ma dostępu do klasy podstawowej `Private Protected` elementów.</span><span class="sxs-lookup"><span data-stu-id="69536-119">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="69536-120">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="69536-120">**Access Modifiers.**</span></span> <span data-ttu-id="69536-121">Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorów dostępu*.</span><span class="sxs-lookup"><span data-stu-id="69536-121">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="69536-122">Porównanie modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="69536-122">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>
  
 <span data-ttu-id="69536-123">`Private Protected` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="69536-123">The `Private Protected` modifier can be used in these contexts:</span></span>  
  
 <span data-ttu-id="69536-124">[Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md) klasy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="69536-124">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>  
  
 [<span data-ttu-id="69536-125">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69536-125">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="69536-126">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69536-126">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="69536-127">[Delegate — instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md) delegata zagnieżdżona w klasie</span><span class="sxs-lookup"><span data-stu-id="69536-127">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>  
  
 [<span data-ttu-id="69536-128">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69536-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 <span data-ttu-id="69536-129">[Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md) z eumeration zagnieżdżona w klasie</span><span class="sxs-lookup"><span data-stu-id="69536-129">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an eumeration nested in a class</span></span> 
  
 [<span data-ttu-id="69536-130">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69536-130">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="69536-131">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69536-131">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 <span data-ttu-id="69536-132">[Interface — instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md) interfejsu zagnieżdżona w klasie</span><span class="sxs-lookup"><span data-stu-id="69536-132">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span> 
  
 [<span data-ttu-id="69536-133">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69536-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 <span data-ttu-id="69536-134">[Struktura instrukcji](../../../visual-basic/language-reference/statements/structure-statement.md) struktury zagnieżdżone w klasie</span><span class="sxs-lookup"><span data-stu-id="69536-134">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span> 
  
 [<span data-ttu-id="69536-135">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69536-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="69536-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69536-136">See Also</span></span>

[<span data-ttu-id="69536-137">Public</span><span class="sxs-lookup"><span data-stu-id="69536-137">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
[<span data-ttu-id="69536-138">Protected</span><span class="sxs-lookup"><span data-stu-id="69536-138">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
<span data-ttu-id="69536-139">[Friend](friend.md) </span><span class="sxs-lookup"><span data-stu-id="69536-139">[Friend](friend.md) </span></span>  
[<span data-ttu-id="69536-140">Private</span><span class="sxs-lookup"><span data-stu-id="69536-140">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
<span data-ttu-id="69536-141">[Friend chronionych](./protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="69536-141">[Protected Friend](./protected-friend.md) </span></span>  
[<span data-ttu-id="69536-142">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69536-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[<span data-ttu-id="69536-143">Procedury</span><span class="sxs-lookup"><span data-stu-id="69536-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[<span data-ttu-id="69536-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="69536-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[<span data-ttu-id="69536-145">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="69536-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
