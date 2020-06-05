---
title: Function, instrukcja
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
ms.openlocfilehash: 49cf4fead2c5594b7ac6815f82fea0dc995ea436
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404631"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="a60e8-102">Function — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a60e8-102">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="a60e8-103">Deklaruje nazwę, parametry i kod definiujący `Function` procedurę.</span><span class="sxs-lookup"><span data-stu-id="a60e8-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="a60e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a60e8-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="a60e8-105">Części</span><span class="sxs-lookup"><span data-stu-id="a60e8-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="a60e8-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a60e8-106">Optional.</span></span> <span data-ttu-id="a60e8-107">Zobacz [listę atrybutów](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="a60e8-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a60e8-108">Optional.</span></span> <span data-ttu-id="a60e8-109">Może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a60e8-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="a60e8-110">Społeczeństwo</span><span class="sxs-lookup"><span data-stu-id="a60e8-110">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="a60e8-111">Chronione</span><span class="sxs-lookup"><span data-stu-id="a60e8-111">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="a60e8-112">Osoby</span><span class="sxs-lookup"><span data-stu-id="a60e8-112">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="a60e8-113">Użytek</span><span class="sxs-lookup"><span data-stu-id="a60e8-113">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="a60e8-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="a60e8-114">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="a60e8-115">Prywatne chronione</span><span class="sxs-lookup"><span data-stu-id="a60e8-115">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="a60e8-116">Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="a60e8-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a60e8-117">Optional.</span></span> <span data-ttu-id="a60e8-118">Może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a60e8-118">Can be one of the following:</span></span>

  - [<span data-ttu-id="a60e8-119">Przeciążenia</span><span class="sxs-lookup"><span data-stu-id="a60e8-119">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="a60e8-120">Przesłonięcia</span><span class="sxs-lookup"><span data-stu-id="a60e8-120">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="a60e8-121">Overridable</span><span class="sxs-lookup"><span data-stu-id="a60e8-121">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="a60e8-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="a60e8-122">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="a60e8-123">MustOverride</span><span class="sxs-lookup"><span data-stu-id="a60e8-123">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="a60e8-124">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a60e8-124">Optional.</span></span> <span data-ttu-id="a60e8-125">Zobacz [udostępnianie](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-125">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="a60e8-126">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a60e8-126">Optional.</span></span> <span data-ttu-id="a60e8-127">Zobacz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-127">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="a60e8-128">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a60e8-128">Optional.</span></span> <span data-ttu-id="a60e8-129">Zobacz [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-129">See [Async](../modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="a60e8-130">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a60e8-130">Optional.</span></span> <span data-ttu-id="a60e8-131">Zobacz [iterator](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-131">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="a60e8-132">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a60e8-132">Required.</span></span> <span data-ttu-id="a60e8-133">Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="a60e8-133">Name of the procedure.</span></span> <span data-ttu-id="a60e8-134">Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-134">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="a60e8-135">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a60e8-135">Optional.</span></span> <span data-ttu-id="a60e8-136">Lista parametrów typu dla procedury ogólnej.</span><span class="sxs-lookup"><span data-stu-id="a60e8-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="a60e8-137">Zobacz [Lista typów](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-137">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="a60e8-138">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a60e8-138">Optional.</span></span> <span data-ttu-id="a60e8-139">Lista nazw zmiennych lokalnych reprezentujących parametry tej procedury.</span><span class="sxs-lookup"><span data-stu-id="a60e8-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="a60e8-140">Zobacz [listę parametrów](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-140">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="a60e8-141">Wymagane, jeśli `Option Strict` jest `On` .</span><span class="sxs-lookup"><span data-stu-id="a60e8-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="a60e8-142">Typ danych wartości zwracanej przez tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="a60e8-142">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="a60e8-143">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a60e8-143">Optional.</span></span> <span data-ttu-id="a60e8-144">Wskazuje, że ta procedura implementuje jedną lub więcej `Function` procedur, każda zdefiniowana w interfejsie implementowanym przez tę procedurę zawierającą klasę lub strukturę.</span><span class="sxs-lookup"><span data-stu-id="a60e8-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="a60e8-145">Zobacz [instrukcja Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-145">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="a60e8-146">Wymagane, jeśli `Implements` jest podany.</span><span class="sxs-lookup"><span data-stu-id="a60e8-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="a60e8-147">Lista `Function` implementowanych procedur.</span><span class="sxs-lookup"><span data-stu-id="a60e8-147">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="a60e8-148">Każda `implementedprocedure` z nich ma następującą składnię i części:</span><span class="sxs-lookup"><span data-stu-id="a60e8-148">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="a60e8-149">Część</span><span class="sxs-lookup"><span data-stu-id="a60e8-149">Part</span></span>|<span data-ttu-id="a60e8-150">Opis</span><span class="sxs-lookup"><span data-stu-id="a60e8-150">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="a60e8-151">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a60e8-151">Required.</span></span> <span data-ttu-id="a60e8-152">Nazwa interfejsu implementowanego przez tę procedurę zawierającą klasę lub strukturę.</span><span class="sxs-lookup"><span data-stu-id="a60e8-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="a60e8-153">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a60e8-153">Required.</span></span> <span data-ttu-id="a60e8-154">Nazwa, przez którą procedura jest zdefiniowana `interface` .</span><span class="sxs-lookup"><span data-stu-id="a60e8-154">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="a60e8-155">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a60e8-155">Optional.</span></span> <span data-ttu-id="a60e8-156">Wskazuje, że ta procedura może obsłużyć jedno lub więcej konkretnych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a60e8-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="a60e8-157">Zobacz [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-157">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="a60e8-158">Wymagane, jeśli `Handles` jest podany.</span><span class="sxs-lookup"><span data-stu-id="a60e8-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="a60e8-159">Lista zdarzeń, których dotyczy ta procedura.</span><span class="sxs-lookup"><span data-stu-id="a60e8-159">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="a60e8-160">Każda `eventspecifier` z nich ma następującą składnię i części:</span><span class="sxs-lookup"><span data-stu-id="a60e8-160">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="a60e8-161">Część</span><span class="sxs-lookup"><span data-stu-id="a60e8-161">Part</span></span>|<span data-ttu-id="a60e8-162">Opis</span><span class="sxs-lookup"><span data-stu-id="a60e8-162">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="a60e8-163">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a60e8-163">Required.</span></span> <span data-ttu-id="a60e8-164">Zmienna obiektu zadeklarowana z typem danych klasy lub struktury, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a60e8-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="a60e8-165">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a60e8-165">Required.</span></span> <span data-ttu-id="a60e8-166">Nazwa zdarzenia, którego dotyczy ta procedura.</span><span class="sxs-lookup"><span data-stu-id="a60e8-166">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="a60e8-167">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a60e8-167">Optional.</span></span> <span data-ttu-id="a60e8-168">Blok instrukcji do wykonania w ramach tej procedury.</span><span class="sxs-lookup"><span data-stu-id="a60e8-168">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="a60e8-169">Kończy definicję tej procedury.</span><span class="sxs-lookup"><span data-stu-id="a60e8-169">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="a60e8-170">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a60e8-170">Remarks</span></span>

<span data-ttu-id="a60e8-171">Cały kod wykonywalny musi znajdować się wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="a60e8-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="a60e8-172">Każda procedura z kolei jest zadeklarowana w obrębie klasy, struktury lub modułu, który jest nazywany klasą zawierającą, strukturą lub modułem.</span><span class="sxs-lookup"><span data-stu-id="a60e8-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="a60e8-173">Aby zwrócić wartość do kodu wywołującego, użyj `Function` procedury; w przeciwnym razie użyj `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="a60e8-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="a60e8-174">Definiowanie funkcji</span><span class="sxs-lookup"><span data-stu-id="a60e8-174">Defining a Function</span></span>

<span data-ttu-id="a60e8-175">Procedurę można zdefiniować `Function` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="a60e8-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="a60e8-176">W związku z tym kontekst deklaracji dla funkcji musi być klasą, strukturą, modułem lub interfejsem i nie może być plikiem źródłowym, przestrzenią nazw, procedurą lub blokiem.</span><span class="sxs-lookup"><span data-stu-id="a60e8-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="a60e8-177">Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="a60e8-178">`Function`procedury domyślne do dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="a60e8-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="a60e8-179">Możesz dostosować ich poziomy dostępu za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="a60e8-179">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="a60e8-180">`Function`Procedura może deklarować typ danych wartości zwracanej przez procedurę.</span><span class="sxs-lookup"><span data-stu-id="a60e8-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="a60e8-181">Można określić dowolny typ danych lub nazwę wyliczenia, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a60e8-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="a60e8-182">Jeśli parametr nie zostanie określony `returntype` , procedura zwróci wartość `Object` .</span><span class="sxs-lookup"><span data-stu-id="a60e8-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="a60e8-183">Jeśli ta procedura używa `Implements` słowa kluczowego, Klasa zawierająca lub struktura musi również mieć `Implements` instrukcję, która bezpośrednio następuje `Class` po `Structure` instrukcji or.</span><span class="sxs-lookup"><span data-stu-id="a60e8-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="a60e8-184">`Implements`Instrukcja musi zawierać wszystkie interfejsy, które są określone w `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="a60e8-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="a60e8-185">Jednak nazwa, za pomocą której interfejs definiuje `Function` (w), `definedname` nie musi być zgodna z nazwą tej procedury (w programie `name` ).</span><span class="sxs-lookup"><span data-stu-id="a60e8-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="a60e8-186">Można użyć wyrażeń lambda do definiowania wyrażeń funkcji w tekście.</span><span class="sxs-lookup"><span data-stu-id="a60e8-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="a60e8-187">Aby uzyskać więcej informacji, zobacz [wyrażenie funkcji](../operators/function-expression.md) i [wyrażenia lambda](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-187">For more information, see [Function Expression](../operators/function-expression.md) and [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="a60e8-188">Zwracanie z funkcji</span><span class="sxs-lookup"><span data-stu-id="a60e8-188">Returning from a Function</span></span>

<span data-ttu-id="a60e8-189">Gdy `Function` procedura zwraca kod wywołujący, wykonywanie jest kontynuowane za pomocą instrukcji, która następuje po instrukcji, która wywołała procedurę.</span><span class="sxs-lookup"><span data-stu-id="a60e8-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="a60e8-190">Aby zwrócić wartość z funkcji, można przypisać wartość do nazwy funkcji lub dołączyć ją do `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a60e8-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="a60e8-191">`Return`Instrukcja równocześnie przypisuje wartość zwracaną i opuszcza funkcję, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a60e8-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="a60e8-192">Poniższy przykład przypisuje wartość zwracaną do nazwy funkcji `myFunction` , a następnie używa `Exit Function` instrukcji do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="a60e8-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="a60e8-193">`Exit Function`Instrukcje i `Return` powodują natychmiastowe wyjście z `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="a60e8-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="a60e8-194">Dowolna liczba `Exit Function` `Return` instrukcji i może występować w dowolnym miejscu procedury i można mieszać i wypełniać `Exit Function` `Return` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="a60e8-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="a60e8-195">Jeśli używasz `Exit Function` bez przypisywania wartości do `name` , procedura zwraca wartość domyślną dla typu danych określonego w `returntype` .</span><span class="sxs-lookup"><span data-stu-id="a60e8-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="a60e8-196">Jeśli `returntype` nie jest określony, procedura zwraca `Nothing` wartość, która jest wartością domyślną dla `Object` .</span><span class="sxs-lookup"><span data-stu-id="a60e8-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="a60e8-197">Wywołanie funkcji</span><span class="sxs-lookup"><span data-stu-id="a60e8-197">Calling a Function</span></span>

<span data-ttu-id="a60e8-198">Procedurę można wywołać przy `Function` użyciu nazwy procedury, a następnie listy argumentów w nawiasach w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="a60e8-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="a60e8-199">Nawiasy można pominąć tylko wtedy, gdy nie podasz żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="a60e8-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="a60e8-200">Jednak kod jest bardziej czytelny, jeśli zawsze zawiera nawiasy.</span><span class="sxs-lookup"><span data-stu-id="a60e8-200">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="a60e8-201">Wywoływana jest `Function` procedura w taki sam sposób, jak w przypadku każdej funkcji biblioteki, takiej jak `Sqrt` , `Cos` lub `ChrW` .</span><span class="sxs-lookup"><span data-stu-id="a60e8-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="a60e8-202">Możesz również wywołać funkcję za pomocą `Call` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="a60e8-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="a60e8-203">W takim przypadku zwracana wartość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="a60e8-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="a60e8-204">Użycie `Call` słowa kluczowego nie jest zalecane w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="a60e8-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="a60e8-205">Aby uzyskać więcej informacji, zobacz [wywoływanie instrukcji](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-205">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="a60e8-206">Visual Basic czasami ponownie rozmieszcza wyrażenia arytmetyczne w celu zwiększenia wydajności wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="a60e8-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="a60e8-207">Z tego powodu nie należy używać `Function` procedury w wyrażeniu arytmetycznym, gdy funkcja zmienia wartość zmiennych w tym samym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="a60e8-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="a60e8-208">Funkcje asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="a60e8-208">Async Functions</span></span>

<span data-ttu-id="a60e8-209">Funkcja *Async* umożliwia wywoływanie funkcji asynchronicznych bez użycia jawnych wywołań zwrotnych lub Ręczne dzielenie kodu w wielu funkcjach lub wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="a60e8-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="a60e8-210">Jeśli oznaczesz funkcję z modyfikatorem [Async](../modifiers/async.md) , możesz użyć operatora [await](../operators/await-operator.md) w funkcji.</span><span class="sxs-lookup"><span data-stu-id="a60e8-210">If you mark a function with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="a60e8-211">Gdy kontrolka osiągnie `Await` wyrażenie w `Async` funkcji, sterowanie powraca do obiektu wywołującego, a postęp w funkcji jest zawieszony do momentu zakończenia zadania oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="a60e8-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="a60e8-212">Po zakończeniu zadania wykonywanie może zostać wznowione w funkcji.</span><span class="sxs-lookup"><span data-stu-id="a60e8-212">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="a60e8-213">`Async`Procedura powraca do obiektu wywołującego, gdy napotka on pierwszy oczekujący obiekt, który nie został jeszcze ukończony, lub otrzymuje koniec `Async` procedury, zależnie od tego, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="a60e8-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="a60e8-214">`Async`Funkcja może mieć zwracany typ <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="a60e8-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="a60e8-215">Przykład `Async` funkcji o zwracanym typie <xref:System.Threading.Tasks.Task%601> jest podany poniżej.</span><span class="sxs-lookup"><span data-stu-id="a60e8-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="a60e8-216">`Async`Funkcja nie może deklarować żadnych parametrów [ByRef](../modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="a60e8-216">An `Async` function cannot declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="a60e8-217">[Instrukcja sub](sub-statement.md) może być również oznaczona `Async` modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="a60e8-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="a60e8-218">Jest to używane głównie dla programów obsługi zdarzeń, w których nie można zwrócić wartości.</span><span class="sxs-lookup"><span data-stu-id="a60e8-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="a60e8-219">`Async` `Sub` Nie można oczekiwać procedury, a obiekt wywołujący `Async` `Sub` procedury nie może przechwytywać wyjątków, które są zgłaszane przez `Sub` procedurę.</span><span class="sxs-lookup"><span data-stu-id="a60e8-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="a60e8-220">Aby uzyskać więcej informacji na temat `Async` funkcji, zobacz [programowanie asynchroniczne z asynchroniczne i oczekujące](../../programming-guide/concepts/async/index.md), [przepływ sterowania w programach asynchronicznych](../../programming-guide/concepts/async/control-flow-in-async-programs.md)i [asynchroniczne typy zwracane](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="a60e8-221">Funkcje iteratora</span><span class="sxs-lookup"><span data-stu-id="a60e8-221">Iterator Functions</span></span>

<span data-ttu-id="a60e8-222">Funkcja *iteratora* wykonuje niestandardową iterację w kolekcji, na przykład listę lub tablicę.</span><span class="sxs-lookup"><span data-stu-id="a60e8-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="a60e8-223">Funkcja iteratora używa instrukcji [Yield](yield-statement.md) do zwrócenia każdego elementu w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="a60e8-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="a60e8-224">Po osiągnięciu instrukcji [Yield](yield-statement.md) bieżąca lokalizacja w kodzie jest zapamiętywana.</span><span class="sxs-lookup"><span data-stu-id="a60e8-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="a60e8-225">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="a60e8-225">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="a60e8-226">Należy wywołać iterator z kodu klienta przy użyciu [for each... Next](for-each-next-statement.md) — instrukcja.</span><span class="sxs-lookup"><span data-stu-id="a60e8-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="a60e8-227">Zwracanym typem funkcji iteratora może być <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> , lub <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="a60e8-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="a60e8-228">Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="a60e8-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="a60e8-229">Przykład</span><span class="sxs-lookup"><span data-stu-id="a60e8-229">Example</span></span>

<span data-ttu-id="a60e8-230">Poniższy przykład używa instrukcji, `Function` Aby zadeklarować nazwę, parametry i kod, który stanowi treść `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="a60e8-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="a60e8-231">`ParamArray`Modyfikator włącza funkcję, aby akceptować zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="a60e8-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="a60e8-232">Przykład</span><span class="sxs-lookup"><span data-stu-id="a60e8-232">Example</span></span>

<span data-ttu-id="a60e8-233">Poniższy przykład wywołuje funkcję zadeklarowaną w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a60e8-233">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="a60e8-234">Przykład</span><span class="sxs-lookup"><span data-stu-id="a60e8-234">Example</span></span>

<span data-ttu-id="a60e8-235">W poniższym przykładzie `DelayAsync` jest to, `Async` `Function` który ma zwracany typ <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="a60e8-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="a60e8-236">`DelayAsync`zawiera `Return` instrukcję zwracającą liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="a60e8-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="a60e8-237">W związku z tym deklaracja funkcji `DelayAsync` musi mieć typ zwracany `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="a60e8-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="a60e8-238">Ponieważ typem zwracanym jest `Task(Of Integer)` , obliczanie `Await` wyrażenia w `DoSomethingAsync` tworzy liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="a60e8-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="a60e8-239">Przedstawiono to w tej instrukcji: `Dim result As Integer = Await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="a60e8-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="a60e8-240">`startButton_Click`Procedura jest przykładem `Async Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="a60e8-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="a60e8-241">Ponieważ `DoSomethingAsync` jest `Async` funkcją, zadanie dla wywołania `DoSomethingAsync` musi być oczekiwane, jak pokazano w poniższej instrukcji: `Await DoSomethingAsync()` .</span><span class="sxs-lookup"><span data-stu-id="a60e8-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="a60e8-242">`startButton_Click` `Sub` Procedura musi być zdefiniowana z `Async` modyfikatorem, ponieważ ma `Await` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="a60e8-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="a60e8-243">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a60e8-243">See also</span></span>

- [<span data-ttu-id="a60e8-244">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a60e8-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="a60e8-245">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="a60e8-245">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="a60e8-246">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="a60e8-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="a60e8-247">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a60e8-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="a60e8-248">Call, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a60e8-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="a60e8-249">Z</span><span class="sxs-lookup"><span data-stu-id="a60e8-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="a60e8-250">Parameter — Tablice</span><span class="sxs-lookup"><span data-stu-id="a60e8-250">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="a60e8-251">Instrukcje: Używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="a60e8-251">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="a60e8-252">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="a60e8-252">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="a60e8-253">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="a60e8-253">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="a60e8-254">Wyrażenie funkcji</span><span class="sxs-lookup"><span data-stu-id="a60e8-254">Function Expression</span></span>](../operators/function-expression.md)
