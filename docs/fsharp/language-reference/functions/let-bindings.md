---
title: let — Powiązania
description: Dowiedz się, jak F# używać powiązania "let", które kojarzy identyfikator z wartością lub funkcją.
ms.date: 05/16/2016
ms.openlocfilehash: 654631c7d1c48d8737e6098c98efee54cfdd91be
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630640"
---
# <a name="let-bindings"></a><span data-ttu-id="90fb4-103">let — Powiązania</span><span class="sxs-lookup"><span data-stu-id="90fb4-103">let Bindings</span></span>

<span data-ttu-id="90fb4-104">*Powiązanie* kojarzy identyfikator z wartością lub funkcją.</span><span class="sxs-lookup"><span data-stu-id="90fb4-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="90fb4-105">Użyj słowa kluczowego, `let` aby powiązać nazwę z wartością lub funkcją.</span><span class="sxs-lookup"><span data-stu-id="90fb4-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="90fb4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="90fb4-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="90fb4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90fb4-107">Remarks</span></span>

<span data-ttu-id="90fb4-108">`let` Słowo kluczowe jest używane w wyrażeniach wiązania do definiowania wartości lub wartości funkcji dla co najmniej jednej nazwy.</span><span class="sxs-lookup"><span data-stu-id="90fb4-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="90fb4-109">Najprostsza forma `let` wyrażenia wiąże nazwę z prostą wartością w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="90fb4-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="90fb4-110">Jeśli wyrażenie jest oddzielane od identyfikatora przy użyciu nowego wiersza, należy wciąć każdy wiersz wyrażenia, tak jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="90fb4-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="90fb4-111">Zamiast tylko nazwy, wzorzec zawierający nazwy można określić na przykład krotka, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="90fb4-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="90fb4-112">*Wyrażenie Body* jest wyrażeniem, w którym są używane nazwy.</span><span class="sxs-lookup"><span data-stu-id="90fb4-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="90fb4-113">Wyrażenie treści jest wyświetlane w osobnym wierszu, wcięcie w celu podzielenia dokładnie z pierwszym znakiem `let` słowa kluczowego:</span><span class="sxs-lookup"><span data-stu-id="90fb4-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="90fb4-114">`let` Powiązanie może być wyświetlane na poziomie modułu, w definicji typu klasy lub w lokalnych zakresach, takich jak w definicji funkcji.</span><span class="sxs-lookup"><span data-stu-id="90fb4-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="90fb4-115">`let` Powiązanie na najwyższym poziomie modułu lub w typie klasy nie musi mieć wyrażenia Body, ale na innych poziomach zakresu wyrażenie treści jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="90fb4-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="90fb4-116">Nazwy powiązane są użyteczne po punkcie definicji, ale nie w żadnym punkcie przed `let` wyświetleniem powiązania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="90fb4-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a><span data-ttu-id="90fb4-117">Powiązania funkcji</span><span class="sxs-lookup"><span data-stu-id="90fb4-117">Function Bindings</span></span>

<span data-ttu-id="90fb4-118">Powiązania funkcji są zgodne z regułami dotyczącymi powiązań wartości, z tą różnicą, że powiązania funkcji zawierają nazwę funkcji i parametry, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="90fb4-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="90fb4-119">Ogólnie rzecz biorąc, parametry są wzorcami, takimi jak wzorzec krotki:</span><span class="sxs-lookup"><span data-stu-id="90fb4-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="90fb4-120">Wyrażenie `let` powiązania daje w wyniku wartość ostatniego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="90fb4-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="90fb4-121">W związku z tym, w poniższym przykładzie kodu, wartość `result` jest obliczana z `100 * function3 (1, 2)` `300`, która daje w wyniku.</span><span class="sxs-lookup"><span data-stu-id="90fb4-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="90fb4-122">Aby uzyskać więcej informacji, zobacz [funkcji](index.md).</span><span class="sxs-lookup"><span data-stu-id="90fb4-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="90fb4-123">Adnotacje typu</span><span class="sxs-lookup"><span data-stu-id="90fb4-123">Type Annotations</span></span>

<span data-ttu-id="90fb4-124">Można określić typy parametrów, dołączając dwukropek (:) po którym następuje nazwa typu, wszystkie zawarte w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="90fb4-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="90fb4-125">Można również określić typ wartości zwracanej przez dołączenie dwukropka i typu po ostatnim parametrze.</span><span class="sxs-lookup"><span data-stu-id="90fb4-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="90fb4-126">Pełne adnotacje typu dla `function1`, z liczbami całkowitymi jako typy parametrów, byłyby następujące.</span><span class="sxs-lookup"><span data-stu-id="90fb4-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="90fb4-127">Jeśli nie ma żadnych jawnych parametrów typu, wnioskowanie typu jest używane do określenia typów parametrów funkcji.</span><span class="sxs-lookup"><span data-stu-id="90fb4-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="90fb4-128">Może to obejmować automatyczne uogólnianie typu parametru, który ma być ogólny.</span><span class="sxs-lookup"><span data-stu-id="90fb4-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="90fb4-129">Aby uzyskać więcej informacji, zobacz [Automatyczne uogólnianie](../generics/automatic-generalization.md) i wnioskowanie o [typie](../type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="90fb4-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="90fb4-130">Powiązania let w klasach</span><span class="sxs-lookup"><span data-stu-id="90fb4-130">let Bindings in Classes</span></span>

