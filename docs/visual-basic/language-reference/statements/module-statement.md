---
title: "Module — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 92cdcd1919f21243118108da3bc382ea5d954130
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="module-statement"></a><span data-ttu-id="69d79-102">Module — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="69d79-102">Module Statement</span></span>
<span data-ttu-id="69d79-103">Deklaruje nazwę modułu i wprowadza definicje zmiennych, właściwości, zdarzeń i procedur, które składa się z modułu.</span><span class="sxs-lookup"><span data-stu-id="69d79-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69d79-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69d79-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a><span data-ttu-id="69d79-105">Części</span><span class="sxs-lookup"><span data-stu-id="69d79-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="69d79-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="69d79-106">Optional.</span></span> <span data-ttu-id="69d79-107">Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="69d79-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="69d79-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="69d79-108">Optional.</span></span> <span data-ttu-id="69d79-109">Może to być jedna z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="69d79-109">Can be one of the following:</span></span>  
  
-   [<span data-ttu-id="69d79-110">Publiczna</span><span class="sxs-lookup"><span data-stu-id="69d79-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [<span data-ttu-id="69d79-111">Friend</span><span class="sxs-lookup"><span data-stu-id="69d79-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 <span data-ttu-id="69d79-112">Zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="69d79-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `name`  
 <span data-ttu-id="69d79-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="69d79-113">Required.</span></span> <span data-ttu-id="69d79-114">Nazwa tego modułu.</span><span class="sxs-lookup"><span data-stu-id="69d79-114">Name of this module.</span></span> <span data-ttu-id="69d79-115">Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="69d79-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `statements`  
 <span data-ttu-id="69d79-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="69d79-116">Optional.</span></span> <span data-ttu-id="69d79-117">Instrukcje, które definiują zmiennych, właściwości, zdarzenia, procedury i zagnieżdżone typy tego modułu.</span><span class="sxs-lookup"><span data-stu-id="69d79-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>  
  
 `End Module`  
 <span data-ttu-id="69d79-118">Kończy `Module` definicji.</span><span class="sxs-lookup"><span data-stu-id="69d79-118">Terminates the `Module` definition.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69d79-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69d79-119">Remarks</span></span>  
 <span data-ttu-id="69d79-120">A `Module` instrukcji definiuje typ referencyjny w całym ich nazw.</span><span class="sxs-lookup"><span data-stu-id="69d79-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="69d79-121">A *modułu* (nazywane również *standardowy moduł*) jest podobny do klasy, ale niektóre istotne różnice.</span><span class="sxs-lookup"><span data-stu-id="69d79-121">A *module* (sometimes called a *standard module*)is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="69d79-122">Każdy moduł ma dokładnie jedno wystąpienie i nie trzeba można utworzyć ani przypisany do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="69d79-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="69d79-123">Moduły nie obsługuje dziedziczenia lub implementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="69d79-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="69d79-124">Należy zauważyć, że nie jest modułem *typu* w tym sensie, że klasy lub struktury — nie można zadeklarować elementu programistycznego typu danych modułu.</span><span class="sxs-lookup"><span data-stu-id="69d79-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>  
  
 <span data-ttu-id="69d79-125">Można użyć `Module` tylko na poziomie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="69d79-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="69d79-126">Oznacza to, że *kontekście deklaracji* modułu musi być pliku źródłowego lub obszaru nazw i nie może być klasy, struktury, modułu, interfejsu, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="69d79-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="69d79-127">Nie można zagnieździć w innym module lub do dowolnego typu modułu.</span><span class="sxs-lookup"><span data-stu-id="69d79-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="69d79-128">Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="69d79-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="69d79-129">Moduł ma tego samego czas istnienia jako program.</span><span class="sxs-lookup"><span data-stu-id="69d79-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="69d79-130">Ponieważ wszystkie jej elementów członkowskich `Shared`, ma także okresy istnienia równa program.</span><span class="sxs-lookup"><span data-stu-id="69d79-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>  
  
 <span data-ttu-id="69d79-131">Domyślnie moduły [Friend](../../../visual-basic/language-reference/modifiers/friend.md) dostępu.</span><span class="sxs-lookup"><span data-stu-id="69d79-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="69d79-132">Można dostosować ich poziomy dostępu z modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="69d79-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="69d79-133">Aby uzyskać więcej informacji, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="69d79-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="69d79-134">Wszystkie elementy członkowskie modułu są niejawnie `Shared`.</span><span class="sxs-lookup"><span data-stu-id="69d79-134">All members of a module are implicitly `Shared`.</span></span>  
  
## <a name="classes-and-modules"></a><span data-ttu-id="69d79-135">Klasy i moduły</span><span class="sxs-lookup"><span data-stu-id="69d79-135">Classes and Modules</span></span>  
 <span data-ttu-id="69d79-136">Te elementy mają wiele podobieństw, ale istnieje kilka istotnych różnic.</span><span class="sxs-lookup"><span data-stu-id="69d79-136">These elements have many similarities, but there are some important differences as well.</span></span>  
  
-   <span data-ttu-id="69d79-137">**Terminologia z zakresu.**</span><span class="sxs-lookup"><span data-stu-id="69d79-137">**Terminology.**</span></span> <span data-ttu-id="69d79-138">Poprzednie wersje programu Visual Basic rozpoznaje dwa typy modułów: *klasy modułów* (pliki .cls) i *standardowe moduły* (pliki .bas).</span><span class="sxs-lookup"><span data-stu-id="69d79-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="69d79-139">Bieżąca wersja wywołuje te *klasy* i *modułów*odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="69d79-139">The current version calls these *classes* and *modules*, respectively.</span></span>  
  
-   <span data-ttu-id="69d79-140">**Udostępniane elementy członkowskie.**</span><span class="sxs-lookup"><span data-stu-id="69d79-140">**Shared Members.**</span></span> <span data-ttu-id="69d79-141">Można kontrolować, czy udostępniony jest element członkowski klasy lub wystąpienia elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="69d79-141">You can control whether a member of a class is a shared or instance member.</span></span>  
  
-   <span data-ttu-id="69d79-142">**Orientacja obiektu.**</span><span class="sxs-lookup"><span data-stu-id="69d79-142">**Object Orientation.**</span></span> <span data-ttu-id="69d79-143">Klasy są zorientowane obiektowo, ale nie są moduły.</span><span class="sxs-lookup"><span data-stu-id="69d79-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="69d79-144">Tak jak obiekty można wdrożyć tylko klasy.</span><span class="sxs-lookup"><span data-stu-id="69d79-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="69d79-145">Aby uzyskać więcej informacji, zobacz [obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="69d79-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="69d79-146">Reguły</span><span class="sxs-lookup"><span data-stu-id="69d79-146">Rules</span></span>  
  
-   <span data-ttu-id="69d79-147">**Modyfikatorów.**</span><span class="sxs-lookup"><span data-stu-id="69d79-147">**Modifiers.**</span></span> <span data-ttu-id="69d79-148">Wszyscy członkowie modułu są niejawnie [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="69d79-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="69d79-149">Nie można użyć `Shared` — słowo kluczowe podczas deklarowania elementem członkowskim i nie można zmienić udostępniony stan dowolnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="69d79-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>  
  
-   <span data-ttu-id="69d79-150">**Dziedziczenie.**</span><span class="sxs-lookup"><span data-stu-id="69d79-150">**Inheritance.**</span></span> <span data-ttu-id="69d79-151">Moduł nie może dziedziczyć z dowolnego typu innego niż <xref:System.Object>, z których wszystkie moduły dziedziczyć.</span><span class="sxs-lookup"><span data-stu-id="69d79-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="69d79-152">W szczególności jeden moduł nie może dziedziczyć z innego.</span><span class="sxs-lookup"><span data-stu-id="69d79-152">In particular, one module cannot inherit from another.</span></span>  
  
     <span data-ttu-id="69d79-153">Nie można użyć [dziedziczy instrukcję](../../../visual-basic/language-reference/statements/inherits-statement.md) w definicji modułu, nawet do określenia <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="69d79-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>  
  
-   <span data-ttu-id="69d79-154">**Domyślna właściwość.**</span><span class="sxs-lookup"><span data-stu-id="69d79-154">**Default Property.**</span></span> <span data-ttu-id="69d79-155">Nie można zdefiniować żadnych właściwości domyślne w module.</span><span class="sxs-lookup"><span data-stu-id="69d79-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="69d79-156">Aby uzyskać więcej informacji, zobacz [domyślne](../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="69d79-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="69d79-157">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="69d79-157">Behavior</span></span>  
  
-   <span data-ttu-id="69d79-158">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="69d79-158">**Access Level.**</span></span> <span data-ttu-id="69d79-159">W module mogą zadeklarować każdy element członkowski z poziomu dostępu.</span><span class="sxs-lookup"><span data-stu-id="69d79-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="69d79-160">Domyślnie moduł członków [publicznego](../../../visual-basic/language-reference/modifiers/public.md) uzyskać dostęp, z wyjątkiem zmienne i stałe, które domyślnie [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) dostępu.</span><span class="sxs-lookup"><span data-stu-id="69d79-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="69d79-161">Gdy moduł ograniczył dostęp więcej niż jeden z jego elementów członkowskich, pierwszeństwo ma poziom dostępu do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="69d79-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>  
  
-   <span data-ttu-id="69d79-162">**Zakres.**</span><span class="sxs-lookup"><span data-stu-id="69d79-162">**Scope.**</span></span> <span data-ttu-id="69d79-163">Moduł jest w zakresie w całym ich nazw.</span><span class="sxs-lookup"><span data-stu-id="69d79-163">A module is in scope throughout its namespace.</span></span>  
  
     <span data-ttu-id="69d79-164">Zakres każdego elementu modułu jest cały moduł.</span><span class="sxs-lookup"><span data-stu-id="69d79-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="69d79-165">Należy zauważyć, że wszystkie elementy członkowskie przejście *wpisz podwyższania poziomu*, co powoduje, że ich zakres się dopiero przestrzeni nazw zawierającej modułu.</span><span class="sxs-lookup"><span data-stu-id="69d79-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="69d79-166">Aby uzyskać więcej informacji, zobacz [promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="69d79-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
-   <span data-ttu-id="69d79-167">**Kwalifikacji.**</span><span class="sxs-lookup"><span data-stu-id="69d79-167">**Qualification.**</span></span> <span data-ttu-id="69d79-168">Może mieć wiele modułów w projekcie i można zadeklarować elementów członkowskich o tej samej nazwie w co najmniej dwa moduły.</span><span class="sxs-lookup"><span data-stu-id="69d79-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="69d79-169">Jednak jeśli odwołanie jest z poza ten moduł muszą kwalifikować się wszystkich odwołań do takiego elementu członkowskiego o nazwie odpowiedniego modułu.</span><span class="sxs-lookup"><span data-stu-id="69d79-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="69d79-170">Aby uzyskać więcej informacji, zobacz [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="69d79-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69d79-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="69d79-171">Example</span></span>  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="69d79-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69d79-172">See Also</span></span>  
 [<span data-ttu-id="69d79-173">Class — instrukcja</span><span class="sxs-lookup"><span data-stu-id="69d79-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="69d79-174">Namespace — instrukcja</span><span class="sxs-lookup"><span data-stu-id="69d79-174">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="69d79-175">Structure — instrukcja</span><span class="sxs-lookup"><span data-stu-id="69d79-175">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="69d79-176">Interface — instrukcja</span><span class="sxs-lookup"><span data-stu-id="69d79-176">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="69d79-177">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="69d79-177">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="69d79-178">Promocja typu</span><span class="sxs-lookup"><span data-stu-id="69d79-178">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
