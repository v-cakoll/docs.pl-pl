---
title: "Lista typów (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 35e72414b236615dc230b654ccfeed290841fb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="3a0d8-102">Lista typów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a0d8-102">Type List (Visual Basic)</span></span>
<span data-ttu-id="3a0d8-103">Określa *parametry typu* dla *ogólnego* elementu programistycznego.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="3a0d8-104">Wiele parametrów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="3a0d8-105">Poniżej przedstawiono składnię dla parametru typu.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-105">Following is the syntax for one type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a0d8-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a0d8-106">Syntax</span></span>  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a><span data-ttu-id="3a0d8-107">Części</span><span class="sxs-lookup"><span data-stu-id="3a0d8-107">Parts</span></span>  
  
|<span data-ttu-id="3a0d8-108">Termin</span><span class="sxs-lookup"><span data-stu-id="3a0d8-108">Term</span></span>|<span data-ttu-id="3a0d8-109">Definicja</span><span class="sxs-lookup"><span data-stu-id="3a0d8-109">Definition</span></span>|  
|---|---|  
|`genericmodifier`|<span data-ttu-id="3a0d8-110">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-110">Optional.</span></span> <span data-ttu-id="3a0d8-111">Może być używana tylko w interfejsach i delegatów.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="3a0d8-112">Można zadeklarować typu kowariantnego przy użyciu [limit](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) — słowo kluczowe lub kontrawariantnego przy użyciu [w](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="3a0d8-113">Zobacz [Kowariancja i Kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="3a0d8-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|  
|`typename`|<span data-ttu-id="3a0d8-114">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-114">Required.</span></span> <span data-ttu-id="3a0d8-115">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-115">Name of the type parameter.</span></span> <span data-ttu-id="3a0d8-116">Jest to symbol zastępczy, mają zostać zastąpione przez zdefiniowanego typu dostarczonych przez argument odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|  
|`constraintlist`|<span data-ttu-id="3a0d8-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-117">Optional.</span></span> <span data-ttu-id="3a0d8-118">Listę wymagań, które ograniczenia typu danych, które mogą być dostarczane na potrzeby `typename`.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="3a0d8-119">Jeśli masz wiele ograniczeń, ujmij ją w nawiasy klamrowe (`{ }`) i oddziel je przecinkami.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="3a0d8-120">Należy wprowadzić listę powiązanych z [jako](../../../visual-basic/language-reference/statements/as-clause.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="3a0d8-121">Możesz użyć `As` tylko jeden raz na początku listy.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-121">You use `As` only once, at the beginning of the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a0d8-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a0d8-122">Remarks</span></span>  
 <span data-ttu-id="3a0d8-123">Co ogólnego elementu programistycznego musi mieć co najmniej jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="3a0d8-124">Parametr typu jest symbolem zastępczym dla określonego typu ( *skonstruowane elementu*) kodu klienta określa, kiedy tworzy wystąpienie typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="3a0d8-125">Można zdefiniować klasy ogólnej, struktury, interfejsu, procedury lub delegowanie.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>  
  
 <span data-ttu-id="3a0d8-126">Aby uzyskać więcej informacji o tym, kiedy do definiowania typu ogólnego, zobacz [typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="3a0d8-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="3a0d8-127">Aby uzyskać więcej informacji dotyczących nazwy parametrów typu, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="3a0d8-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3a0d8-128">Reguły</span><span class="sxs-lookup"><span data-stu-id="3a0d8-128">Rules</span></span>  
  
-   <span data-ttu-id="3a0d8-129">**Nawiasy.**</span><span class="sxs-lookup"><span data-stu-id="3a0d8-129">**Parentheses.**</span></span> <span data-ttu-id="3a0d8-130">Jeśli możesz podać listę parametrów typu, należy ująć go w nawiasy i należy wprowadzić listę z [z](../../../visual-basic/language-reference/statements/of-clause.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="3a0d8-131">Możesz użyć `Of` tylko jeden raz na początku listy.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-131">You use `Of` only once, at the beginning of the list.</span></span>  
  
-   <span data-ttu-id="3a0d8-132">**Ograniczenia.**</span><span class="sxs-lookup"><span data-stu-id="3a0d8-132">**Constraints.**</span></span> <span data-ttu-id="3a0d8-133">Lista *ograniczenia* na typ parametru mogą obejmować następujące elementy w dowolnej kombinacji:</span><span class="sxs-lookup"><span data-stu-id="3a0d8-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>  
  
    -   <span data-ttu-id="3a0d8-134">Dowolna liczba interfejsów.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-134">Any number of interfaces.</span></span> <span data-ttu-id="3a0d8-135">Dostarczony typ musi implementować interfejs co na tej liście.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-135">The supplied type must implement every interface in this list.</span></span>  
  
    -   <span data-ttu-id="3a0d8-136">Co najwyżej jedną klasę.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-136">At most one class.</span></span> <span data-ttu-id="3a0d8-137">Dostarczony typ musi dziedziczyć z tej klasy.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-137">The supplied type must inherit from that class.</span></span>  
  
    -   <span data-ttu-id="3a0d8-138">`New` — Słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-138">The `New` keyword.</span></span> <span data-ttu-id="3a0d8-139">Dostarczony typ musi ujawniać konstruktor bez parametrów, dostępnym dla danego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="3a0d8-140">Jest to przydatne, jeśli w przypadku ograniczenia parametru typu, przez co najmniej jeden interfejs.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="3a0d8-141">Typ, który implementuje interfejsy nie ujawnia konstruktora, a w zależności od poziomu dostępu konstruktora kod w typie ogólnym może okazać się niemożliwe do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>  
  
    -   <span data-ttu-id="3a0d8-142">Albo `Class` — słowo kluczowe lub `Structure` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="3a0d8-143">`Class` — Słowo kluczowe ogranicza parametr typu ogólnego, aby wymagać przekazywania do niej wszystkich argumentów typu być typem referencyjnym, na przykład ciąg, tablicy lub delegatem, lub obiekt utworzony z klasy.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="3a0d8-144">`Structure` — Słowo kluczowe ogranicza parametr typu ogólnego, aby wymagał przekazywania do niej wszystkich argumentów typu jako typów wartości, na przykład typ struktury, wyliczenia lub podstawowym danych.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="3a0d8-145">Nie może zawierać jednocześnie `Class` i `Structure` w tym samym `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>  
  
     <span data-ttu-id="3a0d8-146">Dostarczony typ musi spełniać wymagania, co w `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>  
  
     <span data-ttu-id="3a0d8-147">Ograniczenia dotyczące każdego parametru typu są niezależne od ograniczenia dotyczące innych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="3a0d8-148">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="3a0d8-148">Behavior</span></span>  
  
-   <span data-ttu-id="3a0d8-149">**Podstawienia w czasie kompilacji.**</span><span class="sxs-lookup"><span data-stu-id="3a0d8-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="3a0d8-150">Po utworzeniu skonstruowanego typu z ogólnego elementu programistycznego, należy podać dla każdego parametru typu zdefiniowanego typu.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="3a0d8-151">Kompilator Visual Basic zastępuje typu dostarczonego dla wszystkich wystąpień `typename` w elemencie ogólnego.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>  
  
-   <span data-ttu-id="3a0d8-152">**Brak ograniczenia.**</span><span class="sxs-lookup"><span data-stu-id="3a0d8-152">**Absence of Constraints.**</span></span> <span data-ttu-id="3a0d8-153">Jeśli nie określisz żadnych ograniczeń dla parametru typu kodu jest ograniczona do operacji i elementy obsługiwane przez [Object — typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md) dla tego parametru typu.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a0d8-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a0d8-154">Example</span></span>  
 <span data-ttu-id="3a0d8-155">Poniższy przykład przedstawia definicję szkielet klasy ogólnego słownika, włączając funkcję szkielet, aby dodać nowy wpis do słownika.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="3a0d8-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a0d8-156">Example</span></span>  
 <span data-ttu-id="3a0d8-157">Ponieważ `dictionary` jest ogólny, kod, który korzysta z niego można tworzyć wiele obiektów z niego, każdy mających taką samą funkcję, ale na inny typ danych.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="3a0d8-158">W poniższym przykładzie przedstawiono wiersza kodu, który tworzy `dictionary` obiekt z `String` wpisy i `Integer` kluczy.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="3a0d8-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a0d8-159">Example</span></span>  
 <span data-ttu-id="3a0d8-160">Poniższy przykład przedstawia równoważne definicji szkielet generowane przez w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3a0d8-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3a0d8-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a0d8-161">See Also</span></span>  
 [<span data-ttu-id="3a0d8-162">Z</span><span class="sxs-lookup"><span data-stu-id="3a0d8-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="3a0d8-163">New — Operator</span><span class="sxs-lookup"><span data-stu-id="3a0d8-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="3a0d8-164">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a0d8-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="3a0d8-165">Object — typ danych</span><span class="sxs-lookup"><span data-stu-id="3a0d8-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="3a0d8-166">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="3a0d8-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="3a0d8-167">Structure — instrukcja</span><span class="sxs-lookup"><span data-stu-id="3a0d8-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="3a0d8-168">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="3a0d8-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="3a0d8-169">Porady: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="3a0d8-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="3a0d8-170">Kowariancja i Kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="3a0d8-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="3a0d8-171">W</span><span class="sxs-lookup"><span data-stu-id="3a0d8-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [<span data-ttu-id="3a0d8-172">Limit</span><span class="sxs-lookup"><span data-stu-id="3a0d8-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
