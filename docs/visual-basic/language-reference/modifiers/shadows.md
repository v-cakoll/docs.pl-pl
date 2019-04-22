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
ms.openlocfilehash: c314db90a1a0f89613e20897387bdec8ec534837
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834143"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="ee112-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee112-102">Shadows (Visual Basic)</span></span>
<span data-ttu-id="ee112-103">Określa, że zadeklarowany element programistyczny ponownie deklaruje i ukrywa element o identycznej nazwie, lub zestaw przeciążonych elementów w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="ee112-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee112-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee112-104">Remarks</span></span>  
 <span data-ttu-id="ee112-105">Głównym celem cieniowania (który jest również nazywany *ukrycie przez nazwę*) jest zachowanie definicji usługi składowych klasy.</span><span class="sxs-lookup"><span data-stu-id="ee112-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="ee112-106">Klasy bazowej może przechodzić zmianę, która tworzy element o takiej samej nazwie jako jeden, który został już zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="ee112-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="ee112-107">W takim przypadku `Shadows` wymusza modyfikator odwołuje się do swojej klasy, które mają zostać rozwiązane do elementu członkowskiego zdefiniowane, zamiast na nowy element klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="ee112-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
 <span data-ttu-id="ee112-108">Zarówno przesłanianiem i zastępowaniem przedefiniować dziedziczonego elementu, ale istnieją znaczne różnice między dwa podejścia.</span><span class="sxs-lookup"><span data-stu-id="ee112-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="ee112-109">Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="ee112-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ee112-110">reguły</span><span class="sxs-lookup"><span data-stu-id="ee112-110">Rules</span></span>  
  
-   <span data-ttu-id="ee112-111">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="ee112-111">**Declaration Context.**</span></span> <span data-ttu-id="ee112-112">Możesz użyć `Shadows` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="ee112-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="ee112-113">Oznacza to, że kontekst deklaracji `Shadows` element musi być klasą i nie może być plik źródłowy, przestrzeń nazw, interfejsu, moduł, struktura lub procedury.</span><span class="sxs-lookup"><span data-stu-id="ee112-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
     <span data-ttu-id="ee112-114">Można zadeklarować tylko jeden element przesłaniania w instrukcji jednej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="ee112-114">You can declare only one shadowing element in a single declaration statement.</span></span>  
  
-   <span data-ttu-id="ee112-115">**Modyfikatory połączone.**</span><span class="sxs-lookup"><span data-stu-id="ee112-115">**Combined Modifiers.**</span></span> <span data-ttu-id="ee112-116">Nie można określić `Shadows` wraz z `Overloads`, `Overrides`, lub `Static` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="ee112-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="ee112-117">**Typy elementów.**</span><span class="sxs-lookup"><span data-stu-id="ee112-117">**Element Types.**</span></span> <span data-ttu-id="ee112-118">Można w tle dowolnego typu element zadeklarowany za pomocą dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="ee112-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="ee112-119">Jeśli użytkownik w tle, właściwość lub procedura z inną właściwość lub procedura, parametry oraz zwracany typ musi odpowiadać znajdującymi się na właściwości klasy bazowej lub procedury.</span><span class="sxs-lookup"><span data-stu-id="ee112-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>  
  
-   <span data-ttu-id="ee112-120">**Uzyskiwanie dostępu do.**</span><span class="sxs-lookup"><span data-stu-id="ee112-120">**Accessing.**</span></span> <span data-ttu-id="ee112-121">Element zasłonięte w klasie bazowej niedostępności zwykle od w klasie pochodnej, która przesłania go.</span><span class="sxs-lookup"><span data-stu-id="ee112-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="ee112-122">Jednak mają zastosowanie następujące kwestie.</span><span class="sxs-lookup"><span data-stu-id="ee112-122">However, the following considerations apply.</span></span>  
  
    -   <span data-ttu-id="ee112-123">Jeśli element przesłaniania nie jest dostępne z kodu, odwołując się do niego, odwołanie zostaje rozpoznany tekst z cieniem elementu.</span><span class="sxs-lookup"><span data-stu-id="ee112-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="ee112-124">Na przykład jeśli `Private` element zasłania elementu klasy podstawowej, kod, który nie ma uprawnień dostępu do `Private` element uzyskuje dostęp do elementu klasy podstawowej zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="ee112-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>  
  
    -   <span data-ttu-id="ee112-125">Jeśli w tle elementu możesz uzyskiwać dostęp element zasłonięte przez obiekt, który zadeklarowane z typem klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="ee112-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="ee112-126">Możesz również do niego dostęp za pośrednictwem `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="ee112-126">You can also access it through `MyBase`.</span></span>  
  
 <span data-ttu-id="ee112-127">`Shadows` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="ee112-127">The `Shadows` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ee112-128">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ee112-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="ee112-129">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ee112-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="ee112-130">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ee112-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="ee112-131">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ee112-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="ee112-132">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ee112-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="ee112-133">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ee112-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="ee112-134">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ee112-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="ee112-135">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ee112-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="ee112-136">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="ee112-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="ee112-137">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="ee112-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="ee112-138">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ee112-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="ee112-139">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ee112-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ee112-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee112-140">See also</span></span>

- [<span data-ttu-id="ee112-141">Shared</span><span class="sxs-lookup"><span data-stu-id="ee112-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="ee112-142">Static</span><span class="sxs-lookup"><span data-stu-id="ee112-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="ee112-143">Private</span><span class="sxs-lookup"><span data-stu-id="ee112-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="ee112-144">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="ee112-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="ee112-145">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="ee112-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="ee112-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="ee112-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="ee112-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="ee112-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="ee112-148">Overloads</span><span class="sxs-lookup"><span data-stu-id="ee112-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="ee112-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="ee112-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="ee112-150">Overrides</span><span class="sxs-lookup"><span data-stu-id="ee112-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="ee112-151">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee112-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
