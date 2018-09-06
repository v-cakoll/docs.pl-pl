---
title: let — Powiązania (F#)
description: 'Dowiedz się, jak używać języka F # "let" powiązania, co umożliwi skojarzenie identyfikatora z wartością lub funkcji.'
ms.date: 05/16/2016
ms.openlocfilehash: 1a35b5a39f2768a18665b5c7fe768af0e7714577
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777473"
---
# <a name="let-bindings"></a><span data-ttu-id="8f65c-103">let — Powiązania</span><span class="sxs-lookup"><span data-stu-id="8f65c-103">let Bindings</span></span>

<span data-ttu-id="8f65c-104">A *powiązania* kojarzy identyfikator z wartością lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="8f65c-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="8f65c-105">Możesz użyć `let` — słowo kluczowe, aby powiązać nazwę wartości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="8f65c-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="8f65c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f65c-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="8f65c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f65c-107">Remarks</span></span>

<span data-ttu-id="8f65c-108">`let` Słowo kluczowe jest używane w powiązaniu wyrażeń do definiowania wartości lub wartości funkcji dla co najmniej jedną nazwę.</span><span class="sxs-lookup"><span data-stu-id="8f65c-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="8f65c-109">Najprostsza forma `let` wyrażenie wiąże nazwę prostej wartości w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="8f65c-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="8f65c-110">Jeśli oddzielisz wyrażenia z identyfikatorem przy użyciu nowego wiersza, należy utworzyć wcięcie każdego wiersza wyrażenie, tak jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8f65c-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="8f65c-111">Zamiast tylko nazwy, można określić wzorzec, który zawiera nazwy, na przykład spójna kolekcja, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8f65c-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="8f65c-112">*Wyrażenie treści* jest wyrażeniem, w którym są używane nazwy.</span><span class="sxs-lookup"><span data-stu-id="8f65c-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="8f65c-113">Wyrażenie treści pojawia się w osobnym wierszu wcięcia linii się dokładnie z pierwszego znaku w `let` — słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="8f65c-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="8f65c-114">A `let` powiązań mogą być wyświetlane na poziomie modułu w definicji typu klasy lub w lokalnych zakresów, takich jak definicja funkcji.</span><span class="sxs-lookup"><span data-stu-id="8f65c-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="8f65c-115">A `let` powiązania na najwyższym poziomie, modułu lub typu klasy nie musi zawierać wyrażenie treści, ale na innych poziomach zakresu wyrażenie treści jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="8f65c-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="8f65c-116">Powiązane są użyteczne po punkcie definicji, ale nie w dowolnym momencie przed `let` powiązania pojawi się, jak to pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8f65c-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a><span data-ttu-id="8f65c-117">Powiązania — funkcja</span><span class="sxs-lookup"><span data-stu-id="8f65c-117">Function Bindings</span></span>

<span data-ttu-id="8f65c-118">Powiązania funkcji postępuj zgodnie z reguły dla powiązania wartości, z tą różnicą, że funkcja powiązań obejmują nazwy funkcji i parametrów, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8f65c-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="8f65c-119">Ogólnie rzecz biorąc parametry są wzorców, takich jak wzorzec spójnej kolekcji:</span><span class="sxs-lookup"><span data-stu-id="8f65c-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="8f65c-120">A `let` powiązanie wyrażenie zwróci wartość ostatniego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="8f65c-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="8f65c-121">W związku z tym, w poniższym przykładzie kodu wartość `result` jest obliczany na podstawie `100 * function3 (1, 2)`, która daje w wyniku `300`.</span><span class="sxs-lookup"><span data-stu-id="8f65c-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="8f65c-122">Aby uzyskać więcej informacji, zobacz [funkcji](index.md).</span><span class="sxs-lookup"><span data-stu-id="8f65c-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="8f65c-123">Deklaracje typów</span><span class="sxs-lookup"><span data-stu-id="8f65c-123">Type Annotations</span></span>

<span data-ttu-id="8f65c-124">Można określić typy parametrów, umieszczając dwukropek (:), a następnie nazwę typu, wszystkie ujęty w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="8f65c-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="8f65c-125">Można również określić typ wartości zwracanej przez dołączenie dwukropek i typ po ostatnim parametrze.</span><span class="sxs-lookup"><span data-stu-id="8f65c-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="8f65c-126">Adnotacje pełny typ dla `function1`, za pomocą liczb całkowitych jako typy parametrów, należy użyć następującego.</span><span class="sxs-lookup"><span data-stu-id="8f65c-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="8f65c-127">Jeśli nie ma żadnych parametrów typu jawnego, wnioskowanie o typie umożliwia określić typy parametrów funkcji.</span><span class="sxs-lookup"><span data-stu-id="8f65c-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="8f65c-128">Może to obejmować automatyczne uogólnianie typ parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="8f65c-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="8f65c-129">Aby uzyskać więcej informacji, zobacz [automatyczna Generalizacja](../generics/automatic-generalization.md) i [wnioskowanie o typie](../type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="8f65c-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="8f65c-130">Powiązania let w klasach</span><span class="sxs-lookup"><span data-stu-id="8f65c-130">let Bindings in Classes</span></span>

<span data-ttu-id="8f65c-131">A `let` powiązań mogą być wyświetlane w typu klasy, ale nie w strukturze lub typie rekordu.</span><span class="sxs-lookup"><span data-stu-id="8f65c-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="8f65c-132">Aby użyć umożliwiają powiązania w typie klasy, klasy musi mieć konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="8f65c-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="8f65c-133">Parametry Konstruktora musi znajdować się po nazwie typu w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="8f65c-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="8f65c-134">A `let` powiązania w typie klasy definiuje pola prywatne i członków dla tego typu klasy, a wraz z `do` powiązania w typie formularzy kodu dla konstruktora podstawowego typu.</span><span class="sxs-lookup"><span data-stu-id="8f65c-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="8f65c-135">W poniższych przykładach kodu pokazano klasę `MyClass` za pomocą pola prywatne `field1` i `field2`.</span><span class="sxs-lookup"><span data-stu-id="8f65c-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="8f65c-136">Zakresy `field1` i `field2` są ograniczone do typu, w którym są one zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="8f65c-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="8f65c-137">Aby uzyskać więcej informacji, zobacz [ `let` powiązania w klasach](../members/let-bindings-in-classes.md) i [klasy](../classes.md).</span><span class="sxs-lookup"><span data-stu-id="8f65c-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="8f65c-138">Let — powiązania parametrów typu w</span><span class="sxs-lookup"><span data-stu-id="8f65c-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="8f65c-139">A `let` powiązania na poziomie modułu w typie lub w wyrażeniu obliczeń może mieć parametrów typu jawnego.</span><span class="sxs-lookup"><span data-stu-id="8f65c-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="8f65c-140">Let, powiązanie w wyrażeniu, takie jak w definicji funkcji, nie może mieć parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="8f65c-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="8f65c-141">Aby uzyskać więcej informacji, zobacz [ogólne](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="8f65c-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="8f65c-142">Atrybuty let — powiązania</span><span class="sxs-lookup"><span data-stu-id="8f65c-142">Attributes on let Bindings</span></span>

<span data-ttu-id="8f65c-143">Atrybuty mogą być stosowane do najwyższego poziomu `let` powiązania w module, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8f65c-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="8f65c-144">Zakres i dostępności powiązania Let</span><span class="sxs-lookup"><span data-stu-id="8f65c-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="8f65c-145">Zakres jednostki zadeklarowane za pomocą powiązania let jest ograniczony do części zawierający zakresu (na przykład funkcja modułu, plik lub klasy), po wyświetleniu powiązania.</span><span class="sxs-lookup"><span data-stu-id="8f65c-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="8f65c-146">W związku z tym można powiedzieć, że powiązania let wprowadza nazwę w zakresie.</span><span class="sxs-lookup"><span data-stu-id="8f65c-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="8f65c-147">W module wartość granicy umożliwiają lub funkcja jest dostępna dla klientów modułu tak długo, jak moduł jest niedostępna, ponieważ powiązania let w moduł są kompilowane do funkcji publicznych modułu.</span><span class="sxs-lookup"><span data-stu-id="8f65c-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="8f65c-148">Z drugiej strony powiązania let w klasie są prywatne do klasy.</span><span class="sxs-lookup"><span data-stu-id="8f65c-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="8f65c-149">Zwykle funkcje w modułach musi być kwalifikowana przez nazwę modułu, gdy jest używana przez kod klienta.</span><span class="sxs-lookup"><span data-stu-id="8f65c-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="8f65c-150">Na przykład, jeśli moduł `Module1` ma funkcję `function1`, należałoby określić użytkowników `Module1.function1` do odwoływania się do funkcji.</span><span class="sxs-lookup"><span data-stu-id="8f65c-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="8f65c-151">Użytkownicy modułu mogą skorzystać z deklaracji importu, aby udostępnić funkcje w ramach tego modułu do użycia nie jest kwalifikowana przez nazwę modułu.</span><span class="sxs-lookup"><span data-stu-id="8f65c-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="8f65c-152">W przykładzie powyżej, użytkownicy modułu można otworzyć w takim przypadku moduł przy użyciu open deklaracji importu `Module1` i po tej dacie odnoszą się do `function1` bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="8f65c-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

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

<span data-ttu-id="8f65c-153">Niektóre moduły mają atrybut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), co oznacza, że funkcje, które udostępniają musi być kwalifikowana z nazwą modułu.</span><span class="sxs-lookup"><span data-stu-id="8f65c-153">Some modules have the attribute [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="8f65c-154">Na przykład moduł F # listy ma tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8f65c-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="8f65c-155">Aby uzyskać więcej informacji na temat modułów i kontroli dostępu, zobacz [modułów](../modules.md) i [kontroli dostępu](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="8f65c-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f65c-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f65c-156">See also</span></span>

- [<span data-ttu-id="8f65c-157">Funkcje</span><span class="sxs-lookup"><span data-stu-id="8f65c-157">Functions</span></span>](index.md)
- [<span data-ttu-id="8f65c-158">`let` Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="8f65c-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
