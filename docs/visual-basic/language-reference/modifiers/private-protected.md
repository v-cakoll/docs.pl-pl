---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 265141f77f4a61a61414a07214830feaa8a1ab05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351345"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="54fb5-102">Prywatna chroniona (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54fb5-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="54fb5-103">Kombinacja słowa kluczowego `Private Protected` jest modyfikatorem dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="54fb5-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="54fb5-104">Członek `Private Protected` jest dostępny dla wszystkich elementów członkowskich w klasie zawierającej, a także typów pochodzących od klasy zawierającej, ale tylko wtedy, gdy znajdują się w jego zestawie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="54fb5-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="54fb5-105">Można określić `Private Protected` tylko dla elementów członkowskich klasy; nie można zastosować `Private Protected` do elementów członkowskich struktury, ponieważ struktury nie mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="54fb5-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="54fb5-106">Modyfikator dostępu `Private Protected` jest obsługiwany przez Visual Basic 15,5 i nowsze.</span><span class="sxs-lookup"><span data-stu-id="54fb5-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="54fb5-107">Aby go użyć, można dodać następujący element do pliku projektu Visual Basic (\*. vbproj).</span><span class="sxs-lookup"><span data-stu-id="54fb5-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="54fb5-108">Tak długo, jak Visual Basic 15,5 lub nowszy jest zainstalowany w systemie, umożliwia korzystanie ze wszystkich funkcji językowych obsługiwanych przez najnowszą wersję kompilatora Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="54fb5-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="54fb5-109">Aby uzyskać więcej informacji [, zobacz Ustawianie wersji językowej Visual Basic](../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="54fb5-109">For more information see [setting the Visual Basic language version](../../language-reference/configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="54fb5-110">W programie Visual Studio wybierz pozycję Pomoc F1 na `private protected` zawiera pomoc dla opcji [Private](private.md) lub [Protected](protected.md).</span><span class="sxs-lookup"><span data-stu-id="54fb5-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="54fb5-111">IDE wybiera pojedynczy token w obszarze kursora zamiast słowa złożonego.</span><span class="sxs-lookup"><span data-stu-id="54fb5-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="54fb5-112">Reguły</span><span class="sxs-lookup"><span data-stu-id="54fb5-112">Rules</span></span>

- <span data-ttu-id="54fb5-113">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="54fb5-113">**Declaration Context.**</span></span> <span data-ttu-id="54fb5-114">`Private Protected` można używać tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="54fb5-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="54fb5-115">Oznacza to, że kontekst deklaracji dla elementu `Protected` musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, strukturą ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="54fb5-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="54fb5-116">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="54fb5-116">Behavior</span></span>

- <span data-ttu-id="54fb5-117">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="54fb5-117">**Access Level.**</span></span> <span data-ttu-id="54fb5-118">Cały kod w klasie ma dostęp do jego elementów.</span><span class="sxs-lookup"><span data-stu-id="54fb5-118">All code in a class can access its elements.</span></span> <span data-ttu-id="54fb5-119">Kod w dowolnej klasie, która dziedziczy z klasy bazowej i znajduje się w tym samym zestawie, może uzyskać dostęp do wszystkich elementów `Private Protected` klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="54fb5-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="54fb5-120">Jednak kod w dowolnej klasie, która dziedziczy z klasy bazowej i jest zawarty w innym zestawie, nie może uzyskać dostępu do klasy bazowej `Private Protected` elementów.</span><span class="sxs-lookup"><span data-stu-id="54fb5-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="54fb5-121">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="54fb5-121">**Access Modifiers.**</span></span> <span data-ttu-id="54fb5-122">Słowa kluczowe określające poziom dostępu są nazywane *modyfikatorami dostępu*.</span><span class="sxs-lookup"><span data-stu-id="54fb5-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="54fb5-123">Aby porównać Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="54fb5-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="54fb5-124">Modyfikator `Private Protected` może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="54fb5-124">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="54fb5-125">[Instrukcja klasy](../../../visual-basic/language-reference/statements/class-statement.md) klasy zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="54fb5-125">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="54fb5-126">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fb5-126">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="54fb5-127">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fb5-127">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- <span data-ttu-id="54fb5-128">[Delegata — instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md) delegata zagnieżdżona w klasie</span><span class="sxs-lookup"><span data-stu-id="54fb5-128">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="54fb5-129">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fb5-129">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- <span data-ttu-id="54fb5-130">[Instrukcja enum](../../../visual-basic/language-reference/statements/enum-statement.md) wyliczenia zagnieżdżona w klasie</span><span class="sxs-lookup"><span data-stu-id="54fb5-130">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="54fb5-131">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fb5-131">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="54fb5-132">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fb5-132">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- <span data-ttu-id="54fb5-133">[Instrukcja interfejsu](../../../visual-basic/language-reference/statements/interface-statement.md) w interfejsie zagnieżdżonym w klasie</span><span class="sxs-lookup"><span data-stu-id="54fb5-133">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="54fb5-134">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fb5-134">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- <span data-ttu-id="54fb5-135">[Instrukcja struktury](../../../visual-basic/language-reference/statements/structure-statement.md) struktury zagnieżdżonej w klasie</span><span class="sxs-lookup"><span data-stu-id="54fb5-135">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="54fb5-136">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fb5-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="54fb5-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54fb5-137">See also</span></span>

- [<span data-ttu-id="54fb5-138">Public</span><span class="sxs-lookup"><span data-stu-id="54fb5-138">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="54fb5-139">Protected</span><span class="sxs-lookup"><span data-stu-id="54fb5-139">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="54fb5-140">Friend</span><span class="sxs-lookup"><span data-stu-id="54fb5-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="54fb5-141">Private</span><span class="sxs-lookup"><span data-stu-id="54fb5-141">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="54fb5-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="54fb5-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="54fb5-143">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54fb5-143">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="54fb5-144">Procedury</span><span class="sxs-lookup"><span data-stu-id="54fb5-144">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="54fb5-145">Struktury</span><span class="sxs-lookup"><span data-stu-id="54fb5-145">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="54fb5-146">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="54fb5-146">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
