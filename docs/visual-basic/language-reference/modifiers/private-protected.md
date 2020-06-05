---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: b7d9f81e41950b92c787e2e50fb94fe3d7c07559
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362232"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="ba5a3-102">Prywatna chroniona (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba5a3-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="ba5a3-103">`Private Protected`Kombinacja słowa kluczowego jest modyfikatorem dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="ba5a3-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="ba5a3-104">`Private Protected`Członek jest dostępny dla wszystkich elementów członkowskich w swojej klasie zawierającej, a także typów pochodzących od klasy zawierającej, ale tylko wtedy, gdy znajdują się w jego zestawie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="ba5a3-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="ba5a3-105">Można określić `Private Protected` tylko dla elementów członkowskich klasy; nie można stosować `Private Protected` do elementów członkowskich struktury, ponieważ struktury nie mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="ba5a3-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="ba5a3-106">`Private Protected`Modyfikator dostępu jest obsługiwany przez Visual Basic 15,5 i nowsze.</span><span class="sxs-lookup"><span data-stu-id="ba5a3-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="ba5a3-107">Aby go użyć, można dodać następujący element do pliku projektu Visual Basic ( \* . vbproj).</span><span class="sxs-lookup"><span data-stu-id="ba5a3-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="ba5a3-108">Tak długo, jak Visual Basic 15,5 lub nowszy jest zainstalowany w systemie, umożliwia korzystanie ze wszystkich funkcji językowych obsługiwanych przez najnowszą wersję kompilatora Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="ba5a3-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="ba5a3-109">Aby uzyskać więcej informacji [, zobacz Ustawianie wersji językowej Visual Basic](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="ba5a3-109">For more information see [setting the Visual Basic language version](../configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ba5a3-110">W programie Visual Studio wybierz pozycję Pomoc F1, aby uzyskać pomoc dotyczącą `private protected` opcji [Private](private.md) lub [Protected](protected.md).</span><span class="sxs-lookup"><span data-stu-id="ba5a3-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="ba5a3-111">IDE wybiera pojedynczy token w obszarze kursora zamiast słowa złożonego.</span><span class="sxs-lookup"><span data-stu-id="ba5a3-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="ba5a3-112">Reguły</span><span class="sxs-lookup"><span data-stu-id="ba5a3-112">Rules</span></span>

- <span data-ttu-id="ba5a3-113">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="ba5a3-113">**Declaration Context.**</span></span> <span data-ttu-id="ba5a3-114">Można używać `Private Protected` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="ba5a3-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="ba5a3-115">Oznacza to, że kontekst deklaracji dla `Protected` elementu musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, modułem, strukturą ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="ba5a3-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="ba5a3-116">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="ba5a3-116">Behavior</span></span>

- <span data-ttu-id="ba5a3-117">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="ba5a3-117">**Access Level.**</span></span> <span data-ttu-id="ba5a3-118">Cały kod w klasie ma dostęp do jego elementów.</span><span class="sxs-lookup"><span data-stu-id="ba5a3-118">All code in a class can access its elements.</span></span> <span data-ttu-id="ba5a3-119">Kod w dowolnej klasie, która dziedziczy z klasy bazowej i znajduje się w tym samym zestawie, może uzyskać dostęp do wszystkich `Private Protected` elementów klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="ba5a3-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="ba5a3-120">Jednak kod w dowolnej klasie, która dziedziczy z klasy bazowej i znajduje się w innym zestawie nie może uzyskać dostępu do elementów klasy bazowej `Private Protected` .</span><span class="sxs-lookup"><span data-stu-id="ba5a3-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="ba5a3-121">**Modyfikatory dostępu.**</span><span class="sxs-lookup"><span data-stu-id="ba5a3-121">**Access Modifiers.**</span></span> <span data-ttu-id="ba5a3-122">Słowa kluczowe określające poziom dostępu są nazywane *modyfikatorami dostępu*.</span><span class="sxs-lookup"><span data-stu-id="ba5a3-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="ba5a3-123">Aby porównać Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ba5a3-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="ba5a3-124">`Private Protected`Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="ba5a3-124">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="ba5a3-125">[Instrukcja klasy](../statements/class-statement.md) klasy zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="ba5a3-125">[Class Statement](../statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="ba5a3-126">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ba5a3-126">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="ba5a3-127">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="ba5a3-127">Declare Statement</span></span>](../statements/declare-statement.md)

- <span data-ttu-id="ba5a3-128">[Delegata — instrukcja](../statements/delegate-statement.md) delegata zagnieżdżona w klasie</span><span class="sxs-lookup"><span data-stu-id="ba5a3-128">[Delegate Statement](../statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="ba5a3-129">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ba5a3-129">Dim Statement</span></span>](../statements/dim-statement.md)

- <span data-ttu-id="ba5a3-130">[Instrukcja enum](../statements/enum-statement.md) wyliczenia zagnieżdżona w klasie</span><span class="sxs-lookup"><span data-stu-id="ba5a3-130">[Enum Statement](../statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="ba5a3-131">Event — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="ba5a3-131">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="ba5a3-132">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ba5a3-132">Function Statement</span></span>](../statements/function-statement.md)

- <span data-ttu-id="ba5a3-133">[Instrukcja interfejsu](../statements/interface-statement.md) w interfejsie zagnieżdżonym w klasie</span><span class="sxs-lookup"><span data-stu-id="ba5a3-133">[Interface Statement](../statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="ba5a3-134">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="ba5a3-134">Property Statement</span></span>](../statements/property-statement.md)

- <span data-ttu-id="ba5a3-135">[Instrukcja struktury](../statements/structure-statement.md) struktury zagnieżdżonej w klasie</span><span class="sxs-lookup"><span data-stu-id="ba5a3-135">[Structure Statement](../statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="ba5a3-136">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ba5a3-136">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="ba5a3-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba5a3-137">See also</span></span>

- [<span data-ttu-id="ba5a3-138">Społeczeństwo</span><span class="sxs-lookup"><span data-stu-id="ba5a3-138">Public</span></span>](public.md)
- [<span data-ttu-id="ba5a3-139">Chronione</span><span class="sxs-lookup"><span data-stu-id="ba5a3-139">Protected</span></span>](protected.md)
- [<span data-ttu-id="ba5a3-140">Osoby</span><span class="sxs-lookup"><span data-stu-id="ba5a3-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="ba5a3-141">Użytek</span><span class="sxs-lookup"><span data-stu-id="ba5a3-141">Private</span></span>](private.md)
- [<span data-ttu-id="ba5a3-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="ba5a3-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="ba5a3-143">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba5a3-143">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="ba5a3-144">Procedury</span><span class="sxs-lookup"><span data-stu-id="ba5a3-144">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="ba5a3-145">Struktury</span><span class="sxs-lookup"><span data-stu-id="ba5a3-145">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="ba5a3-146">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="ba5a3-146">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
