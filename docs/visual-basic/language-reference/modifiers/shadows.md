---
title: Shadows
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: 7aed6bec21bd484cca019b061bd5915de13a9eb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402710"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="eb1c5-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb1c5-102">Shadows (Visual Basic)</span></span>

<span data-ttu-id="eb1c5-103">Określa, że zadeklarowany element programistyczny ponownie deklaruje i ukrywa element o identycznej nazwie, lub zestaw przeciążonych elementów w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb1c5-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb1c5-104">Remarks</span></span>

<span data-ttu-id="eb1c5-105">Głównym celem przesłaniania (który jest również znany jako *ukrywanie według nazwy*) jest zachowanie definicji elementów członkowskich klasy.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="eb1c5-106">Klasa bazowa może ulec zmianie, która tworzy element o takiej samej nazwie jak już zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="eb1c5-107">W takim przypadku `Shadows` modyfikator wymusza odwołania za pomocą klasy, aby można było rozpoznać element członkowski zdefiniowany przez użytkownika, a nie do nowego elementu klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="eb1c5-108">Zarówno przesłanianie, jak i przesłonięcie przedefiniują Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="eb1c5-109">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="eb1c5-109">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="eb1c5-110">Reguły</span><span class="sxs-lookup"><span data-stu-id="eb1c5-110">Rules</span></span>

- <span data-ttu-id="eb1c5-111">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="eb1c5-111">**Declaration Context.**</span></span> <span data-ttu-id="eb1c5-112">Można używać `Shadows` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="eb1c5-113">Oznacza to, że kontekst deklaracji dla `Shadows` elementu musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, modułem, strukturą ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="eb1c5-114">Można zadeklarować tylko jeden element przesłaniania w jednej instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-114">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="eb1c5-115">**Połączone modyfikatory.**</span><span class="sxs-lookup"><span data-stu-id="eb1c5-115">**Combined Modifiers.**</span></span> <span data-ttu-id="eb1c5-116">Nie można określić `Shadows` razem z `Overloads` , `Overrides` , lub `Static` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="eb1c5-117">**Typy elementów.**</span><span class="sxs-lookup"><span data-stu-id="eb1c5-117">**Element Types.**</span></span> <span data-ttu-id="eb1c5-118">Można obsłużyć dowolny rodzaj zadeklarowanego elementu z dowolnego innego rodzaju.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="eb1c5-119">Jeśli właściwość lub procedura została przesłonięta przez inną właściwość lub procedurę, parametry i zwracany typ nie muszą pasować do tych w właściwości lub procedurze klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="eb1c5-120">**Korzystając.**</span><span class="sxs-lookup"><span data-stu-id="eb1c5-120">**Accessing.**</span></span> <span data-ttu-id="eb1c5-121">Element shadowd w klasie bazowej jest zwykle niedostępny z poziomu klasy pochodnej, która go zasłania.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="eb1c5-122">Jednak obowiązują następujące zagadnienia.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-122">However, the following considerations apply.</span></span>

  - <span data-ttu-id="eb1c5-123">Jeśli element przesłaniania nie jest dostępny z kodu odwołującego się do niego, odwołanie jest rozpoznawane jako element w tle.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="eb1c5-124">Na przykład, jeśli `Private` element zasłania element klasy bazowej, kod, który nie ma uprawnień dostępu do `Private` elementu uzyskuje dostęp do elementu klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="eb1c5-125">W przypadku obserwowania elementu można nadal uzyskać dostęp do elementu w tle za pomocą obiektu zadeklarowanego z typem klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="eb1c5-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="eb1c5-126">Możesz również uzyskać do niego dostęp za poorednictwem `MyBase` .</span><span class="sxs-lookup"><span data-stu-id="eb1c5-126">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="eb1c5-127">`Shadows`Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="eb1c5-127">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="eb1c5-128">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="eb1c5-128">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="eb1c5-129">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="eb1c5-129">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="eb1c5-130">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="eb1c5-130">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="eb1c5-131">Delegate — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="eb1c5-131">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="eb1c5-132">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="eb1c5-132">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="eb1c5-133">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="eb1c5-133">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="eb1c5-134">Event — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="eb1c5-134">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="eb1c5-135">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="eb1c5-135">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="eb1c5-136">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="eb1c5-136">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="eb1c5-137">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="eb1c5-137">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="eb1c5-138">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="eb1c5-138">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="eb1c5-139">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="eb1c5-139">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="eb1c5-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb1c5-140">See also</span></span>

- [<span data-ttu-id="eb1c5-141">Shared</span><span class="sxs-lookup"><span data-stu-id="eb1c5-141">Shared</span></span>](shared.md)
- [<span data-ttu-id="eb1c5-142">Ruchom</span><span class="sxs-lookup"><span data-stu-id="eb1c5-142">Static</span></span>](static.md)
- [<span data-ttu-id="eb1c5-143">Użytek</span><span class="sxs-lookup"><span data-stu-id="eb1c5-143">Private</span></span>](private.md)
- [<span data-ttu-id="eb1c5-144">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="eb1c5-144">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="eb1c5-145">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="eb1c5-145">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="eb1c5-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="eb1c5-146">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="eb1c5-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="eb1c5-147">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="eb1c5-148">Przeciążenia</span><span class="sxs-lookup"><span data-stu-id="eb1c5-148">Overloads</span></span>](overloads.md)
- [<span data-ttu-id="eb1c5-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="eb1c5-149">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="eb1c5-150">Przesłonięcia</span><span class="sxs-lookup"><span data-stu-id="eb1c5-150">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="eb1c5-151">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb1c5-151">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