<span data-ttu-id="90fb4-131">`let` Powiązanie może pojawić się w typie klasy, ale nie w typie struktury lub rekordu.</span><span class="sxs-lookup"><span data-stu-id="90fb4-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="90fb4-132">Aby można było użyć powiązania let w typie klasy, Klasa musi mieć konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="90fb4-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="90fb4-133">Parametry konstruktora muszą występować po nazwie typu w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="90fb4-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="90fb4-134">Powiązanie w typie klasy definiuje prywatne pola i elementy członkowskie dla tego typu klasy oraz, wraz z `do` powiązaniami w typie, tworzy kod dla głównego konstruktora typu. `let`</span><span class="sxs-lookup"><span data-stu-id="90fb4-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="90fb4-135">Poniższe przykłady kodu przedstawiają klasę `MyClass` z polami `field1` prywatnymi i `field2`.</span><span class="sxs-lookup"><span data-stu-id="90fb4-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="90fb4-136">Zakresy `field1` i`field2` są ograniczone do typu, w którym są zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="90fb4-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="90fb4-137">Aby uzyskać więcej informacji, zobacz [ `let` powiązania w klasach](../members/let-bindings-in-classes.md) i [klasach](../classes.md).</span><span class="sxs-lookup"><span data-stu-id="90fb4-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="90fb4-138">Parametry typu w programie Let bindings</span><span class="sxs-lookup"><span data-stu-id="90fb4-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="90fb4-139">`let` Powiązanie na poziomie modułu, w typie lub w wyrażeniu obliczeniowym może mieć jawne parametry typu.</span><span class="sxs-lookup"><span data-stu-id="90fb4-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="90fb4-140">Powiązanie let w wyrażeniu, takie jak w definicji funkcji, nie może mieć parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="90fb4-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="90fb4-141">Aby uzyskać więcej informacji, zobacz [Ogólne](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="90fb4-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="90fb4-142">Atrybuty dla powiązań Let</span><span class="sxs-lookup"><span data-stu-id="90fb4-142">Attributes on let Bindings</span></span>

<span data-ttu-id="90fb4-143">Atrybuty mogą być stosowane do powiązań najwyższego poziomu `let` w module, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="90fb4-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="90fb4-144">Zakres i dostępność powiązań Let</span><span class="sxs-lookup"><span data-stu-id="90fb4-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="90fb4-145">Zakres jednostki zadeklarowanej za pomocą powiązania Let jest ograniczony do części zawierającego ją zakresu (na przykład funkcji, modułu, pliku lub klasy) po wyświetleniu powiązania.</span><span class="sxs-lookup"><span data-stu-id="90fb4-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="90fb4-146">W związku z tym może być uważany, że powiązanie Let wprowadza nazwę do zakresu.</span><span class="sxs-lookup"><span data-stu-id="90fb4-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="90fb4-147">W module, wartość lub funkcja, którą można powiązać, jest dostępna dla klientów modułu, o ile moduł jest dostępny, ponieważ powiązania let w module są kompilowane do funkcji publicznych modułu.</span><span class="sxs-lookup"><span data-stu-id="90fb4-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="90fb4-148">Z kolei należy zezwolić na powiązania w klasie z klasą.</span><span class="sxs-lookup"><span data-stu-id="90fb4-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="90fb4-149">Zwykle funkcje w modułach muszą być kwalifikowane według nazwy modułu, gdy są używane przez kod klienta.</span><span class="sxs-lookup"><span data-stu-id="90fb4-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="90fb4-150">Na przykład jeśli moduł `Module1` zawiera funkcję `function1`, użytkownicy mogą `Module1.function1` odwoływać się do funkcji.</span><span class="sxs-lookup"><span data-stu-id="90fb4-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="90fb4-151">Użytkownicy modułu mogą używać deklaracji importu, aby udostępnić funkcje w ramach tego modułu bez zakwalifikowania nazwy modułu.</span><span class="sxs-lookup"><span data-stu-id="90fb4-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="90fb4-152">W takim przykładzie użytkownicy modułu mogą w tym przypadku otworzyć moduł przy użyciu otwartej `Module1` deklaracji import, a następnie odwołać się bezpośrednio do `function1` niego.</span><span class="sxs-lookup"><span data-stu-id="90fb4-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

<span data-ttu-id="90fb4-153">Niektóre moduły mają atrybut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), co oznacza, że funkcje, które uwidaczniają, muszą być kwalifikowane przy użyciu nazwy modułu.</span><span class="sxs-lookup"><span data-stu-id="90fb4-153">Some modules have the attribute [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="90fb4-154">Na przykład moduł F# listy ma ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="90fb4-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="90fb4-155">Aby uzyskać więcej informacji na temat modułów i kontroli dostępu, zobacz [moduły](../modules.md) i [Access Control](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="90fb4-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="90fb4-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90fb4-156">See also</span></span>

- [<span data-ttu-id="90fb4-157">Funkcje</span><span class="sxs-lookup"><span data-stu-id="90fb4-157">Functions</span></span>](index.md)
- [<span data-ttu-id="90fb4-158">`let`Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="90fb4-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
