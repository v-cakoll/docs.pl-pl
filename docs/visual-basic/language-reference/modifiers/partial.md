---
title: Częściowe
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
ms.openlocfilehash: df85571b757fd54496677bad1195fab9690b79cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351358"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="36e64-102">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36e64-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="36e64-103">Indicates that a type declaration is a partial definition of the type.</span><span class="sxs-lookup"><span data-stu-id="36e64-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="36e64-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span><span class="sxs-lookup"><span data-stu-id="36e64-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="36e64-105">You can use as many partial declarations as you want, in as many different source files as you want.</span><span class="sxs-lookup"><span data-stu-id="36e64-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="36e64-106">However, all the declarations must be in the same assembly and the same namespace.</span><span class="sxs-lookup"><span data-stu-id="36e64-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36e64-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span><span class="sxs-lookup"><span data-stu-id="36e64-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="36e64-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="36e64-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36e64-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="36e64-109">Syntax</span></span>  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="36e64-110">Części</span><span class="sxs-lookup"><span data-stu-id="36e64-110">Parts</span></span>  
  
|<span data-ttu-id="36e64-111">Termin</span><span class="sxs-lookup"><span data-stu-id="36e64-111">Term</span></span>|<span data-ttu-id="36e64-112">Definicja</span><span class="sxs-lookup"><span data-stu-id="36e64-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="36e64-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="36e64-113">Optional.</span></span> <span data-ttu-id="36e64-114">List of attributes that apply to this type.</span><span class="sxs-lookup"><span data-stu-id="36e64-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="36e64-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span><span class="sxs-lookup"><span data-stu-id="36e64-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="36e64-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="36e64-116">Optional.</span></span> <span data-ttu-id="36e64-117">Specifies what code can access this type.</span><span class="sxs-lookup"><span data-stu-id="36e64-117">Specifies what code can access this type.</span></span> <span data-ttu-id="36e64-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="36e64-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="36e64-119">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="36e64-119">Optional.</span></span> <span data-ttu-id="36e64-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="36e64-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="36e64-121">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="36e64-121">Optional.</span></span> <span data-ttu-id="36e64-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="36e64-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="36e64-123">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="36e64-123">Optional.</span></span> <span data-ttu-id="36e64-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="36e64-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="36e64-125">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="36e64-125">Required.</span></span> <span data-ttu-id="36e64-126">Name of this type.</span><span class="sxs-lookup"><span data-stu-id="36e64-126">Name of this type.</span></span> <span data-ttu-id="36e64-127">Must match the name defined in all other partial declarations of the same type.</span><span class="sxs-lookup"><span data-stu-id="36e64-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="36e64-128">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="36e64-128">Optional.</span></span> <span data-ttu-id="36e64-129">Specifies that this is a generic type.</span><span class="sxs-lookup"><span data-stu-id="36e64-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="36e64-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="36e64-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="36e64-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="36e64-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="36e64-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="36e64-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="36e64-133">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="36e64-133">Optional.</span></span> <span data-ttu-id="36e64-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="36e64-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="36e64-135">Required if you use `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="36e64-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="36e64-136">The name of the class or interface from which this class derives.</span><span class="sxs-lookup"><span data-stu-id="36e64-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="36e64-137">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="36e64-137">Optional.</span></span> <span data-ttu-id="36e64-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="36e64-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="36e64-139">Required if you use `Implements`.</span><span class="sxs-lookup"><span data-stu-id="36e64-139">Required if you use `Implements`.</span></span> <span data-ttu-id="36e64-140">The names of the interfaces this type implements.</span><span class="sxs-lookup"><span data-stu-id="36e64-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="36e64-141">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="36e64-141">Optional.</span></span> <span data-ttu-id="36e64-142">Statements which declare additional variables and events for the type.</span><span class="sxs-lookup"><span data-stu-id="36e64-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="36e64-143">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="36e64-143">Optional.</span></span> <span data-ttu-id="36e64-144">Statements which declare and define additional procedures for the type.</span><span class="sxs-lookup"><span data-stu-id="36e64-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="36e64-145">`End Class` or `End Structure`</span><span class="sxs-lookup"><span data-stu-id="36e64-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="36e64-146">Ends this partial `Class` or `Structure` definition.</span><span class="sxs-lookup"><span data-stu-id="36e64-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36e64-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36e64-147">Remarks</span></span>  
 <span data-ttu-id="36e64-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span><span class="sxs-lookup"><span data-stu-id="36e64-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="36e64-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="36e64-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="36e64-150">You should not modify the generated code in these controls.</span><span class="sxs-lookup"><span data-stu-id="36e64-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="36e64-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span><span class="sxs-lookup"><span data-stu-id="36e64-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="36e64-152">Najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="36e64-152">Best Practices</span></span>  
  
- <span data-ttu-id="36e64-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span><span class="sxs-lookup"><span data-stu-id="36e64-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="36e64-154">Therefore, in most cases you do not need the `Partial` keyword.</span><span class="sxs-lookup"><span data-stu-id="36e64-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="36e64-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span><span class="sxs-lookup"><span data-stu-id="36e64-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="36e64-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span><span class="sxs-lookup"><span data-stu-id="36e64-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="36e64-157">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="36e64-157">Behavior</span></span>  
  
- <span data-ttu-id="36e64-158">**Union of Declarations.**</span><span class="sxs-lookup"><span data-stu-id="36e64-158">**Union of Declarations.**</span></span> <span data-ttu-id="36e64-159">The compiler treats the type as the union of all its partial declarations.</span><span class="sxs-lookup"><span data-stu-id="36e64-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="36e64-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span><span class="sxs-lookup"><span data-stu-id="36e64-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="36e64-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span><span class="sxs-lookup"><span data-stu-id="36e64-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="36e64-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span><span class="sxs-lookup"><span data-stu-id="36e64-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="36e64-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span><span class="sxs-lookup"><span data-stu-id="36e64-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="36e64-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="36e64-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="36e64-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span><span class="sxs-lookup"><span data-stu-id="36e64-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="36e64-166">The `Partial` keyword can be used in these contexts:</span><span class="sxs-lookup"><span data-stu-id="36e64-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="36e64-167">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="36e64-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="36e64-168">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="36e64-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="36e64-169">Przykład</span><span class="sxs-lookup"><span data-stu-id="36e64-169">Example</span></span>  
 <span data-ttu-id="36e64-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="36e64-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="36e64-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span><span class="sxs-lookup"><span data-stu-id="36e64-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e64-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36e64-172">See also</span></span>

- [<span data-ttu-id="36e64-173">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="36e64-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="36e64-174">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="36e64-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="36e64-175">Promocja typu</span><span class="sxs-lookup"><span data-stu-id="36e64-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="36e64-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="36e64-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="36e64-177">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36e64-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="36e64-178">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="36e64-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
