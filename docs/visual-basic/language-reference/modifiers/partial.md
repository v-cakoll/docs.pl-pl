---
title: Partial (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: 0f74935d58d47e65b5eb614abc86a3fc9c8e6c42
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838368"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="8c226-102">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c226-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="8c226-103">Wskazuje częściową definicję typu deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="8c226-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="8c226-104">Definicję typu między kilka deklaracji można podzielić przy użyciu `Partial` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8c226-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="8c226-105">Można użyć tylu częściowe deklaracje, jak chcesz, tyle plików innego źródła.</span><span class="sxs-lookup"><span data-stu-id="8c226-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="8c226-106">Jednak wszystkie deklaracje musi należeć do tego samego zestawu i tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8c226-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c226-107">Obsługa języka Visual Basic *metod częściowych*, które są zazwyczaj implementowani w klas częściowych.</span><span class="sxs-lookup"><span data-stu-id="8c226-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="8c226-108">Aby uzyskać więcej informacji, zobacz [metod częściowych](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) i [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8c226-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c226-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c226-109">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="8c226-110">Części</span><span class="sxs-lookup"><span data-stu-id="8c226-110">Parts</span></span>  
  
|<span data-ttu-id="8c226-111">Termin</span><span class="sxs-lookup"><span data-stu-id="8c226-111">Term</span></span>|<span data-ttu-id="8c226-112">Definicja</span><span class="sxs-lookup"><span data-stu-id="8c226-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="8c226-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8c226-113">Optional.</span></span> <span data-ttu-id="8c226-114">Lista atrybutów, które są stosowane do tego typu.</span><span class="sxs-lookup"><span data-stu-id="8c226-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="8c226-115">Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ostre (`< >`).</span><span class="sxs-lookup"><span data-stu-id="8c226-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="8c226-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8c226-116">Optional.</span></span> <span data-ttu-id="8c226-117">Określa, jaki kod może uzyskać dostęp do tego typu.</span><span class="sxs-lookup"><span data-stu-id="8c226-117">Specifies what code can access this type.</span></span> <span data-ttu-id="8c226-118">Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8c226-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="8c226-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8c226-119">Optional.</span></span> <span data-ttu-id="8c226-120">Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="8c226-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="8c226-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8c226-121">Optional.</span></span> <span data-ttu-id="8c226-122">Zobacz [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="8c226-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="8c226-123">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8c226-123">Optional.</span></span> <span data-ttu-id="8c226-124">Zobacz [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="8c226-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="8c226-125">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="8c226-125">Required.</span></span> <span data-ttu-id="8c226-126">Nazwa tego typu.</span><span class="sxs-lookup"><span data-stu-id="8c226-126">Name of this type.</span></span> <span data-ttu-id="8c226-127">Musi być zgodna z nazwą zdefiniowaną w innych częściowe deklaracje tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="8c226-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="8c226-128">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8c226-128">Optional.</span></span> <span data-ttu-id="8c226-129">Określa, że jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="8c226-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="8c226-130">Zobacz [typów ogólnych w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="8c226-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="8c226-131">Wymagane w przypadku użycia [z](../../../visual-basic/language-reference/statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8c226-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="8c226-132">Zobacz [Lista typów](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="8c226-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="8c226-133">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8c226-133">Optional.</span></span> <span data-ttu-id="8c226-134">Zobacz [Inherits — instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8c226-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="8c226-135">Wymagane w przypadku użycia `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="8c226-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="8c226-136">Nazwa klasy lub interfejsu, z której pochodzi ta klasa.</span><span class="sxs-lookup"><span data-stu-id="8c226-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="8c226-137">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8c226-137">Optional.</span></span> <span data-ttu-id="8c226-138">Zobacz [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8c226-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="8c226-139">Wymagane w przypadku użycia `Implements`.</span><span class="sxs-lookup"><span data-stu-id="8c226-139">Required if you use `Implements`.</span></span> <span data-ttu-id="8c226-140">Nazwy interfejsów, które implementuje tego typu.</span><span class="sxs-lookup"><span data-stu-id="8c226-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="8c226-141">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8c226-141">Optional.</span></span> <span data-ttu-id="8c226-142">Instrukcje, które zadeklarować dodatkowe zmienne i zdarzenia dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="8c226-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="8c226-143">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8c226-143">Optional.</span></span> <span data-ttu-id="8c226-144">Instrukcje, które deklarowania i definiowania dodatkowych procedur dla typu.</span><span class="sxs-lookup"><span data-stu-id="8c226-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="8c226-145">`End Class` lub `End Structure`</span><span class="sxs-lookup"><span data-stu-id="8c226-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="8c226-146">Kończy się w tej części `Class` lub `Structure` definicji.</span><span class="sxs-lookup"><span data-stu-id="8c226-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c226-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c226-147">Remarks</span></span>  
 <span data-ttu-id="8c226-148">Visual Basic używa definicji częściowej klasy do oddzielania wygenerowanego kodu z utworzonymi przez użytkownika kod w plikach źródłowych oddzielne.</span><span class="sxs-lookup"><span data-stu-id="8c226-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="8c226-149">Na przykład **projektanta formularzy Windows** definiuje częściowe klasy dla kontrolek, takich jak <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="8c226-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="8c226-150">Kod wygenerowany w tych kontrolek nie należy modyfikować.</span><span class="sxs-lookup"><span data-stu-id="8c226-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="8c226-151">Wszystkie reguły dla klasy, struktury, interfejsu i tworzenia modułu, takich jak użycie modyfikatora i dziedziczenie, zastosowanie przy tworzeniu typu częściowego.</span><span class="sxs-lookup"><span data-stu-id="8c226-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="8c226-152">Najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="8c226-152">Best Practices</span></span>  
  
-   <span data-ttu-id="8c226-153">W normalnych warunkach należy nie Podziel rozwój jednego typu na dwóch lub więcej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="8c226-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="8c226-154">W związku z tym, w większości przypadków nie trzeba `Partial` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8c226-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
-   <span data-ttu-id="8c226-155">Aby zwiększyć czytelność, powinien zawierać każdy częściowa deklaracja typu `Partial` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8c226-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="8c226-156">Kompilator umożliwi co najwyżej jeden częściowa deklaracja pominięcie słowa kluczowego. Jeśli co najmniej dwóch Pomiń ją kompilator sygnalizuje błąd.</span><span class="sxs-lookup"><span data-stu-id="8c226-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="8c226-157">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="8c226-157">Behavior</span></span>  
  
-   <span data-ttu-id="8c226-158">**Unia deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="8c226-158">**Union of Declarations.**</span></span> <span data-ttu-id="8c226-159">Kompilator traktuje typ jako sumę wszystkich częściowe deklaracje.</span><span class="sxs-lookup"><span data-stu-id="8c226-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="8c226-160">Każdy modyfikator z każdym częściowa definicja odnoszące się do całego typu, a każdy element członkowski z każdym częściowa definicja jest dostępna dla wszystkich typu.</span><span class="sxs-lookup"><span data-stu-id="8c226-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
-   <span data-ttu-id="8c226-161">**Promocja typu nie jest dozwolona dla typów częściowych w modułach.**</span><span class="sxs-lookup"><span data-stu-id="8c226-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="8c226-162">Jeśli częściowa definicja znajduje się wewnątrz modułu, promocji typu tego typu jest bezcelowe automatycznie.</span><span class="sxs-lookup"><span data-stu-id="8c226-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="8c226-163">W takim przypadku zestaw definicje częściowe może spowodować nieoczekiwane wyniki, a nawet błędy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="8c226-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="8c226-164">Aby uzyskać więcej informacji, zobacz [promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="8c226-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="8c226-165">Kompilator scala definicje częściowe, tylko wtedy, gdy ich w pełni kwalifikowanej ścieżki są identyczne.</span><span class="sxs-lookup"><span data-stu-id="8c226-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="8c226-166">Słowa kluczowego `Partial` można używać w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="8c226-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="8c226-167">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c226-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="8c226-168">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c226-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="8c226-169">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c226-169">Example</span></span>  
 <span data-ttu-id="8c226-170">Poniższy przykład dzieli definicję klasy `sampleClass` na dwie deklaracje, z których każdy definiuje innego `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="8c226-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="8c226-171">Dwie definicje częściowe w poprzednim przykładzie może być w tym samym pliku źródłowym lub w dwóch innych plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="8c226-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c226-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c226-172">See also</span></span>

- [<span data-ttu-id="8c226-173">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c226-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="8c226-174">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c226-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="8c226-175">Promocja typu</span><span class="sxs-lookup"><span data-stu-id="8c226-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="8c226-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="8c226-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="8c226-177">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c226-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="8c226-178">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="8c226-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
