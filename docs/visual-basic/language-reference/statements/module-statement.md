---
title: Module — instrukcja (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 73d4a5cc8fd4bad41ead1fda830504b19877a8d8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625470"
---
# <a name="module-statement"></a><span data-ttu-id="0171e-102">Module — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="0171e-102">Module Statement</span></span>
<span data-ttu-id="0171e-103">Deklaruje nazwę modułu i wprowadza definicje zmiennych, właściwości, zdarzeń i procedur, z których składa się moduł.</span><span class="sxs-lookup"><span data-stu-id="0171e-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0171e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0171e-104">Syntax</span></span>  
  
```vb 
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a><span data-ttu-id="0171e-105">Części</span><span class="sxs-lookup"><span data-stu-id="0171e-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="0171e-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0171e-106">Optional.</span></span> <span data-ttu-id="0171e-107">Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="0171e-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="0171e-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0171e-108">Optional.</span></span> <span data-ttu-id="0171e-109">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="0171e-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="0171e-110">Public</span><span class="sxs-lookup"><span data-stu-id="0171e-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
- [<span data-ttu-id="0171e-111">Friend</span><span class="sxs-lookup"><span data-stu-id="0171e-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 <span data-ttu-id="0171e-112">Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0171e-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `name`  
 <span data-ttu-id="0171e-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="0171e-113">Required.</span></span> <span data-ttu-id="0171e-114">Nazwa tego modułu.</span><span class="sxs-lookup"><span data-stu-id="0171e-114">Name of this module.</span></span> <span data-ttu-id="0171e-115">Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="0171e-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `statements`  
 <span data-ttu-id="0171e-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0171e-116">Optional.</span></span> <span data-ttu-id="0171e-117">Instrukcje, które definiują zmienne, właściwości, zdarzenia, procedury i zagnieżdżone typy tego modułu.</span><span class="sxs-lookup"><span data-stu-id="0171e-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>  
  
 `End Module`  
 <span data-ttu-id="0171e-118">Kończy definicję `Module`.</span><span class="sxs-lookup"><span data-stu-id="0171e-118">Terminates the `Module` definition.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0171e-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0171e-119">Remarks</span></span>  
 <span data-ttu-id="0171e-120">Instrukcja `Module` definiuje typ referencyjny dostępny w całej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0171e-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="0171e-121">*Moduł* (nazywany również *modułem standardowym*) przypomina klasę, ale z pewnymi istotnymi różnicami.</span><span class="sxs-lookup"><span data-stu-id="0171e-121">A *module* (sometimes called a *standard module*)is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="0171e-122">Każdy moduł ma dokładnie jedno wystąpienie i nie trzeba go tworzyć ani przypisywać do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0171e-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="0171e-123">Moduły nie obsługują dziedziczenia ani implementacji interfejsów.</span><span class="sxs-lookup"><span data-stu-id="0171e-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="0171e-124">Ponadto moduł nie jest *typem* w takim sensie jak klasy czy struktury — nie można zadeklarować elementu programistycznego, którego typem danych będzie moduł.</span><span class="sxs-lookup"><span data-stu-id="0171e-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>  
  
 <span data-ttu-id="0171e-125">Instrukcji `Module` można użyć tylko na poziomie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0171e-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="0171e-126">Oznacza to, że *kontekst deklaracji* modułu musi być plikiem źródłowym lub przestrzenią nazw. Nie może być klasą, strukturą, modułem, interfejsem, procedurą ani blokiem.</span><span class="sxs-lookup"><span data-stu-id="0171e-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="0171e-127">Nie można zagnieździć modułu w innym module ani żadnym typie.</span><span class="sxs-lookup"><span data-stu-id="0171e-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="0171e-128">Aby uzyskać więcej informacji, zobacz temat [Konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0171e-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="0171e-129">Moduł ma ten sam okres istnienia co program.</span><span class="sxs-lookup"><span data-stu-id="0171e-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="0171e-130">Ponieważ wszystkie jego elementy członkowskie są typu `Shared`, one także mają okresy istnienia takie same jak program.</span><span class="sxs-lookup"><span data-stu-id="0171e-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>  
  
 <span data-ttu-id="0171e-131">Domyślnym typem dostępu modułów jest [Friend](../../../visual-basic/language-reference/modifiers/friend.md).</span><span class="sxs-lookup"><span data-stu-id="0171e-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="0171e-132">Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="0171e-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="0171e-133">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0171e-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="0171e-134">Wszystkie elementy członkowskie modułu są niejawną kolekcją `Shared`.</span><span class="sxs-lookup"><span data-stu-id="0171e-134">All members of a module are implicitly `Shared`.</span></span>  
  
## <a name="classes-and-modules"></a><span data-ttu-id="0171e-135">Klasy i moduły</span><span class="sxs-lookup"><span data-stu-id="0171e-135">Classes and Modules</span></span>  
 <span data-ttu-id="0171e-136">Te elementy mają wiele wspólnego, ale istnieją pewne ważne różnice.</span><span class="sxs-lookup"><span data-stu-id="0171e-136">These elements have many similarities, but there are some important differences as well.</span></span>  
  
- <span data-ttu-id="0171e-137">**Terminologia.**</span><span class="sxs-lookup"><span data-stu-id="0171e-137">**Terminology.**</span></span> <span data-ttu-id="0171e-138">Poprzednie wersje języka Visual Basic rozpoznawały dwa typy modułów: *moduły klas* (pliki .cls) i *moduły standardowe* (pliki .bas).</span><span class="sxs-lookup"><span data-stu-id="0171e-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="0171e-139">W bieżącej wersji są one nazywane odpowiednio *klasami* i *modułami*.</span><span class="sxs-lookup"><span data-stu-id="0171e-139">The current version calls these *classes* and *modules*, respectively.</span></span>  
  
- <span data-ttu-id="0171e-140">**Udostępnione elementy członkowskie.**</span><span class="sxs-lookup"><span data-stu-id="0171e-140">**Shared Members.**</span></span> <span data-ttu-id="0171e-141">Można określić, czy udostępniany jest element członkowski klasy czy wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0171e-141">You can control whether a member of a class is a shared or instance member.</span></span>  
  
- <span data-ttu-id="0171e-142">**Orientacja obiektowa.**</span><span class="sxs-lookup"><span data-stu-id="0171e-142">**Object Orientation.**</span></span> <span data-ttu-id="0171e-143">Klasy są zorientowane obiektowo, a moduły nie.</span><span class="sxs-lookup"><span data-stu-id="0171e-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="0171e-144">Dlatego jako obiekty można tworzyć tylko wystąpienia klas.</span><span class="sxs-lookup"><span data-stu-id="0171e-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="0171e-145">Aby uzyskać więcej informacji, zobacz temat [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="0171e-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="0171e-146">reguły</span><span class="sxs-lookup"><span data-stu-id="0171e-146">Rules</span></span>  
  
- <span data-ttu-id="0171e-147">**Modyfikatory.**</span><span class="sxs-lookup"><span data-stu-id="0171e-147">**Modifiers.**</span></span> <span data-ttu-id="0171e-148">Wszystkie elementy członkowskie modułu mają niejawnie przypisany modyfikator [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="0171e-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="0171e-149">Nie można użyć słowa kluczowego `Shared` podczas deklarowania elementu członkowskiego. Nie można także zmienić stanu udostępnienia żadnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0171e-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>  
  
- <span data-ttu-id="0171e-150">**Dziedziczenie.**</span><span class="sxs-lookup"><span data-stu-id="0171e-150">**Inheritance.**</span></span> <span data-ttu-id="0171e-151">Moduł nie może dziedziczyć z dowolnego typu innego niż <xref:System.Object>, z których wszystkie moduły dziedziczyć.</span><span class="sxs-lookup"><span data-stu-id="0171e-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="0171e-152">W szczególności jeden moduł nie może dziedziczyć z innej.</span><span class="sxs-lookup"><span data-stu-id="0171e-152">In particular, one module cannot inherit from another.</span></span>  
  
     <span data-ttu-id="0171e-153">Nie można użyć [dziedziczy instrukcję](../../../visual-basic/language-reference/statements/inherits-statement.md) w definicji modułu, nawet do określenia <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="0171e-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="0171e-154">**Właściwość domyślna.**</span><span class="sxs-lookup"><span data-stu-id="0171e-154">**Default Property.**</span></span> <span data-ttu-id="0171e-155">Nie można zdefiniować żadnych właściwości domyślne w module.</span><span class="sxs-lookup"><span data-stu-id="0171e-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="0171e-156">Aby uzyskać więcej informacji, zobacz temat [Default](../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="0171e-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="0171e-157">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="0171e-157">Behavior</span></span>  
  
- <span data-ttu-id="0171e-158">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="0171e-158">**Access Level.**</span></span> <span data-ttu-id="0171e-159">W ramach modułu można zadeklarować każdego członka z poziomu dostępu.</span><span class="sxs-lookup"><span data-stu-id="0171e-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="0171e-160">Domyślnie członkowie modułu [publicznych](../../../visual-basic/language-reference/modifiers/public.md) dostęp, z wyjątkiem sytuacji zmiennych i stałych, które domyślnie [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) dostępu.</span><span class="sxs-lookup"><span data-stu-id="0171e-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="0171e-161">Gdy moduł ograniczył dostęp więcej niż jeden z jej członków, pierwszeństwo ma poziom dostępu określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="0171e-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>  
  
- <span data-ttu-id="0171e-162">**Zakres.**</span><span class="sxs-lookup"><span data-stu-id="0171e-162">**Scope.**</span></span> <span data-ttu-id="0171e-163">Moduł jest w zakresie jego przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="0171e-163">A module is in scope throughout its namespace.</span></span>  
  
     <span data-ttu-id="0171e-164">Zakres każdego członka modułu jest cały moduł.</span><span class="sxs-lookup"><span data-stu-id="0171e-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="0171e-165">Należy zauważyć, że wszystkie elementy członkowskie poddawane *wpisz podwyższania poziomu*, co powoduje, że ich zakres ma zostać podniesiony do przestrzeni nazw, zawierającej moduł.</span><span class="sxs-lookup"><span data-stu-id="0171e-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="0171e-166">Aby uzyskać więcej informacji, zobacz [promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="0171e-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
- <span data-ttu-id="0171e-167">**Kwalifikacja.**</span><span class="sxs-lookup"><span data-stu-id="0171e-167">**Qualification.**</span></span> <span data-ttu-id="0171e-168">Może mieć wiele modułów w projekcie i można zadeklarować składowych o tej samej nazwie w co najmniej dwa moduły.</span><span class="sxs-lookup"><span data-stu-id="0171e-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="0171e-169">Jednak jeśli odwołanie jest z poza ten moduł musi kwalifikować się wszelkie odwołania do składowej o nazwie odpowiedniego modułu.</span><span class="sxs-lookup"><span data-stu-id="0171e-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="0171e-170">Aby uzyskać więcej informacji, zobacz [Odwołania do zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="0171e-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0171e-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="0171e-171">Example</span></span>  
 [!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]  
  
## <a name="see-also"></a><span data-ttu-id="0171e-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0171e-172">See also</span></span>

- [<span data-ttu-id="0171e-173">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0171e-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="0171e-174">Namespace, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0171e-174">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="0171e-175">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0171e-175">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="0171e-176">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="0171e-176">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="0171e-177">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="0171e-177">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="0171e-178">Promocja typu</span><span class="sxs-lookup"><span data-stu-id="0171e-178">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
