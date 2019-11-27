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
ms.openlocfilehash: e9a423fa69ad1dcd8c1d4a5b7085e5b5da548f93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351263"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="86b8b-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86b8b-102">Shadows (Visual Basic)</span></span>

<span data-ttu-id="86b8b-103">Określa, że zadeklarowany element programistyczny ponownie deklaruje i ukrywa element o identycznej nazwie, lub zestaw przeciążonych elementów w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="86b8b-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="86b8b-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86b8b-104">Remarks</span></span>

<span data-ttu-id="86b8b-105">Głównym celem przesłaniania (który jest również znany jako *ukrywanie według nazwy*) jest zachowanie definicji elementów członkowskich klasy.</span><span class="sxs-lookup"><span data-stu-id="86b8b-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="86b8b-106">Klasa bazowa może ulec zmianie, która tworzy element o takiej samej nazwie jak już zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="86b8b-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="86b8b-107">Jeśli tak się stanie, modyfikator `Shadows` wymusza odwołania za pomocą klasy, aby można go było rozpoznać do zdefiniowanego elementu członkowskiego, a nie do nowego elementu klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="86b8b-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="86b8b-108">Zarówno przesłanianie, jak i przesłonięcie przedefiniują Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami.</span><span class="sxs-lookup"><span data-stu-id="86b8b-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="86b8b-109">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="86b8b-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="86b8b-110">Reguły</span><span class="sxs-lookup"><span data-stu-id="86b8b-110">Rules</span></span>

- <span data-ttu-id="86b8b-111">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="86b8b-111">**Declaration Context.**</span></span> <span data-ttu-id="86b8b-112">`Shadows` można użyć tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="86b8b-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="86b8b-113">Oznacza to, że kontekst deklaracji dla elementu `Shadows` musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, strukturą ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="86b8b-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="86b8b-114">Można zadeklarować tylko jeden element przesłaniania w jednej instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="86b8b-114">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="86b8b-115">**Połączone modyfikatory.**</span><span class="sxs-lookup"><span data-stu-id="86b8b-115">**Combined Modifiers.**</span></span> <span data-ttu-id="86b8b-116">Nie można określić `Shadows` razem z `Overloads`, `Overrides`lub `Static` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="86b8b-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="86b8b-117">**Typy elementów.**</span><span class="sxs-lookup"><span data-stu-id="86b8b-117">**Element Types.**</span></span> <span data-ttu-id="86b8b-118">Można obsłużyć dowolny rodzaj zadeklarowanego elementu z dowolnego innego rodzaju.</span><span class="sxs-lookup"><span data-stu-id="86b8b-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="86b8b-119">Jeśli właściwość lub procedura została przesłonięta przez inną właściwość lub procedurę, parametry i zwracany typ nie muszą pasować do tych w właściwości lub procedurze klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="86b8b-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="86b8b-120">**Korzystając.**</span><span class="sxs-lookup"><span data-stu-id="86b8b-120">**Accessing.**</span></span> <span data-ttu-id="86b8b-121">Element shadowd w klasie bazowej jest zwykle niedostępny z poziomu klasy pochodnej, która go zasłania.</span><span class="sxs-lookup"><span data-stu-id="86b8b-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="86b8b-122">Jednak obowiązują następujące zagadnienia.</span><span class="sxs-lookup"><span data-stu-id="86b8b-122">However, the following considerations apply.</span></span>

  - <span data-ttu-id="86b8b-123">Jeśli element przesłaniania nie jest dostępny z kodu odwołującego się do niego, odwołanie jest rozpoznawane jako element w tle.</span><span class="sxs-lookup"><span data-stu-id="86b8b-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="86b8b-124">Na przykład, jeśli element `Private` zasłania element klasy bazowej, kod, który nie ma uprawnień dostępu do elementu `Private`, zamiast tego uzyskuje dostęp do elementu klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="86b8b-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="86b8b-125">W przypadku obserwowania elementu można nadal uzyskać dostęp do elementu w tle za pomocą obiektu zadeklarowanego z typem klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="86b8b-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="86b8b-126">Możesz również uzyskać do niego dostęp za poorednictwem `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="86b8b-126">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="86b8b-127">Modyfikator `Shadows` może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="86b8b-127">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="86b8b-128">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="86b8b-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

- [<span data-ttu-id="86b8b-129">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="86b8b-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="86b8b-130">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="86b8b-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- [<span data-ttu-id="86b8b-131">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="86b8b-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [<span data-ttu-id="86b8b-132">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="86b8b-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- [<span data-ttu-id="86b8b-133">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="86b8b-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)

- [<span data-ttu-id="86b8b-134">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="86b8b-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="86b8b-135">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="86b8b-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="86b8b-136">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="86b8b-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)

- [<span data-ttu-id="86b8b-137">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="86b8b-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="86b8b-138">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="86b8b-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

- [<span data-ttu-id="86b8b-139">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="86b8b-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="86b8b-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86b8b-140">See also</span></span>

- [<span data-ttu-id="86b8b-141">Shared</span><span class="sxs-lookup"><span data-stu-id="86b8b-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="86b8b-142">Static</span><span class="sxs-lookup"><span data-stu-id="86b8b-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="86b8b-143">Private</span><span class="sxs-lookup"><span data-stu-id="86b8b-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="86b8b-144">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="86b8b-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="86b8b-145">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="86b8b-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="86b8b-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="86b8b-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="86b8b-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="86b8b-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="86b8b-148">Overloads</span><span class="sxs-lookup"><span data-stu-id="86b8b-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="86b8b-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="86b8b-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="86b8b-150">Overrides</span><span class="sxs-lookup"><span data-stu-id="86b8b-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="86b8b-151">Obserwowanie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86b8b-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
