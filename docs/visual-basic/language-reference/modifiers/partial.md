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
ms.openlocfilehash: dd7550b8b1e164c55bd97828d395b43a60c87cfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929950"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="ca2e0-102">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca2e0-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="ca2e0-103">Wskazuje, że deklaracja typu jest częściową definicją typu.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="ca2e0-104">Można podzielić definicję typu między kilka deklaracji za pomocą `Partial` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="ca2e0-105">Możesz użyć dowolną liczbę deklaracji częściowych, tak jak wiele różnych plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="ca2e0-106">Wszystkie deklaracje muszą jednak znajdować się w tym samym zestawie i w tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca2e0-107">Visual Basic obsługuje *metody częściowe*, które zwykle są implementowane w klasach częściowych.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="ca2e0-108">Aby uzyskać więcej informacji, zobacz [częściowe metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) i [Sub instrukcji](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ca2e0-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca2e0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca2e0-109">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="ca2e0-110">Części</span><span class="sxs-lookup"><span data-stu-id="ca2e0-110">Parts</span></span>  
  
|<span data-ttu-id="ca2e0-111">Termin</span><span class="sxs-lookup"><span data-stu-id="ca2e0-111">Term</span></span>|<span data-ttu-id="ca2e0-112">Definicja</span><span class="sxs-lookup"><span data-stu-id="ca2e0-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="ca2e0-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-113">Optional.</span></span> <span data-ttu-id="ca2e0-114">Lista atrybutów, które są stosowane do tego typu.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="ca2e0-115">Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy kątowe (`< >`).</span><span class="sxs-lookup"><span data-stu-id="ca2e0-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="ca2e0-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-116">Optional.</span></span> <span data-ttu-id="ca2e0-117">Określa kod, który może uzyskać dostęp do tego typu.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-117">Specifies what code can access this type.</span></span> <span data-ttu-id="ca2e0-118">Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ca2e0-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="ca2e0-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-119">Optional.</span></span> <span data-ttu-id="ca2e0-120">Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="ca2e0-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="ca2e0-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-121">Optional.</span></span> <span data-ttu-id="ca2e0-122">Zobacz [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="ca2e0-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="ca2e0-123">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-123">Optional.</span></span> <span data-ttu-id="ca2e0-124">Zobacz [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="ca2e0-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="ca2e0-125">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-125">Required.</span></span> <span data-ttu-id="ca2e0-126">Nazwa tego typu.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-126">Name of this type.</span></span> <span data-ttu-id="ca2e0-127">Musi odpowiadać nazwie zdefiniowanej we wszystkich innych deklaracjach częściowych tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="ca2e0-128">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-128">Optional.</span></span> <span data-ttu-id="ca2e0-129">Określa, że jest to typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="ca2e0-130">Zobacz [typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="ca2e0-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="ca2e0-131">Wymagane w przypadku użycia [programu](../../../visual-basic/language-reference/statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ca2e0-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="ca2e0-132">Zobacz [Lista typów](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="ca2e0-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="ca2e0-133">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-133">Optional.</span></span> <span data-ttu-id="ca2e0-134">Zobacz [instrukcje Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ca2e0-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="ca2e0-135">Wymagane, `Inherits`Jeśli używasz.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="ca2e0-136">Nazwa klasy lub interfejsu, z której pochodzi ta klasa.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="ca2e0-137">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-137">Optional.</span></span> <span data-ttu-id="ca2e0-138">Zobacz [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ca2e0-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="ca2e0-139">Wymagane, `Implements`Jeśli używasz.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-139">Required if you use `Implements`.</span></span> <span data-ttu-id="ca2e0-140">Nazwy interfejsów implementowanych przez ten typ.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="ca2e0-141">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-141">Optional.</span></span> <span data-ttu-id="ca2e0-142">Instrukcje, które deklarują dodatkowe zmienne i zdarzenia dla typu.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="ca2e0-143">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-143">Optional.</span></span> <span data-ttu-id="ca2e0-144">Instrukcje, które deklarują i definiują dodatkowe procedury dla typu.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="ca2e0-145">`End Class` lub `End Structure`</span><span class="sxs-lookup"><span data-stu-id="ca2e0-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="ca2e0-146">Zakończenie tej `Class` częściowej `Structure` lub definicji.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca2e0-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca2e0-147">Remarks</span></span>  
 <span data-ttu-id="ca2e0-148">Visual Basic używa definicji klasy częściowej do oddzielenia wygenerowanego kodu od kodu napisanego przez użytkownika w oddzielnych plikach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="ca2e0-149">Na przykład **Projektant formularzy systemu Windows** definiuje klasy częściowe dla formantów, takich jak <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="ca2e0-150">Nie należy modyfikować wygenerowanego kodu w tych kontrolkach.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="ca2e0-151">W przypadku tworzenia typu częściowego stosowane są wszystkie reguły tworzenia klas, struktur, interfejsów i modułów, takie jak te dla modyfikatorów użycia i dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="ca2e0-152">Najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="ca2e0-152">Best Practices</span></span>  
  
- <span data-ttu-id="ca2e0-153">W normalnych warunkach nie należy dzielić na rozwój jednego typu między dwie lub więcej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="ca2e0-154">W związku z tym w większości przypadków `Partial` słowo kluczowe nie jest potrzebne.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="ca2e0-155">W celu zapewnienia czytelności każda częściowa deklaracja typu powinna zawierać `Partial` słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="ca2e0-156">Kompilator zezwala przynajmniej jednej deklaracji częściowej na pominięcie słowa kluczowego; Jeśli dwa lub więcej pomijają, kompilator sygnalizuje błąd.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="ca2e0-157">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="ca2e0-157">Behavior</span></span>  
  
- <span data-ttu-id="ca2e0-158">**Związek deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="ca2e0-158">**Union of Declarations.**</span></span> <span data-ttu-id="ca2e0-159">Kompilator traktuje typ jako związek wszystkich jego częściowych deklaracji.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="ca2e0-160">Każdy modyfikator od każdej częściowej definicji ma zastosowanie do całego typu, a każdy element członkowski z każdej częściowej definicji jest dostępny dla całego typu.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="ca2e0-161">**Promocja typu nie jest dozwolona dla typów częściowych w modułach.**</span><span class="sxs-lookup"><span data-stu-id="ca2e0-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="ca2e0-162">Jeśli częściowa definicja znajduje się w module, podwyższanie poziomu tego typu jest automatycznie obniżane.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="ca2e0-163">W takim przypadku zestaw częściowych definicji może spowodować nieoczekiwane wyniki, a nawet błędy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="ca2e0-164">Aby uzyskać więcej informacji, zobacz [Promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="ca2e0-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="ca2e0-165">Kompilator Scala definicje częściowe tylko wtedy, gdy ich w pełni kwalifikowane ścieżki są identyczne.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="ca2e0-166">Słowa kluczowego `Partial` można używać w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="ca2e0-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ca2e0-167">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ca2e0-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="ca2e0-168">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ca2e0-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="ca2e0-169">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca2e0-169">Example</span></span>  
 <span data-ttu-id="ca2e0-170">Poniższy przykład dzieli definicję klasy `sampleClass` na dwie deklaracje, z których każda definiuje inną `Sub` procedurę.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="ca2e0-171">Dwie częściowe definicje w poprzednim przykładzie mogą znajdować się w tym samym pliku źródłowym lub w dwóch różnych plikach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="ca2e0-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca2e0-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca2e0-172">See also</span></span>

- [<span data-ttu-id="ca2e0-173">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ca2e0-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="ca2e0-174">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ca2e0-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="ca2e0-175">Promocja typu</span><span class="sxs-lookup"><span data-stu-id="ca2e0-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="ca2e0-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="ca2e0-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="ca2e0-177">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca2e0-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="ca2e0-178">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="ca2e0-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
