---
title: Module — Instrukcja
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
ms.openlocfilehash: 24a27ba41f5ac889f2f2725a2852368a4292a6fb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404461"
---
# <a name="module-statement"></a><span data-ttu-id="66eaf-102">Module — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="66eaf-102">Module Statement</span></span>

<span data-ttu-id="66eaf-103">Deklaruje nazwę modułu i wprowadza definicje zmiennych, właściwości, zdarzeń i procedur, które składają się na moduł.</span><span class="sxs-lookup"><span data-stu-id="66eaf-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>

## <a name="syntax"></a><span data-ttu-id="66eaf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66eaf-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a><span data-ttu-id="66eaf-105">Części</span><span class="sxs-lookup"><span data-stu-id="66eaf-105">Parts</span></span>

`attributelist`  
<span data-ttu-id="66eaf-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="66eaf-106">Optional.</span></span> <span data-ttu-id="66eaf-107">Zobacz [listę atrybutów](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="66eaf-107">See [Attribute List](attribute-list.md).</span></span>

`accessmodifier`  
<span data-ttu-id="66eaf-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="66eaf-108">Optional.</span></span> <span data-ttu-id="66eaf-109">Może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="66eaf-109">Can be one of the following:</span></span>

- [<span data-ttu-id="66eaf-110">Społeczeństwo</span><span class="sxs-lookup"><span data-stu-id="66eaf-110">Public</span></span>](../modifiers/public.md)

- [<span data-ttu-id="66eaf-111">Osoby</span><span class="sxs-lookup"><span data-stu-id="66eaf-111">Friend</span></span>](../modifiers/friend.md)

<span data-ttu-id="66eaf-112">Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="66eaf-112">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

`name`  
<span data-ttu-id="66eaf-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="66eaf-113">Required.</span></span> <span data-ttu-id="66eaf-114">Nazwa tego modułu.</span><span class="sxs-lookup"><span data-stu-id="66eaf-114">Name of this module.</span></span> <span data-ttu-id="66eaf-115">Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="66eaf-115">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

`statements`  
<span data-ttu-id="66eaf-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="66eaf-116">Optional.</span></span> <span data-ttu-id="66eaf-117">Instrukcje, które definiują zmienne, właściwości, zdarzenia, procedury i zagnieżdżone typy tego modułu.</span><span class="sxs-lookup"><span data-stu-id="66eaf-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>

`End Module`  
<span data-ttu-id="66eaf-118">Kończy `Module` definicję.</span><span class="sxs-lookup"><span data-stu-id="66eaf-118">Terminates the `Module` definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="66eaf-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66eaf-119">Remarks</span></span>

<span data-ttu-id="66eaf-120">`Module`Instrukcja definiuje typ referencyjny, który jest dostępny w całej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="66eaf-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="66eaf-121">*Moduł* (czasami nazywany *modułem standardowym*) jest podobny do klasy, ale z istotnymi różnicami.</span><span class="sxs-lookup"><span data-stu-id="66eaf-121">A *module* (sometimes called a *standard module*) is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="66eaf-122">Każdy moduł ma dokładnie jedno wystąpienie i nie musi być utworzony ani przypisany do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="66eaf-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="66eaf-123">Moduły nie obsługują dziedziczenia ani implementowania interfejsów.</span><span class="sxs-lookup"><span data-stu-id="66eaf-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="66eaf-124">Należy zauważyć, że moduł nie jest *typem* w sensie, że Klasa lub struktura to — nie można zadeklarować elementu programistycznego w taki sposób, aby miał typ danych modułu.</span><span class="sxs-lookup"><span data-stu-id="66eaf-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>

<span data-ttu-id="66eaf-125">Można używać `Module` tylko na poziomie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="66eaf-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="66eaf-126">Oznacza to, że *kontekst deklaracji* dla modułu musi być plikiem źródłowym lub przestrzenią nazw i nie może być klasą, strukturą, modułem, interfejsem, procedurą lub blokiem.</span><span class="sxs-lookup"><span data-stu-id="66eaf-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="66eaf-127">Nie można zagnieżdżać modułu w innym module ani w żadnym typie.</span><span class="sxs-lookup"><span data-stu-id="66eaf-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="66eaf-128">Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="66eaf-128">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="66eaf-129">Moduł ma ten sam okres istnienia co program.</span><span class="sxs-lookup"><span data-stu-id="66eaf-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="66eaf-130">Ze względu na to, że jego elementy członkowskie są wszystkie `Shared` , mają także okresy istnienia równe tym programowi.</span><span class="sxs-lookup"><span data-stu-id="66eaf-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>

