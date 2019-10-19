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
ms.openlocfilehash: a0d489684b8f98e871211e6d0d95d42284275954
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582897"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="b9bf1-102">Lista typów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9bf1-102">Type List (Visual Basic)</span></span>

<span data-ttu-id="b9bf1-103">Określa *parametry typu* dla *ogólnego* elementu programistycznego.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="b9bf1-104">Wiele parametrów jest oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="b9bf1-105">Poniżej przedstawiono składnię dla jednego parametru typu.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-105">Following is the syntax for one type parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9bf1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9bf1-106">Syntax</span></span>

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a><span data-ttu-id="b9bf1-107">Części</span><span class="sxs-lookup"><span data-stu-id="b9bf1-107">Parts</span></span>

|<span data-ttu-id="b9bf1-108">Termin</span><span class="sxs-lookup"><span data-stu-id="b9bf1-108">Term</span></span>|<span data-ttu-id="b9bf1-109">Definicja</span><span class="sxs-lookup"><span data-stu-id="b9bf1-109">Definition</span></span>|
|---|---|
|`genericmodifier`|<span data-ttu-id="b9bf1-110">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-110">Optional.</span></span> <span data-ttu-id="b9bf1-111">Może być używany tylko w interfejsach ogólnych i delegatach.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="b9bf1-112">Można zadeklarować typ współvariant przy użyciu słowa kluczowego [out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) lub kontrawariantne za pomocą słowa kluczowego [in](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="b9bf1-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="b9bf1-113">Zobacz [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="b9bf1-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|
|`typename`|<span data-ttu-id="b9bf1-114">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-114">Required.</span></span> <span data-ttu-id="b9bf1-115">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-115">Name of the type parameter.</span></span> <span data-ttu-id="b9bf1-116">Jest to symbol zastępczy, który ma zostać zastąpiony przez zdefiniowany typ dostarczony przez odpowiedni argument typu.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|
|`constraintlist`|<span data-ttu-id="b9bf1-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-117">Optional.</span></span> <span data-ttu-id="b9bf1-118">Lista wymagań, które ograniczają typ danych, które można dostarczyć dla `typename`.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="b9bf1-119">W przypadku wielu ograniczeń należy ująć je w nawiasy klamrowe (`{ }`) i oddzielić je przecinkami.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="b9bf1-120">Należy wprowadzić listę ograniczeń za pomocą słowa kluczowego [as](../../../visual-basic/language-reference/statements/as-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="b9bf1-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="b9bf1-121">@No__t_0 można używać tylko raz, na początku listy.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-121">You use `As` only once, at the beginning of the list.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b9bf1-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9bf1-122">Remarks</span></span>

<span data-ttu-id="b9bf1-123">Każdy ogólny element programistyczny musi przyjmować co najmniej jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="b9bf1-124">Parametr typu jest symbolem zastępczym określonego typu ( *skonstruowany element*), który jest określany przez kod klienta podczas tworzenia wystąpienia typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="b9bf1-125">Istnieje możliwość zdefiniowania klasy ogólnej, struktury, interfejsu, procedury lub delegata.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>

<span data-ttu-id="b9bf1-126">Aby uzyskać więcej informacji na temat definiowania typu ogólnego, zobacz [typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="b9bf1-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="b9bf1-127">Aby uzyskać więcej informacji na temat nazw parametrów typu, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="b9bf1-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="rules"></a><span data-ttu-id="b9bf1-128">Przepisy</span><span class="sxs-lookup"><span data-stu-id="b9bf1-128">Rules</span></span>

- <span data-ttu-id="b9bf1-129">**Nawiasów.**</span><span class="sxs-lookup"><span data-stu-id="b9bf1-129">**Parentheses.**</span></span> <span data-ttu-id="b9bf1-130">W przypadku podania listy parametrów typu należy ująć ją w nawiasy i należy wprowadzić listę za [pomocą słowa](../../../visual-basic/language-reference/statements/of-clause.md) kluczowego.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="b9bf1-131">@No__t_0 można używać tylko raz, na początku listy.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-131">You use `Of` only once, at the beginning of the list.</span></span>

- <span data-ttu-id="b9bf1-132">**Powiązanych.**</span><span class="sxs-lookup"><span data-stu-id="b9bf1-132">**Constraints.**</span></span> <span data-ttu-id="b9bf1-133">Lista *ograniczeń* dla parametru typu może zawierać następujące elementy w dowolnej kombinacji:</span><span class="sxs-lookup"><span data-stu-id="b9bf1-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>

  - <span data-ttu-id="b9bf1-134">Dowolna liczba interfejsów.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-134">Any number of interfaces.</span></span> <span data-ttu-id="b9bf1-135">Dostarczony typ musi implementować każdy interfejs na tej liście.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-135">The supplied type must implement every interface in this list.</span></span>

  - <span data-ttu-id="b9bf1-136">Co najwyżej jedna Klasa.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-136">At most one class.</span></span> <span data-ttu-id="b9bf1-137">Dostarczony typ musi dziedziczyć po tej klasie.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-137">The supplied type must inherit from that class.</span></span>

  - <span data-ttu-id="b9bf1-138">Słowo kluczowe `New`.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-138">The `New` keyword.</span></span> <span data-ttu-id="b9bf1-139">Dostarczony typ musi ujawniać Konstruktor bez parametrów, który ma dostęp do typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="b9bf1-140">Jest to przydatne w przypadku ograniczenia parametru typu przez jeden lub więcej interfejsów.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="b9bf1-141">Typ, który implementuje interfejsy, niekoniecznie uwidacznia Konstruktor i w zależności od poziomu dostępu konstruktora, kod wewnątrz typu generycznego może nie być w stanie uzyskać do niego dostępu.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>

  - <span data-ttu-id="b9bf1-142">Słowo kluczowe `Class` lub słowo kluczowe `Structure`.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="b9bf1-143">Słowo kluczowe `Class` ogranicza parametr typu ogólnego, aby wymagało, aby każdy argument typu, który został przesłany do niego, był typem referencyjnym, na przykład ciągiem, tablicą lub delegatem lub obiektem utworzonym na podstawie klasy.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="b9bf1-144">Słowo kluczowe `Structure` ogranicza parametr typu ogólnego, aby wymagało, aby dowolny argument typu przekazał do niego typ wartości, na przykład strukturę, Wyliczenie lub typ danych podstawowych.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="b9bf1-145">W tym samym `constraintlist` nie można uwzględnić jednocześnie `Class` i `Structure`.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>

  <span data-ttu-id="b9bf1-146">Dostarczony typ musi spełniać każde wymaganie zawarte w `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>

  <span data-ttu-id="b9bf1-147">Ograniczenia dotyczące każdego parametru typu są niezależne od ograniczeń dla innych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>

## <a name="behavior"></a><span data-ttu-id="b9bf1-148">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="b9bf1-148">Behavior</span></span>

- <span data-ttu-id="b9bf1-149">**Podstawienie czasu kompilacji.**</span><span class="sxs-lookup"><span data-stu-id="b9bf1-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="b9bf1-150">Podczas tworzenia typu konstruowanego z generycznego elementu programistycznego, należy podać zdefiniowany typ dla każdego parametru typu.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="b9bf1-151">Kompilator Visual Basic zastępuje dostarczony typ dla każdego wystąpienia `typename` w elemencie ogólnym.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>

- <span data-ttu-id="b9bf1-152">**Brak ograniczeń.**</span><span class="sxs-lookup"><span data-stu-id="b9bf1-152">**Absence of Constraints.**</span></span> <span data-ttu-id="b9bf1-153">Jeśli nie określisz żadnych ograniczeń dla parametru typu, kod jest ograniczony do operacji i elementów członkowskich obsługiwanych przez [Typ danych obiektu](../../../visual-basic/language-reference/data-types/object-data-type.md) dla tego parametru typu.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="b9bf1-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9bf1-154">Example</span></span>

<span data-ttu-id="b9bf1-155">Poniższy przykład przedstawia definicję szkieletu klasy ogólnego słownika, w tym funkcję szkieletu, aby dodać nowy wpis do słownika.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a><span data-ttu-id="b9bf1-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9bf1-156">Example</span></span>

<span data-ttu-id="b9bf1-157">Ponieważ `dictionary` jest ogólny, kod, który używa go, może utworzyć wiele obiektów z niego, z których każdy ma te same funkcje, ale działa na innym typie danych.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="b9bf1-158">Poniższy przykład pokazuje wiersz kodu, który tworzy obiekt `dictionary` z wpisami `String` i kluczami `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a><span data-ttu-id="b9bf1-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9bf1-159">Example</span></span>

<span data-ttu-id="b9bf1-160">W poniższym przykładzie pokazano równoważną definicję szkieletu wygenerowaną w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b9bf1-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="b9bf1-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9bf1-161">See also</span></span>

- [<span data-ttu-id="b9bf1-162">Z</span><span class="sxs-lookup"><span data-stu-id="b9bf1-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="b9bf1-163">Operator New</span><span class="sxs-lookup"><span data-stu-id="b9bf1-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="b9bf1-164">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9bf1-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="b9bf1-165">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="b9bf1-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="b9bf1-166">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b9bf1-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="b9bf1-167">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b9bf1-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="b9bf1-168">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b9bf1-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="b9bf1-169">Instrukcje: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="b9bf1-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="b9bf1-170">Kowariancja i kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="b9bf1-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="b9bf1-171">Podczas</span><span class="sxs-lookup"><span data-stu-id="b9bf1-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="b9bf1-172">Określoną</span><span class="sxs-lookup"><span data-stu-id="b9bf1-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
