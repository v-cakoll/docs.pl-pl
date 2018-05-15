---
title: Shadows (Visual Basic)
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
ms.openlocfilehash: 4ca4ec48ee63b71447056a2c5cb68e8948f27ad0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="cc2ac-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc2ac-102">Shadows (Visual Basic)</span></span>
<span data-ttu-id="cc2ac-103">Określa, że zadeklarowany element programistyczny ponownie deklaruje i ukrywa element o identycznej nazwie lub zbiór elementów przeciążona w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc2ac-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc2ac-104">Remarks</span></span>  
 <span data-ttu-id="cc2ac-105">Głównym celem przesłanianie (który jest również nazywany *ukrywanie według nazwy*) jest zachowanie definicji członkowie klasy.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="cc2ac-106">Klasa podstawowa mogą być zmiany, która tworzy element o takiej samej nazwie jako jeden, który został już zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="cc2ac-107">W takim przypadku `Shadows` wymusza modyfikator odwołuje się do klasy mają zostać rozwiązane do elementu członkowskiego zdefiniowane, a nie nowy element klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
 <span data-ttu-id="cc2ac-108">Zarówno przesłanianiem i zastępowaniem ponownego zdefiniowania odziedziczonego elementu, ale są istotne różnice między dwa podejścia.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="cc2ac-109">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="cc2ac-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="cc2ac-110">Reguły</span><span class="sxs-lookup"><span data-stu-id="cc2ac-110">Rules</span></span>  
  
-   <span data-ttu-id="cc2ac-111">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="cc2ac-111">**Declaration Context.**</span></span> <span data-ttu-id="cc2ac-112">Można użyć `Shadows` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="cc2ac-113">Oznacza to, że w kontekście deklaracji `Shadows` elementu musi być klasą i nie może być plik źródłowy, przestrzeni nazw, interfejsu, modułu, struktury lub procedury.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
     <span data-ttu-id="cc2ac-114">Można zadeklarować tylko jeden element przesłaniania w instrukcji jednej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-114">You can declare only one shadowing element in a single declaration statement.</span></span>  
  
-   <span data-ttu-id="cc2ac-115">**Łączna modyfikatorów.**</span><span class="sxs-lookup"><span data-stu-id="cc2ac-115">**Combined Modifiers.**</span></span> <span data-ttu-id="cc2ac-116">Nie można określić `Shadows` razem z `Overloads`, `Overrides`, lub `Static` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="cc2ac-117">**Typy elementów.**</span><span class="sxs-lookup"><span data-stu-id="cc2ac-117">**Element Types.**</span></span> <span data-ttu-id="cc2ac-118">Można obserwować dowolny rodzaj elementu zadeklarowany z innego typu.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="cc2ac-119">Jeśli cień właściwość lub procedura z inną właściwość lub procedura parametry oraz zwracany typ nie musi odpowiadać w klasie podstawowej właściwość lub procedura.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>  
  
-   <span data-ttu-id="cc2ac-120">**Uzyskiwanie dostępu do.**</span><span class="sxs-lookup"><span data-stu-id="cc2ac-120">**Accessing.**</span></span> <span data-ttu-id="cc2ac-121">Element zasłonięty w klasie podstawowej zwykle z są niedostępne w klasie pochodnej, któremu go.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="cc2ac-122">Jednak uwzględnić następujące kwestie.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-122">However, the following considerations apply.</span></span>  
  
    -   <span data-ttu-id="cc2ac-123">Jeśli element przesłaniania nie jest dostępny z kod odwołujący się do niego, odwołanie jest rozwiązany do elementu zasłonięty.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="cc2ac-124">Na przykład jeśli `Private` element zasłania element klasy podstawowej, kod, który nie ma uprawnień dostępu do `Private` element uzyskuje dostęp do elementu klasy podstawowej zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>  
  
    -   <span data-ttu-id="cc2ac-125">Jeśli w tle elementu można nadal dostęp do elementu zasłonięty, za pomocą obiektu zadeklarowane z typem klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="cc2ac-126">Możesz również do niego dostęp za pośrednictwem `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="cc2ac-126">You can also access it through `MyBase`.</span></span>  
  
 <span data-ttu-id="cc2ac-127">`Shadows` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="cc2ac-127">The `Shadows` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="cc2ac-128">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc2ac-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="cc2ac-129">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc2ac-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="cc2ac-130">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc2ac-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="cc2ac-131">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc2ac-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="cc2ac-132">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc2ac-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="cc2ac-133">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc2ac-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="cc2ac-134">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc2ac-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="cc2ac-135">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc2ac-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="cc2ac-136">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc2ac-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="cc2ac-137">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc2ac-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="cc2ac-138">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc2ac-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="cc2ac-139">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cc2ac-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cc2ac-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc2ac-140">See Also</span></span>  
 [<span data-ttu-id="cc2ac-141">Shared</span><span class="sxs-lookup"><span data-stu-id="cc2ac-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="cc2ac-142">Static</span><span class="sxs-lookup"><span data-stu-id="cc2ac-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="cc2ac-143">Private</span><span class="sxs-lookup"><span data-stu-id="cc2ac-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="cc2ac-144">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="cc2ac-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="cc2ac-145">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="cc2ac-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="cc2ac-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="cc2ac-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="cc2ac-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="cc2ac-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="cc2ac-148">Overloads</span><span class="sxs-lookup"><span data-stu-id="cc2ac-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="cc2ac-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="cc2ac-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="cc2ac-150">Overrides</span><span class="sxs-lookup"><span data-stu-id="cc2ac-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="cc2ac-151">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc2ac-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
