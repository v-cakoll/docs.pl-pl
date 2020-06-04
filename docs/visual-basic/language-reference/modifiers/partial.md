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
ms.openlocfilehash: 650ead2f0deb9813b26241a6a4676907de3f263d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362245"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="a1cb8-102">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1cb8-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="a1cb8-103">Wskazuje, że deklaracja typu jest częściową definicją typu.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="a1cb8-104">Można podzielić definicję typu między kilka deklaracji za pomocą `Partial` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="a1cb8-105">Możesz użyć dowolną liczbę deklaracji częściowych, tak jak wiele różnych plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="a1cb8-106">Wszystkie deklaracje muszą jednak znajdować się w tym samym zestawie i w tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1cb8-107">Visual Basic obsługuje *metody częściowe*, które zwykle są implementowane w klasach częściowych.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="a1cb8-108">Aby uzyskać więcej informacji, zobacz [częściowe metody](../../programming-guide/language-features/procedures/partial-methods.md) i [Sub instrukcji](../statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a1cb8-108">For more information, see [Partial Methods](../../programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1cb8-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1cb8-109">Syntax</span></span>  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="a1cb8-110">Części</span><span class="sxs-lookup"><span data-stu-id="a1cb8-110">Parts</span></span>  
  
|<span data-ttu-id="a1cb8-111">Termin</span><span class="sxs-lookup"><span data-stu-id="a1cb8-111">Term</span></span>|<span data-ttu-id="a1cb8-112">Definicja</span><span class="sxs-lookup"><span data-stu-id="a1cb8-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="a1cb8-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-113">Optional.</span></span> <span data-ttu-id="a1cb8-114">Lista atrybutów, które są stosowane do tego typu.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="a1cb8-115">Należy ująć [listę atrybutów](../statements/attribute-list.md) w nawiasy kątowe ( `< >` ).</span><span class="sxs-lookup"><span data-stu-id="a1cb8-115">You must enclose the [Attribute List](../statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="a1cb8-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-116">Optional.</span></span> <span data-ttu-id="a1cb8-117">Określa kod, który może uzyskać dostęp do tego typu.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-117">Specifies what code can access this type.</span></span> <span data-ttu-id="a1cb8-118">Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a1cb8-118">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="a1cb8-119">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-119">Optional.</span></span> <span data-ttu-id="a1cb8-120">Zobacz [Shadows](shadows.md).</span><span class="sxs-lookup"><span data-stu-id="a1cb8-120">See [Shadows](shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="a1cb8-121">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-121">Optional.</span></span> <span data-ttu-id="a1cb8-122">Zobacz [MustInherit](mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="a1cb8-122">See [MustInherit](mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="a1cb8-123">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-123">Optional.</span></span> <span data-ttu-id="a1cb8-124">Zobacz [NotInheritable](notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="a1cb8-124">See [NotInheritable](notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="a1cb8-125">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-125">Required.</span></span> <span data-ttu-id="a1cb8-126">Nazwa tego typu.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-126">Name of this type.</span></span> <span data-ttu-id="a1cb8-127">Musi odpowiadać nazwie zdefiniowanej we wszystkich innych deklaracjach częściowych tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="a1cb8-128">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-128">Optional.</span></span> <span data-ttu-id="a1cb8-129">Określa, że jest to typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="a1cb8-130">Zobacz [typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="a1cb8-130">See [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="a1cb8-131">Wymagane w przypadku użycia [programu](../statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a1cb8-131">Required if you use [Of](../statements/of-clause.md).</span></span> <span data-ttu-id="a1cb8-132">Zobacz [Lista typów](../statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="a1cb8-132">See [Type List](../statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="a1cb8-133">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-133">Optional.</span></span> <span data-ttu-id="a1cb8-134">Zobacz [instrukcje Inherits](../statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a1cb8-134">See [Inherits Statement](../statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="a1cb8-135">Wymagane, jeśli używasz `Inherits` .</span><span class="sxs-lookup"><span data-stu-id="a1cb8-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="a1cb8-136">Nazwa klasy lub interfejsu, z której pochodzi ta klasa.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="a1cb8-137">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-137">Optional.</span></span> <span data-ttu-id="a1cb8-138">Zobacz [instrukcja Implements](../statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a1cb8-138">See [Implements Statement](../statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="a1cb8-139">Wymagane, jeśli używasz `Implements` .</span><span class="sxs-lookup"><span data-stu-id="a1cb8-139">Required if you use `Implements`.</span></span> <span data-ttu-id="a1cb8-140">Nazwy interfejsów implementowanych przez ten typ.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="a1cb8-141">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-141">Optional.</span></span> <span data-ttu-id="a1cb8-142">Instrukcje, które deklarują dodatkowe zmienne i zdarzenia dla typu.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="a1cb8-143">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-143">Optional.</span></span> <span data-ttu-id="a1cb8-144">Instrukcje, które deklarują i definiują dodatkowe procedury dla typu.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="a1cb8-145">`End Class` lub `End Structure`</span><span class="sxs-lookup"><span data-stu-id="a1cb8-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="a1cb8-146">Zakończenie tej częściowej `Class` lub `Structure` definicji.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1cb8-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1cb8-147">Remarks</span></span>  
 <span data-ttu-id="a1cb8-148">Visual Basic używa definicji klasy częściowej do oddzielenia wygenerowanego kodu od kodu napisanego przez użytkownika w oddzielnych plikach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="a1cb8-149">Na przykład **Projektant formularzy systemu Windows** definiuje klasy częściowe dla formantów, takich jak <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="a1cb8-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="a1cb8-150">Nie należy modyfikować wygenerowanego kodu w tych kontrolkach.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="a1cb8-151">W przypadku tworzenia typu częściowego stosowane są wszystkie reguły tworzenia klas, struktur, interfejsów i modułów, takie jak te dla modyfikatorów użycia i dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="a1cb8-152">Najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a1cb8-152">Best Practices</span></span>  
  
- <span data-ttu-id="a1cb8-153">W normalnych warunkach nie należy dzielić na rozwój jednego typu między dwie lub więcej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="a1cb8-154">W związku z tym w większości przypadków słowo kluczowe nie jest potrzebne `Partial` .</span><span class="sxs-lookup"><span data-stu-id="a1cb8-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="a1cb8-155">W celu zapewnienia czytelności każda częściowa deklaracja typu powinna zawierać `Partial` słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="a1cb8-156">Kompilator zezwala przynajmniej jednej deklaracji częściowej na pominięcie słowa kluczowego; Jeśli dwa lub więcej pomijają, kompilator sygnalizuje błąd.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="a1cb8-157">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="a1cb8-157">Behavior</span></span>  
  
- <span data-ttu-id="a1cb8-158">**Związek deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="a1cb8-158">**Union of Declarations.**</span></span> <span data-ttu-id="a1cb8-159">Kompilator traktuje typ jako związek wszystkich jego częściowych deklaracji.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="a1cb8-160">Każdy modyfikator od każdej częściowej definicji ma zastosowanie do całego typu, a każdy element członkowski z każdej częściowej definicji jest dostępny dla całego typu.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="a1cb8-161">**Promocja typu nie jest dozwolona dla typów częściowych w modułach.**</span><span class="sxs-lookup"><span data-stu-id="a1cb8-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="a1cb8-162">Jeśli częściowa definicja znajduje się w module, podwyższanie poziomu tego typu jest automatycznie obniżane.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="a1cb8-163">W takim przypadku zestaw częściowych definicji może spowodować nieoczekiwane wyniki, a nawet błędy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="a1cb8-164">Aby uzyskać więcej informacji, zobacz [Promocja typu](../../programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="a1cb8-164">For more information, see [Type Promotion](../../programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="a1cb8-165">Kompilator Scala definicje częściowe tylko wtedy, gdy ich w pełni kwalifikowane ścieżki są identyczne.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="a1cb8-166">`Partial`Słowo kluczowe może być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="a1cb8-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="a1cb8-167">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a1cb8-167">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="a1cb8-168">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="a1cb8-168">Structure Statement</span></span>](../statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="a1cb8-169">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1cb8-169">Example</span></span>  
 <span data-ttu-id="a1cb8-170">Poniższy przykład dzieli definicję klasy `sampleClass` na dwie deklaracje, z których każda definiuje inną `Sub` procedurę.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="a1cb8-171">Dwie częściowe definicje w poprzednim przykładzie mogą znajdować się w tym samym pliku źródłowym lub w dwóch różnych plikach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="a1cb8-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1cb8-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1cb8-172">See also</span></span>

- [<span data-ttu-id="a1cb8-173">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a1cb8-173">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="a1cb8-174">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="a1cb8-174">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="a1cb8-175">Promocja typu</span><span class="sxs-lookup"><span data-stu-id="a1cb8-175">Type Promotion</span></span>](../../programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="a1cb8-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="a1cb8-176">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="a1cb8-177">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1cb8-177">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="a1cb8-178">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="a1cb8-178">Partial Methods</span></span>](../../programming-guide/language-features/procedures/partial-methods.md)
