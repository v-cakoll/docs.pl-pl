---
title: Prywatny chroniony (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 70f725712d52ad055ff69046096da10b8edfb67c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701147"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="6a6a0-102">Prywatny chroniony (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a6a0-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="6a6a0-103">`Private Protected` Kombinacja słów kluczowych jest modyfikator dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="6a6a0-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="6a6a0-104">A `Private Protected` element członkowski jest dostępna, wszystkie elementy członkowskie w swojej klasie zawierający, a także typów pochodnych typu zawierającego klasy, ale tylko wtedy, gdy występują w jego zawierające zestaw.</span><span class="sxs-lookup"><span data-stu-id="6a6a0-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span> 

<span data-ttu-id="6a6a0-105">Można określić `Private Protected` tylko na składowych klas; nie można zastosować `Private Protected` do elementów członkowskich struktury ponieważ struktury nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="6a6a0-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="6a6a0-106">`Private Protected` Modyfikator dostępu jest obsługiwane w wersji 15.5 programu Visual Basic lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="6a6a0-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="6a6a0-107">Aby go użyć, można dodać następującego elementu do projektu języka Visual Basic (\*.vbproj) pliku.</span><span class="sxs-lookup"><span data-stu-id="6a6a0-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="6a6a0-108">Jak długo, jak 15.5 Visual Basic lub nowszy jest zainstalowany w systemie, umożliwia korzystanie z zalet wszystkich funkcji językowych obsługiwanych przez najnowszą wersję kompilatora języka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="6a6a0-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="6a6a0-109">Aby uzyskać więcej informacji, zobacz [ustawienie wersji języka Visual Basic](../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="6a6a0-109">For more information see [setting the Visual Basic language version](../../language-reference/configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6a6a0-110">W programie Visual Studio, wybierając opcję pomocy F1 na `private protected` zapewnia pomoc dla dowolnego [prywatnej](private.md) lub [chronione](protected.md).</span><span class="sxs-lookup"><span data-stu-id="6a6a0-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="6a6a0-111">Środowisko IDE wybiera jednego tokenu pod kursorem, a nie jako wyraz złożony.</span><span class="sxs-lookup"><span data-stu-id="6a6a0-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="6a6a0-112">reguły</span><span class="sxs-lookup"><span data-stu-id="6a6a0-112">Rules</span></span>

- <span data-ttu-id="6a6a0-113">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="6a6a0-113">**Declaration Context.**</span></span> <span data-ttu-id="6a6a0-114">Możesz użyć `Private Protected` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="6a6a0-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="6a6a0-115">Oznacza to, że kontekst deklaracji `Protected` element musi być klasą i nie może być plik źródłowy, przestrzeń nazw, interfejsu, moduł, struktura lub procedury.</span><span class="sxs-lookup"><span data-stu-id="6a6a0-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="6a6a0-116">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="6a6a0-116">Behavior</span></span>

- <span data-ttu-id="6a6a0-117">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="6a6a0-117">**Access Level.**</span></span> <span data-ttu-id="6a6a0-118">Cały kod w klasie mogą uzyskać dostęp do jego elementów.</span><span class="sxs-lookup"><span data-stu-id="6a6a0-118">All code in a class can access its elements.</span></span> <span data-ttu-id="6a6a0-119">Kod w każdej klasy, która pochodzi z klasy bazowej i jest zawarty w tym samym zestawie mogą uzyskać dostęp do wszystkich `Private Protected` elementów klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="6a6a0-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="6a6a0-120">Jednak kod w każdej klasy, która pochodzi z klasy bazowej i znajduje się w innym zestawie nie może uzyskiwać dostęp do klasy bazowej `Private Protected` elementów.</span><span class="sxs-lookup"><span data-stu-id="6a6a0-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="6a6a0-121">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="6a6a0-121">**Access Modifiers.**</span></span> <span data-ttu-id="6a6a0-122">Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorach dostępu*.</span><span class="sxs-lookup"><span data-stu-id="6a6a0-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="6a6a0-123">Dla porównania modyfikatory dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6a6a0-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>
  
 <span data-ttu-id="6a6a0-124">`Private Protected` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="6a6a0-124">The `Private Protected` modifier can be used in these contexts:</span></span>  
  
 <span data-ttu-id="6a6a0-125">[Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md) klasy zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="6a6a0-125">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>  
  
 [<span data-ttu-id="6a6a0-126">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6a6a0-126">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="6a6a0-127">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6a6a0-127">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="6a6a0-128">[Delegate — instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md) delegata zagnieżdżona w klasie</span><span class="sxs-lookup"><span data-stu-id="6a6a0-128">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>  
  
 [<span data-ttu-id="6a6a0-129">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6a6a0-129">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 <span data-ttu-id="6a6a0-130">[Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md) z eumeration zagnieżdżona w klasie</span><span class="sxs-lookup"><span data-stu-id="6a6a0-130">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an eumeration nested in a class</span></span> 
  
 [<span data-ttu-id="6a6a0-131">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6a6a0-131">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="6a6a0-132">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6a6a0-132">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 <span data-ttu-id="6a6a0-133">[Interface — instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md) interfejsu zagnieżdżona w klasie</span><span class="sxs-lookup"><span data-stu-id="6a6a0-133">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span> 
  
 [<span data-ttu-id="6a6a0-134">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="6a6a0-134">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 <span data-ttu-id="6a6a0-135">[Struktury instrukcji](../../../visual-basic/language-reference/statements/structure-statement.md) struktury zagnieżdżona w klasie</span><span class="sxs-lookup"><span data-stu-id="6a6a0-135">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span> 
  
 [<span data-ttu-id="6a6a0-136">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6a6a0-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6a6a0-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a6a0-137">See also</span></span>

- [<span data-ttu-id="6a6a0-138">Public</span><span class="sxs-lookup"><span data-stu-id="6a6a0-138">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="6a6a0-139">Protected</span><span class="sxs-lookup"><span data-stu-id="6a6a0-139">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="6a6a0-140">Friend</span><span class="sxs-lookup"><span data-stu-id="6a6a0-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="6a6a0-141">Private</span><span class="sxs-lookup"><span data-stu-id="6a6a0-141">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="6a6a0-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="6a6a0-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="6a6a0-143">Poziomy dostępu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a6a0-143">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="6a6a0-144">Procedury</span><span class="sxs-lookup"><span data-stu-id="6a6a0-144">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="6a6a0-145">Struktury</span><span class="sxs-lookup"><span data-stu-id="6a6a0-145">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="6a6a0-146">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="6a6a0-146">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
