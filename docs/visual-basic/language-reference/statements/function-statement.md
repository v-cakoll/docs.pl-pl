---
title: Function — Instrukcja (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: dffe67d1c31b0fe7c037839ba0588793a461f276
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638062"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="0be98-102">Function — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0be98-102">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="0be98-103">Deklaruje nazwę, parametry i kod, który definiuje `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="0be98-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="0be98-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0be98-104">Syntax</span></span>

```
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="0be98-105">Części</span><span class="sxs-lookup"><span data-stu-id="0be98-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="0be98-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0be98-106">Optional.</span></span> <span data-ttu-id="0be98-107">Zobacz [Lista atrybutów](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="0be98-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0be98-108">Optional.</span></span> <span data-ttu-id="0be98-109">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="0be98-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="0be98-110">Public</span><span class="sxs-lookup"><span data-stu-id="0be98-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

  - [<span data-ttu-id="0be98-111">Protected</span><span class="sxs-lookup"><span data-stu-id="0be98-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)

  - [<span data-ttu-id="0be98-112">Friend</span><span class="sxs-lookup"><span data-stu-id="0be98-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

  - [<span data-ttu-id="0be98-113">Private</span><span class="sxs-lookup"><span data-stu-id="0be98-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)

  - [<span data-ttu-id="0be98-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="0be98-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="0be98-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="0be98-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

  <span data-ttu-id="0be98-116">Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="0be98-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0be98-117">Optional.</span></span> <span data-ttu-id="0be98-118">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="0be98-118">Can be one of the following:</span></span>

  - [<span data-ttu-id="0be98-119">Overloads</span><span class="sxs-lookup"><span data-stu-id="0be98-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [<span data-ttu-id="0be98-120">Overrides</span><span class="sxs-lookup"><span data-stu-id="0be98-120">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [<span data-ttu-id="0be98-121">Overridable</span><span class="sxs-lookup"><span data-stu-id="0be98-121">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [<span data-ttu-id="0be98-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="0be98-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [<span data-ttu-id="0be98-123">MustOverride</span><span class="sxs-lookup"><span data-stu-id="0be98-123">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="0be98-124">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0be98-124">Optional.</span></span> <span data-ttu-id="0be98-125">Zobacz [udostępnione](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-125">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="0be98-126">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0be98-126">Optional.</span></span> <span data-ttu-id="0be98-127">Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-127">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="0be98-128">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0be98-128">Optional.</span></span> <span data-ttu-id="0be98-129">Zobacz [Async](../../../visual-basic/language-reference/modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-129">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="0be98-130">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0be98-130">Optional.</span></span> <span data-ttu-id="0be98-131">Zobacz [iteratora](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-131">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="0be98-132">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="0be98-132">Required.</span></span> <span data-ttu-id="0be98-133">Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="0be98-133">Name of the procedure.</span></span> <span data-ttu-id="0be98-134">Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="0be98-135">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0be98-135">Optional.</span></span> <span data-ttu-id="0be98-136">Lista parametrów typu ogólnego procedury.</span><span class="sxs-lookup"><span data-stu-id="0be98-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="0be98-137">Zobacz [Lista typów](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-137">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="0be98-138">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0be98-138">Optional.</span></span> <span data-ttu-id="0be98-139">Lista nazwy zmiennych lokalnych reprezentującą parametry tej procedury.</span><span class="sxs-lookup"><span data-stu-id="0be98-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="0be98-140">Zobacz [listy parametrów](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-140">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="0be98-141">Jeśli wymagane `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="0be98-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="0be98-142">Typ danych wartości zwracanej przez tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="0be98-142">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="0be98-143">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0be98-143">Optional.</span></span> <span data-ttu-id="0be98-144">Wskazuje, że ta procedura implementuje co najmniej jeden `Function` procedury, każdy z nich zdefiniowane w interfejsie zaimplementowany przez klasę lub strukturę zawierającego tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="0be98-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="0be98-145">Zobacz [Implements, instrukcja](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-145">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="0be98-146">Jeśli wymagane `Implements` podano.</span><span class="sxs-lookup"><span data-stu-id="0be98-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="0be98-147">Lista `Function` procedury są wdrożone.</span><span class="sxs-lookup"><span data-stu-id="0be98-147">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="0be98-148">Każdy `implementedprocedure` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="0be98-148">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="0be98-149">Część</span><span class="sxs-lookup"><span data-stu-id="0be98-149">Part</span></span>|<span data-ttu-id="0be98-150">Opis</span><span class="sxs-lookup"><span data-stu-id="0be98-150">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="0be98-151">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="0be98-151">Required.</span></span> <span data-ttu-id="0be98-152">Nazwa interfejsu implementowany przez tej procedury zawierający klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0be98-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="0be98-153">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="0be98-153">Required.</span></span> <span data-ttu-id="0be98-154">Nazwa, za pomocą którego procedura jest zdefiniowany w `interface`.</span><span class="sxs-lookup"><span data-stu-id="0be98-154">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="0be98-155">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0be98-155">Optional.</span></span> <span data-ttu-id="0be98-156">Wskazuje, że ta procedura może obsługiwać jeden lub więcej określonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0be98-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="0be98-157">Zobacz [obsługuje](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-157">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="0be98-158">Jeśli wymagane `Handles` podano.</span><span class="sxs-lookup"><span data-stu-id="0be98-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="0be98-159">Lista zdarzeń, które obsługuje tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="0be98-159">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="0be98-160">Każdy `eventspecifier` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="0be98-160">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="0be98-161">Część</span><span class="sxs-lookup"><span data-stu-id="0be98-161">Part</span></span>|<span data-ttu-id="0be98-162">Opis</span><span class="sxs-lookup"><span data-stu-id="0be98-162">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="0be98-163">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="0be98-163">Required.</span></span> <span data-ttu-id="0be98-164">Zmienna obiektu zadeklarowane z typem danych klasy lub struktury, która wywołuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0be98-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="0be98-165">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="0be98-165">Required.</span></span> <span data-ttu-id="0be98-166">Nazwa zdarzenia, które obsługuje tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="0be98-166">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="0be98-167">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0be98-167">Optional.</span></span> <span data-ttu-id="0be98-168">Blok instrukcji do wykonania w ramach tej procedury.</span><span class="sxs-lookup"><span data-stu-id="0be98-168">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="0be98-169">Kończy definicję tej procedury.</span><span class="sxs-lookup"><span data-stu-id="0be98-169">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="0be98-170">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0be98-170">Remarks</span></span>

<span data-ttu-id="0be98-171">Cały kod wykonywalny musi być wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="0be98-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="0be98-172">Każdej procedury z kolei jest zadeklarowana w obrębie klasy, struktury lub modułu, który jest określany jako zawierającego klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="0be98-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="0be98-173">Aby zwrócić wartości do kodu wywołującego, użyj `Function` procedury; w przeciwnym razie użyj `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="0be98-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="0be98-174">Definiowanie funkcji</span><span class="sxs-lookup"><span data-stu-id="0be98-174">Defining a Function</span></span>

<span data-ttu-id="0be98-175">Można zdefiniować `Function` procedury tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="0be98-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="0be98-176">W związku z tym kontekst deklaracji funkcji musi być klasy, struktury, modułem lub interfejsem, a nie może być plikiem źródłowym, przestrzeń nazw, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="0be98-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="0be98-177">Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="0be98-178">`Function` Domyślnie procedur dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="0be98-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="0be98-179">Poziomy dostępu można zmienić za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="0be98-179">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="0be98-180">A `Function` procedury można zadeklarować typ danych wartości, która zwraca procedury.</span><span class="sxs-lookup"><span data-stu-id="0be98-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="0be98-181">Można określić dowolny typ danych lub nazwa wyliczenia, strukturę, klasę lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="0be98-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="0be98-182">Jeśli nie określisz `returntype` parametr, procedura zwraca `Object`.</span><span class="sxs-lookup"><span data-stu-id="0be98-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="0be98-183">Jeśli ta procedura wykorzystuje `Implements` — słowo kluczowe, zawierający klasy lub struktury, również musi mieć `Implements` instrukcji, który następuje bezpośrednio po jego `Class` lub `Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0be98-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="0be98-184">`Implements` Instrukcja musi zawierać każdego interfejsu, który jest określony w `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="0be98-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="0be98-185">Jednak nazwy za pomocą którego interfejs definiuje `Function` (w `definedname`) nie musi być zgodna z nazwą w tej procedurze (w `name`).</span><span class="sxs-lookup"><span data-stu-id="0be98-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="0be98-186">Można użyć wyrażenia lambda do definiowania wbudowane wyrażenia funkcji.</span><span class="sxs-lookup"><span data-stu-id="0be98-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="0be98-187">Aby uzyskać więcej informacji, zobacz [Function — wyrażenie](../../../visual-basic/language-reference/operators/function-expression.md) i [wyrażeń Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-187">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="0be98-188">Zwracanie z funkcji</span><span class="sxs-lookup"><span data-stu-id="0be98-188">Returning from a Function</span></span>

<span data-ttu-id="0be98-189">Gdy `Function` procedury zwraca do kodu wywołującego, wykonywanie jest kontynuowane przy użyciu instrukcji, która następuje po instrukcji, która wywołuje procedurę.</span><span class="sxs-lookup"><span data-stu-id="0be98-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="0be98-190">Aby zwrócić wartości z funkcji, można przypisać wartość do nazwy funkcji lub uwzględnić go w `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0be98-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="0be98-191">`Return` Instrukcji jednocześnie przypisuje wartość zwracaną i kończy działanie funkcji, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="0be98-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="0be98-192">Poniższy przykład przypisuje wartość zwracaną do nazwy funkcji `myFunction` , a następnie używa `Exit Function` instrukcji, aby zwrócić.</span><span class="sxs-lookup"><span data-stu-id="0be98-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="0be98-193">`Exit Function` i `Return` instrukcji powodują natychmiastowego wyjścia z `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="0be98-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="0be98-194">Dowolną liczbę `Exit Function` i `Return` instrukcji może występować w dowolnym miejscu w ramach procedury i możesz mieszać `Exit Function` i `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0be98-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="0be98-195">Jeśli używasz `Exit Function` bez przypisywania wartości do `name`, procedura zwraca wartość domyślna dla typu danych, który jest określony w `returntype`.</span><span class="sxs-lookup"><span data-stu-id="0be98-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="0be98-196">Jeśli `returntype` nie jest określona, zwraca procedury `Nothing`, która jest wartością domyślną dla `Object`.</span><span class="sxs-lookup"><span data-stu-id="0be98-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="0be98-197">Wywołanie funkcji</span><span class="sxs-lookup"><span data-stu-id="0be98-197">Calling a Function</span></span>

<span data-ttu-id="0be98-198">Należy wywołać `Function` procedury przy użyciu nazwy procedury, następuje lista argumentów w nawiasach w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="0be98-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="0be98-199">Nawiasy można pominąć, tylko wtedy, gdy nie udostępnia żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="0be98-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="0be98-200">Jednak kod jest bardziej czytelny, jeśli zawsze zawierać nawiasy.</span><span class="sxs-lookup"><span data-stu-id="0be98-200">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="0be98-201">Należy wywołać `Function` procedury taki sam sposób, że wywołać każdą bibliotekę funkcji, takich jak `Sqrt`, `Cos`, lub `ChrW`.</span><span class="sxs-lookup"><span data-stu-id="0be98-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="0be98-202">Można również wywołać funkcję za pomocą `Call` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="0be98-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="0be98-203">W takim przypadku zwracana wartość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="0be98-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="0be98-204">Korzystanie z `Call` — słowo kluczowe nie jest zalecane w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="0be98-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="0be98-205">Aby uzyskać więcej informacji, zobacz [instrukcji Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-205">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="0be98-206">Visual Basic Reorganizuje czasami wyrażenia arytmetyczne, aby zwiększyć wydajność wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="0be98-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="0be98-207">Z tego powodu nie można używać `Function` procedury w wyrażeniach arytmetycznych funkcja zmianę wartości zmiennych w jednym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="0be98-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="0be98-208">Funkcje asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="0be98-208">Async Functions</span></span>

<span data-ttu-id="0be98-209">*Async* pozwala wywoływać funkcje asynchroniczne bez za pomocą jawnego wywołania zwrotne lub ręcznego podziału kodu na wielu funkcji lub wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="0be98-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="0be98-210">Po oznaczeniu funkcji z [Async](../../../visual-basic/language-reference/modifiers/async.md) modyfikator, można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w funkcji.</span><span class="sxs-lookup"><span data-stu-id="0be98-210">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="0be98-211">Gdy kontrola osiąga `Await` wyrażenia w `Async` funkcji, sterowanie powraca do obiektu wywołującego, a postęp w funkcji jest wstrzymana, dopóki nie zakończy się oczekiwane zadanie.</span><span class="sxs-lookup"><span data-stu-id="0be98-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="0be98-212">Kiedy zadanie zostanie ukończone, wykonanie można wznowić w funkcji.</span><span class="sxs-lookup"><span data-stu-id="0be98-212">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="0be98-213">`Async` Po albo napotka pierwszego oczekiwane obiekt, który nie został jeszcze ukończony procedury powraca do obiektu wywołującego lub pobiera na końcu `Async` procedury, w zależności od tego nastąpi pierwsze.</span><span class="sxs-lookup"><span data-stu-id="0be98-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="0be98-214">`Async` Funkcji może mieć typ zwracany <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="0be98-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="0be98-215">Przykładem `Async` funkcję, która ma typ zwracany <xref:System.Threading.Tasks.Task%601> znajduje się poniżej.</span><span class="sxs-lookup"><span data-stu-id="0be98-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="0be98-216">`Async` Funkcji nie może deklarować [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametrów.</span><span class="sxs-lookup"><span data-stu-id="0be98-216">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="0be98-217">A [Sub — instrukcja](sub-statement.md) również mogą być oznaczone `Async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="0be98-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="0be98-218">To jest używany głównie dla procedury obsługi zdarzeń, których nie można zwrócić wartość.</span><span class="sxs-lookup"><span data-stu-id="0be98-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="0be98-219">`Async` `Sub` Procedura nie może być oczekiwany, a obiekt wywołujący `Async` `Sub` procedura nie może przechwytywać wyjątki wyrzucane przez `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="0be98-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="0be98-220">Aby uzyskać więcej informacji na temat `Async` funkcji, zobacz [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="0be98-221">Funkcje iteratora</span><span class="sxs-lookup"><span data-stu-id="0be98-221">Iterator Functions</span></span>

<span data-ttu-id="0be98-222">*Iteratora* funkcja wykonuje niestandardowych iteracji w kolekcji, takie jak listy lub tablicy.</span><span class="sxs-lookup"><span data-stu-id="0be98-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="0be98-223">Używa funkcji iteratora [uzyskanie](yield-statement.md) instrukcja zwraca każdy element w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="0be98-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="0be98-224">Gdy [uzyskanie](yield-statement.md) osiągnięciu instrukcji zapamiętanych bieżąca lokalizacja w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0be98-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="0be98-225">Wykonanie jest uruchamiane ponownie z tej lokalizacji w następnym razem, gdy zostanie wywołana funkcja iteratora.</span><span class="sxs-lookup"><span data-stu-id="0be98-225">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="0be98-226">Wywołujesz iterację z poziomu kodu klienta przy użyciu [For Each... Następny](for-each-next-statement.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0be98-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="0be98-227">Może być zwracany typ funkcji iteratora <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="0be98-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="0be98-228">Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="0be98-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="0be98-229">Przykład</span><span class="sxs-lookup"><span data-stu-id="0be98-229">Example</span></span>

<span data-ttu-id="0be98-230">W poniższym przykładzie użyto `Function` instrukcję, aby zadeklarować nazwę, parametry i kod, który tworzą treści `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="0be98-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="0be98-231">`ParamArray` Modyfikator umożliwia funkcji zaakceptować zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="0be98-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="0be98-232">Przykład</span><span class="sxs-lookup"><span data-stu-id="0be98-232">Example</span></span>

<span data-ttu-id="0be98-233">Poniższy przykład przedstawia wywoływanie funkcji zadeklarowanej w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0be98-233">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="0be98-234">Przykład</span><span class="sxs-lookup"><span data-stu-id="0be98-234">Example</span></span>

<span data-ttu-id="0be98-235">W poniższym przykładzie `DelayAsync` jest `Async` `Function` zawierający typ zwracany <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="0be98-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="0be98-236">`DelayAsync` ma `Return` instrukcję, która zwraca liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="0be98-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="0be98-237">W związku z tym funkcja deklaracji `DelayAsync` musi mieć typ zwracany `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="0be98-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="0be98-238">Ponieważ typem zwracanym jest `Task(Of Integer)`, oceny `Await` wyrażenia w `DoSomethingAsync` tworzy liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="0be98-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="0be98-239">Zostało to przedstawione w tej instrukcji: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="0be98-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="0be98-240">`startButton_Click` Procedura to przykład `Async Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="0be98-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="0be98-241">Ponieważ `DoSomethingAsync` jest `Async` funkcji, zadanie do wywołań `DoSomethingAsync` musi być oczekiwana, tak jak pokazano w następującej instrukcji: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="0be98-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="0be98-242">`startButton_Click` `Sub` Procedury muszą być zdefiniowane przy użyciu `Async` modyfikator ponieważ ma ona `Await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="0be98-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="0be98-243">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0be98-243">See also</span></span>

- [<span data-ttu-id="0be98-244">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0be98-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="0be98-245">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="0be98-245">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="0be98-246">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="0be98-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="0be98-247">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0be98-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="0be98-248">Call, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0be98-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="0be98-249">z</span><span class="sxs-lookup"><span data-stu-id="0be98-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="0be98-250">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="0be98-250">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="0be98-251">Instrukcje: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="0be98-251">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="0be98-252">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="0be98-252">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="0be98-253">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="0be98-253">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="0be98-254">Function, wyrażenie</span><span class="sxs-lookup"><span data-stu-id="0be98-254">Function Expression</span></span>](../../../visual-basic/language-reference/operators/function-expression.md)