<span data-ttu-id="66eaf-131">Moduły domyślnie mają dostęp do [znajomych](../modifiers/friend.md) .</span><span class="sxs-lookup"><span data-stu-id="66eaf-131">Modules default to [Friend](../modifiers/friend.md) access.</span></span> <span data-ttu-id="66eaf-132">Możesz dostosować ich poziomy dostępu za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="66eaf-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="66eaf-133">Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="66eaf-133">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="66eaf-134">Wszystkie elementy członkowskie modułu są niejawnie `Shared` .</span><span class="sxs-lookup"><span data-stu-id="66eaf-134">All members of a module are implicitly `Shared`.</span></span>

## <a name="classes-and-modules"></a><span data-ttu-id="66eaf-135">Klasy i moduły</span><span class="sxs-lookup"><span data-stu-id="66eaf-135">Classes and Modules</span></span>

<span data-ttu-id="66eaf-136">Te elementy mają wiele podobieństw, ale istnieją pewne istotne różnice.</span><span class="sxs-lookup"><span data-stu-id="66eaf-136">These elements have many similarities, but there are some important differences as well.</span></span>

- <span data-ttu-id="66eaf-137">**Terminologia.**</span><span class="sxs-lookup"><span data-stu-id="66eaf-137">**Terminology.**</span></span> <span data-ttu-id="66eaf-138">Poprzednie wersje Visual Basic rozpoznają dwa typy modułów: *moduły klasy* (pliki. CLS) i *moduły standardowe* (pliki. bas).</span><span class="sxs-lookup"><span data-stu-id="66eaf-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="66eaf-139">Bieżąca wersja wywołuje odpowiednio te *klasy* i *moduły*.</span><span class="sxs-lookup"><span data-stu-id="66eaf-139">The current version calls these *classes* and *modules*, respectively.</span></span>

- <span data-ttu-id="66eaf-140">**Udostępnione elementy członkowskie.**</span><span class="sxs-lookup"><span data-stu-id="66eaf-140">**Shared Members.**</span></span> <span data-ttu-id="66eaf-141">Można kontrolować, czy element członkowski klasy jest członkiem współdzielonym, czy wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="66eaf-141">You can control whether a member of a class is a shared or instance member.</span></span>

