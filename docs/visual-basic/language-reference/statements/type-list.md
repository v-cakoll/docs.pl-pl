---
title: Lista typów (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: d071e59d94e51ca55167983d0ee3098bd5c7dd8f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843633"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="d7134-102">Lista typów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7134-102">Type List (Visual Basic)</span></span>
<span data-ttu-id="d7134-103">Określa *parametry typu* dla *ogólny* elementu programistycznego.</span><span class="sxs-lookup"><span data-stu-id="d7134-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="d7134-104">Wiele parametrów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="d7134-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="d7134-105">Poniżej przedstawiono składnię dla jednego typu parametru.</span><span class="sxs-lookup"><span data-stu-id="d7134-105">Following is the syntax for one type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7134-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7134-106">Syntax</span></span>  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d7134-107">Części</span><span class="sxs-lookup"><span data-stu-id="d7134-107">Parts</span></span>  
  
|<span data-ttu-id="d7134-108">Termin</span><span class="sxs-lookup"><span data-stu-id="d7134-108">Term</span></span>|<span data-ttu-id="d7134-109">Definicja</span><span class="sxs-lookup"><span data-stu-id="d7134-109">Definition</span></span>|  
|---|---|  
|`genericmodifier`|<span data-ttu-id="d7134-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d7134-110">Optional.</span></span> <span data-ttu-id="d7134-111">Mogą być używane tylko w interfejsach ogólnych i delegatach.</span><span class="sxs-lookup"><span data-stu-id="d7134-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="d7134-112">Można zadeklarować typu kowariantne przy użyciu [się](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) — słowo kluczowe lub kontrawariantny przy użyciu [w](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d7134-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="d7134-113">Zobacz [kowariancji i kontrawariancji](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="d7134-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|  
|`typename`|<span data-ttu-id="d7134-114">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d7134-114">Required.</span></span> <span data-ttu-id="d7134-115">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="d7134-115">Name of the type parameter.</span></span> <span data-ttu-id="d7134-116">Jest to symbol zastępczy, mają zostać zastąpione przez dostarczony przez odpowiedni argument typu zdefiniowanego typu.</span><span class="sxs-lookup"><span data-stu-id="d7134-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|  
|`constraintlist`|<span data-ttu-id="d7134-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d7134-117">Optional.</span></span> <span data-ttu-id="d7134-118">Listę wymagań, które ograniczenia typu danych, które mogą być dostarczane na potrzeby `typename`.</span><span class="sxs-lookup"><span data-stu-id="d7134-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="d7134-119">Jeśli masz wiele ograniczeń, należy ją ująć w nawiasy klamrowe (`{ }`) i je oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="d7134-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="d7134-120">Należy wprowadzić listę ograniczenie [jako](../../../visual-basic/language-reference/statements/as-clause.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d7134-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="d7134-121">Możesz użyć `As` tylko raz na początku listy.</span><span class="sxs-lookup"><span data-stu-id="d7134-121">You use `As` only once, at the beginning of the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7134-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7134-122">Remarks</span></span>  
 <span data-ttu-id="d7134-123">Każdy ogólnego elementu programistycznego, należy wykonać co najmniej jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="d7134-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="d7134-124">Parametr typu jest symbolem zastępczym dla określonego typu ( *element skonstruowany*) kod klienta określa, podczas tworzenia wystąpienia typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d7134-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="d7134-125">Można zdefiniować klasy ogólnej, struktury, interfejsu, procedury lub delegowanie.</span><span class="sxs-lookup"><span data-stu-id="d7134-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>  
  
 <span data-ttu-id="d7134-126">Aby uzyskać więcej informacji o tym, kiedy do definiowania typu ogólnego, zobacz [typów ogólnych w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="d7134-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="d7134-127">Aby uzyskać więcej informacji na temat nazwy parametrów typu, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d7134-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d7134-128">reguły</span><span class="sxs-lookup"><span data-stu-id="d7134-128">Rules</span></span>  
  
-   <span data-ttu-id="d7134-129">**Nawiasy.**</span><span class="sxs-lookup"><span data-stu-id="d7134-129">**Parentheses.**</span></span> <span data-ttu-id="d7134-130">Jeśli podasz lista parametrów typu, należy ją ująć w nawiasy i należy wprowadzić listę [z](../../../visual-basic/language-reference/statements/of-clause.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d7134-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="d7134-131">Możesz użyć `Of` tylko raz na początku listy.</span><span class="sxs-lookup"><span data-stu-id="d7134-131">You use `Of` only once, at the beginning of the list.</span></span>  
  
-   <span data-ttu-id="d7134-132">**Ograniczenia.**</span><span class="sxs-lookup"><span data-stu-id="d7134-132">**Constraints.**</span></span> <span data-ttu-id="d7134-133">Lista *ograniczenia* w danym typie parametr może zawierać następujące elementy w dowolnej kombinacji:</span><span class="sxs-lookup"><span data-stu-id="d7134-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>  
  
    -   <span data-ttu-id="d7134-134">Dowolną liczbę interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d7134-134">Any number of interfaces.</span></span> <span data-ttu-id="d7134-135">Dostarczony typ musi implementować każdy interfejs na tej liście.</span><span class="sxs-lookup"><span data-stu-id="d7134-135">The supplied type must implement every interface in this list.</span></span>  
  
    -   <span data-ttu-id="d7134-136">Co najwyżej jedną klasę.</span><span class="sxs-lookup"><span data-stu-id="d7134-136">At most one class.</span></span> <span data-ttu-id="d7134-137">Dostarczony typ musi dziedziczyć z tej klasy.</span><span class="sxs-lookup"><span data-stu-id="d7134-137">The supplied type must inherit from that class.</span></span>  
  
    -   <span data-ttu-id="d7134-138">`New` — Słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d7134-138">The `New` keyword.</span></span> <span data-ttu-id="d7134-139">Dostarczony typ musi ujawniać konstruktor bez parametrów, mogą uzyskiwać dostęp do danego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d7134-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="d7134-140">Jest to przydatne, jeśli ograniczenia parametru typu przez jeden lub więcej interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d7134-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="d7134-141">Typ, który implementuje interfejsy nie ujawnia konstruktora, a następnie w zależności od poziomu dostępu do konstruktora, kod w ramach ogólnego typu nie może być uzyskiwać do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="d7134-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>  
  
    -   <span data-ttu-id="d7134-142">Albo `Class` — słowo kluczowe lub `Structure` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d7134-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="d7134-143">`Class` — Słowo kluczowe ogranicza parametr typu ogólnego, aby wymagać wszystkich argumentów typu do niego być typem referencyjnym, na przykład ciąg, tablica lub delegata, lub obiekt utworzony z klasy.</span><span class="sxs-lookup"><span data-stu-id="d7134-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="d7134-144">`Structure` — Słowo kluczowe ogranicza parametr typu ogólnego, aby wszystkich argumentów typu do niego typ wartości, na przykład wpisz struktury, wyliczenia lub danych podstawowych.</span><span class="sxs-lookup"><span data-stu-id="d7134-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="d7134-145">Nie można uwzględnić jednocześnie `Class` i `Structure` w tym samym `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="d7134-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>  
  
     <span data-ttu-id="d7134-146">Dostarczony typ musi spełniać wymagania, co należy uwzględnić w `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="d7134-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>  
  
     <span data-ttu-id="d7134-147">Ograniczenia dotyczące każdego parametru typu są niezależne od ograniczenia dotyczące innych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="d7134-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="d7134-148">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="d7134-148">Behavior</span></span>  
  
-   <span data-ttu-id="d7134-149">**Podstawienia w czasie kompilacji.**</span><span class="sxs-lookup"><span data-stu-id="d7134-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="d7134-150">Po utworzeniu skonstruowanego typu od ogólnego elementu programistycznego podajesz zdefiniowanym typem dla każdego parametru typu.</span><span class="sxs-lookup"><span data-stu-id="d7134-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="d7134-151">Kompilator Visual Basic zastępuje podane typu każde wystąpienie `typename` w ramach ogólnego elementu.</span><span class="sxs-lookup"><span data-stu-id="d7134-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>  
  
-   <span data-ttu-id="d7134-152">**Brak ograniczeń.**</span><span class="sxs-lookup"><span data-stu-id="d7134-152">**Absence of Constraints.**</span></span> <span data-ttu-id="d7134-153">Jeśli nie określisz żadnych ograniczeń dla parametru typu, Twój kod jest ograniczona do operacji i obsługiwane przez elementy członkowskie [Object — typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md) dla tego parametru typu.</span><span class="sxs-lookup"><span data-stu-id="d7134-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7134-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7134-154">Example</span></span>  
 <span data-ttu-id="d7134-155">Poniższy przykład pokazuje szkielet definicji klasy generyczny słownik, w tym szkielet funkcję, aby dodać nowy wpis do słownika.</span><span class="sxs-lookup"><span data-stu-id="d7134-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>  
  
 [!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="d7134-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7134-156">Example</span></span>  
 <span data-ttu-id="d7134-157">Ponieważ `dictionary` jest ogólny, kod, który korzysta z niego można tworzyć wiele obiektów z niego, każdy mających taką samą funkcjonalność, ale na inny typ danych.</span><span class="sxs-lookup"><span data-stu-id="d7134-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="d7134-158">W poniższym przykładzie pokazano wiersz kodu, który tworzy `dictionary` obiekt z `String` wpisów i `Integer` kluczy.</span><span class="sxs-lookup"><span data-stu-id="d7134-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>  
  
 [!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="d7134-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7134-159">Example</span></span>  
 <span data-ttu-id="d7134-160">Poniższy przykład pokazuje równoważnych definicji szkielet wygenerowane w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d7134-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d7134-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7134-161">See also</span></span>

- [<span data-ttu-id="d7134-162">z</span><span class="sxs-lookup"><span data-stu-id="d7134-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="d7134-163">New, operator</span><span class="sxs-lookup"><span data-stu-id="d7134-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="d7134-164">Poziomy dostępu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7134-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="d7134-165">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="d7134-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="d7134-166">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d7134-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="d7134-167">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d7134-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="d7134-168">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d7134-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d7134-169">Instrukcje: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="d7134-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="d7134-170">Kowariancja i kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="d7134-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="d7134-171">W</span><span class="sxs-lookup"><span data-stu-id="d7134-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="d7134-172">limit</span><span class="sxs-lookup"><span data-stu-id="d7134-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