- <span data-ttu-id="66eaf-142">**Orientacja obiektu.**</span><span class="sxs-lookup"><span data-stu-id="66eaf-142">**Object Orientation.**</span></span> <span data-ttu-id="66eaf-143">Klasy są zorientowane obiektowo, ale moduły nie są.</span><span class="sxs-lookup"><span data-stu-id="66eaf-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="66eaf-144">Dlatego tylko klasy mogą być tworzone jako obiekty.</span><span class="sxs-lookup"><span data-stu-id="66eaf-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="66eaf-145">Aby uzyskać więcej informacji, zobacz [obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="66eaf-145">For more information, see [Objects and Classes](../../programming-guide/language-features/objects-and-classes/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="66eaf-146">Reguły</span><span class="sxs-lookup"><span data-stu-id="66eaf-146">Rules</span></span>

- <span data-ttu-id="66eaf-147">**Modyfikatory.**</span><span class="sxs-lookup"><span data-stu-id="66eaf-147">**Modifiers.**</span></span> <span data-ttu-id="66eaf-148">Wszystkie elementy członkowskie modułu są niejawnie [udostępniane](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="66eaf-148">All module members are implicitly [Shared](../modifiers/shared.md).</span></span> <span data-ttu-id="66eaf-149">Nie można użyć `Shared` słowa kluczowego podczas deklarowania elementu członkowskiego i nie można zmienić stanu udostępnionego żadnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="66eaf-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>

- <span data-ttu-id="66eaf-150">**Strukturze.**</span><span class="sxs-lookup"><span data-stu-id="66eaf-150">**Inheritance.**</span></span> <span data-ttu-id="66eaf-151">Moduł nie może dziedziczyć z dowolnego typu innego niż <xref:System.Object> , z którego dziedziczy wszystkie moduły.</span><span class="sxs-lookup"><span data-stu-id="66eaf-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="66eaf-152">W szczególności jeden moduł nie może dziedziczyć z innego.</span><span class="sxs-lookup"><span data-stu-id="66eaf-152">In particular, one module cannot inherit from another.</span></span>

  <span data-ttu-id="66eaf-153">Nie można użyć [instrukcji Inherits](inherits-statement.md) w definicji modułu, nawet do określenia <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="66eaf-153">You cannot use the [Inherits Statement](inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>

- <span data-ttu-id="66eaf-154">**Właściwość domyślna.**</span><span class="sxs-lookup"><span data-stu-id="66eaf-154">**Default Property.**</span></span> <span data-ttu-id="66eaf-155">Nie można definiować żadnych właściwości domyślnych w module.</span><span class="sxs-lookup"><span data-stu-id="66eaf-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="66eaf-156">Aby uzyskać więcej informacji, zobacz [domyślne](../modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="66eaf-156">For more information, see [Default](../modifiers/default.md).</span></span>

## <a name="behavior"></a><span data-ttu-id="66eaf-157">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="66eaf-157">Behavior</span></span>

- <span data-ttu-id="66eaf-158">**Poziom dostępu.**</span><span class="sxs-lookup"><span data-stu-id="66eaf-158">**Access Level.**</span></span> <span data-ttu-id="66eaf-159">W module można zadeklarować każdego członka z własnym poziomem dostępu.</span><span class="sxs-lookup"><span data-stu-id="66eaf-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="66eaf-160">Członkowie modułów domyślnie mają dostęp [publiczny](../modifiers/public.md) , z wyjątkiem zmiennych i stałych, które domyślnie są dostępem [prywatnym](../modifiers/private.md) .</span><span class="sxs-lookup"><span data-stu-id="66eaf-160">Module members default to [Public](../modifiers/public.md) access, except variables and constants, which default to [Private](../modifiers/private.md) access.</span></span> <span data-ttu-id="66eaf-161">Gdy moduł ma więcej ograniczony dostęp niż jeden z jego składowych, pierwszeństwo ma określony poziom dostępu do modułu.</span><span class="sxs-lookup"><span data-stu-id="66eaf-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>

- <span data-ttu-id="66eaf-162">**Scope.**</span><span class="sxs-lookup"><span data-stu-id="66eaf-162">**Scope.**</span></span> <span data-ttu-id="66eaf-163">Moduł znajduje się w zakresie w całej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="66eaf-163">A module is in scope throughout its namespace.</span></span>

  <span data-ttu-id="66eaf-164">Każdy element członkowski modułu jest zakresem całego modułu.</span><span class="sxs-lookup"><span data-stu-id="66eaf-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="66eaf-165">Zwróć uwagę, że wszyscy członkowie przechodzą *promocję typu*, co powoduje, że ich zakres zostanie podwyższony do przestrzeni nazw zawierającej moduł.</span><span class="sxs-lookup"><span data-stu-id="66eaf-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="66eaf-166">Aby uzyskać więcej informacji, zobacz [Promocja typu](../../programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="66eaf-166">For more information, see [Type Promotion](../../programming-guide/language-features/declared-elements/type-promotion.md).</span></span>

- <span data-ttu-id="66eaf-167">**Branego.**</span><span class="sxs-lookup"><span data-stu-id="66eaf-167">**Qualification.**</span></span> <span data-ttu-id="66eaf-168">W projekcie może istnieć wiele modułów i można zadeklarować składowe o tej samej nazwie w co najmniej dwóch modułach.</span><span class="sxs-lookup"><span data-stu-id="66eaf-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="66eaf-169">Należy jednak zakwalifikować każde odwołanie do takiego elementu członkowskiego z odpowiednią nazwą modułu, jeśli odwołanie pochodzi spoza tego modułu.</span><span class="sxs-lookup"><span data-stu-id="66eaf-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="66eaf-170">Aby uzyskać więcej informacji, zobacz [odwołania do zadeklarowanych elementów](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="66eaf-170">For more information, see [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="example"></a><span data-ttu-id="66eaf-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="66eaf-171">Example</span></span>

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a><span data-ttu-id="66eaf-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66eaf-172">See also</span></span>

- [<span data-ttu-id="66eaf-173">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="66eaf-173">Class Statement</span></span>](class-statement.md)
- [<span data-ttu-id="66eaf-174">Namespace — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="66eaf-174">Namespace Statement</span></span>](namespace-statement.md)
- [<span data-ttu-id="66eaf-175">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="66eaf-175">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="66eaf-176">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="66eaf-176">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="66eaf-177">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="66eaf-177">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="66eaf-178">Promocja typu</span><span class="sxs-lookup"><span data-stu-id="66eaf-178">Type Promotion</span></span>](../../programming-guide/language-features/declared-elements/type-promotion.md)
