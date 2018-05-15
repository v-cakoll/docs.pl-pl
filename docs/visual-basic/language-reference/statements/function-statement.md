---
title: Function — Instrukcja (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: b4a0c33d6d466975ca5dde1bd20ad2e1a9f560e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="d63bc-102">Function — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d63bc-102">Function Statement (Visual Basic)</span></span>
<span data-ttu-id="d63bc-103">Deklaruje nazwę, parametry i kod, który definiuje `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="d63bc-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d63bc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d63bc-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="d63bc-105">Części</span><span class="sxs-lookup"><span data-stu-id="d63bc-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="d63bc-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d63bc-106">Optional.</span></span> <span data-ttu-id="d63bc-107">Zobacz temat [Lista atrybutów](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="d63bc-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d63bc-108">Optional.</span></span> <span data-ttu-id="d63bc-109">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="d63bc-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="d63bc-110">Public</span><span class="sxs-lookup"><span data-stu-id="d63bc-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="d63bc-111">Protected</span><span class="sxs-lookup"><span data-stu-id="d63bc-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="d63bc-112">Friend</span><span class="sxs-lookup"><span data-stu-id="d63bc-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="d63bc-113">Private</span><span class="sxs-lookup"><span data-stu-id="d63bc-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="d63bc-114">Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-114">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="d63bc-115">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d63bc-115">Optional.</span></span> <span data-ttu-id="d63bc-116">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="d63bc-116">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="d63bc-117">Overloads</span><span class="sxs-lookup"><span data-stu-id="d63bc-117">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="d63bc-118">Overrides</span><span class="sxs-lookup"><span data-stu-id="d63bc-118">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="d63bc-119">Overridable</span><span class="sxs-lookup"><span data-stu-id="d63bc-119">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="d63bc-120">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="d63bc-120">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="d63bc-121">MustOverride</span><span class="sxs-lookup"><span data-stu-id="d63bc-121">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="d63bc-122">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d63bc-122">Optional.</span></span> <span data-ttu-id="d63bc-123">Zobacz [udostępnionych](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-123">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="d63bc-124">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d63bc-124">Optional.</span></span> <span data-ttu-id="d63bc-125">Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-125">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="d63bc-126">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d63bc-126">Optional.</span></span> <span data-ttu-id="d63bc-127">Zobacz [Async](../../../visual-basic/language-reference/modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-127">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="d63bc-128">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d63bc-128">Optional.</span></span> <span data-ttu-id="d63bc-129">Zobacz [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-129">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="d63bc-130">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d63bc-130">Required.</span></span> <span data-ttu-id="d63bc-131">Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="d63bc-131">Name of the procedure.</span></span> <span data-ttu-id="d63bc-132">Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-132">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="d63bc-133">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d63bc-133">Optional.</span></span> <span data-ttu-id="d63bc-134">Lista parametrów typu ogólnego procedurę.</span><span class="sxs-lookup"><span data-stu-id="d63bc-134">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="d63bc-135">Zobacz [typu listy](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-135">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="d63bc-136">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d63bc-136">Optional.</span></span> <span data-ttu-id="d63bc-137">Lista nazwy zmiennych lokalnych reprezentujący parametry tej procedury.</span><span class="sxs-lookup"><span data-stu-id="d63bc-137">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="d63bc-138">Zobacz [listy parametrów](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-138">See [Parameter List](parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="d63bc-139">Jeśli wymagane `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="d63bc-139">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="d63bc-140">Typ danych wartości zwracanej przez tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="d63bc-140">Data type of the value returned by this procedure.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="d63bc-141">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d63bc-141">Optional.</span></span> <span data-ttu-id="d63bc-142">Wskazuje, że ta procedura implementuje co najmniej jeden `Function` procedur, każdą z nich zdefiniowane w interfejsie zaimplementowany przez klasę lub strukturę zawierającego tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="d63bc-142">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="d63bc-143">Zobacz [implementuje instrukcji](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-143">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="d63bc-144">Jeśli wymagane `Implements` podano.</span><span class="sxs-lookup"><span data-stu-id="d63bc-144">Required if `Implements` is supplied.</span></span> <span data-ttu-id="d63bc-145">Lista `Function` procedury implementowana.</span><span class="sxs-lookup"><span data-stu-id="d63bc-145">List of `Function` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="d63bc-146">Każdy `implementedprocedure` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="d63bc-146">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="d63bc-147">Część</span><span class="sxs-lookup"><span data-stu-id="d63bc-147">Part</span></span>|<span data-ttu-id="d63bc-148">Opis</span><span class="sxs-lookup"><span data-stu-id="d63bc-148">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="d63bc-149">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d63bc-149">Required.</span></span> <span data-ttu-id="d63bc-150">Nazwa interfejsu implementowanego przez tej procedury zawierający klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="d63bc-150">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="d63bc-151">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d63bc-151">Required.</span></span> <span data-ttu-id="d63bc-152">Za pomocą którego procedura została określona w nazwie `interface`.</span><span class="sxs-lookup"><span data-stu-id="d63bc-152">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="d63bc-153">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d63bc-153">Optional.</span></span> <span data-ttu-id="d63bc-154">Wskazuje, że ta procedura może obsługiwać jeden lub więcej określonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d63bc-154">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="d63bc-155">Zobacz [obsługuje](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-155">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="d63bc-156">Jeśli wymagane `Handles` podano.</span><span class="sxs-lookup"><span data-stu-id="d63bc-156">Required if `Handles` is supplied.</span></span> <span data-ttu-id="d63bc-157">Lista zdarzeń, które obsługuje tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="d63bc-157">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="d63bc-158">Każdy `eventspecifier` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="d63bc-158">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="d63bc-159">Część</span><span class="sxs-lookup"><span data-stu-id="d63bc-159">Part</span></span>|<span data-ttu-id="d63bc-160">Opis</span><span class="sxs-lookup"><span data-stu-id="d63bc-160">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="d63bc-161">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d63bc-161">Required.</span></span> <span data-ttu-id="d63bc-162">Zmienna obiektu zadeklarowane z typem danych klasy lub struktury, który wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="d63bc-162">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="d63bc-163">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d63bc-163">Required.</span></span> <span data-ttu-id="d63bc-164">Nazwa zdarzenia, które obsługuje tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="d63bc-164">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="d63bc-165">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d63bc-165">Optional.</span></span> <span data-ttu-id="d63bc-166">Blok instrukcji do wykonania w ramach tej procedury.</span><span class="sxs-lookup"><span data-stu-id="d63bc-166">Block of statements to be executed within this procedure.</span></span>  
  
-   `End Function`  
  
     <span data-ttu-id="d63bc-167">Kończy definicję tej procedury.</span><span class="sxs-lookup"><span data-stu-id="d63bc-167">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d63bc-168">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d63bc-168">Remarks</span></span>  
 <span data-ttu-id="d63bc-169">Cały kod wykonywalny musi znajdować się w procedurze.</span><span class="sxs-lookup"><span data-stu-id="d63bc-169">All executable code must be inside a procedure.</span></span> <span data-ttu-id="d63bc-170">Każdej procedury z kolei jest zadeklarowany w obrębie klasy, struktury lub moduł, który jest określany jako zawierający klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="d63bc-170">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>  
  
 <span data-ttu-id="d63bc-171">Aby zwrócić wartość do wywołującego kodu, użyj `Function` procedury; w przeciwnym razie użyj `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="d63bc-171">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>  
  
## <a name="defining-a-function"></a><span data-ttu-id="d63bc-172">Definiowanie funkcji</span><span class="sxs-lookup"><span data-stu-id="d63bc-172">Defining a Function</span></span>  
 <span data-ttu-id="d63bc-173">Można zdefiniować `Function` procedury tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="d63bc-173">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="d63bc-174">W związku z tym kontekście deklaracji funkcji musi być klasą, strukturą, modułu lub interfejsu i nie może być plik źródłowy, przestrzeni nazw, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="d63bc-174">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="d63bc-175">Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).</span><span class="sxs-lookup"><span data-stu-id="d63bc-175">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="d63bc-176">`Function` Domyślnie procedur dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="d63bc-176">`Function` procedures default to public access.</span></span> <span data-ttu-id="d63bc-177">Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="d63bc-177">You can adjust their access levels with the access modifiers.</span></span>  
  
 <span data-ttu-id="d63bc-178">A `Function` procedury mogą zadeklarować typ danych wartości, która zwraca procedury.</span><span class="sxs-lookup"><span data-stu-id="d63bc-178">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="d63bc-179">Można określić dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d63bc-179">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="d63bc-180">Jeśli nie określisz `returntype` zwraca procedury parametru `Object`.</span><span class="sxs-lookup"><span data-stu-id="d63bc-180">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>  
  
 <span data-ttu-id="d63bc-181">Jeśli ta procedura wykorzystuje `Implements` — słowo kluczowe, zawierające klasy lub struktury musi mieć również `Implements` instrukcji poniższą jego `Class` lub `Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d63bc-181">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="d63bc-182">`Implements` Instrukcja musi zawierać każdy interfejs, który jest określony w `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="d63bc-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="d63bc-183">Jednak nazwy za pomocą którego definiuje interfejs `Function` (w `definedname`) nie musi być zgodna z nazwą w tej procedurze (w `name`).</span><span class="sxs-lookup"><span data-stu-id="d63bc-183">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d63bc-184">Wyrażenia lambda służy do definiowania wbudowane wyrażenia funkcji.</span><span class="sxs-lookup"><span data-stu-id="d63bc-184">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="d63bc-185">Aby uzyskać więcej informacji, zobacz [wyrażenia funkcji](../../../visual-basic/language-reference/operators/function-expression.md) i [wyrażenia Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-185">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="returning-from-a-function"></a><span data-ttu-id="d63bc-186">Zwracanie z funkcji</span><span class="sxs-lookup"><span data-stu-id="d63bc-186">Returning from a Function</span></span>  
 <span data-ttu-id="d63bc-187">Gdy `Function` procedura zwraca do kodu wywołującego, wykonanie będzie kontynuowane przy użyciu instrukcji następującej instrukcji, która wywołuje procedurę.</span><span class="sxs-lookup"><span data-stu-id="d63bc-187">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>  
  
 <span data-ttu-id="d63bc-188">Aby zwrócić wartości z funkcji, można przypisać wartości do nazwy funkcji lub dołączyć go w `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d63bc-188">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>  
  
 <span data-ttu-id="d63bc-189">`Return` Instrukcji jednocześnie przypisuje wartość zwracaną i kończy działanie funkcji, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d63bc-189">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 <span data-ttu-id="d63bc-190">Poniższy przykład przypisuje wartość zwracaną nazwą funkcji `myFunction` , a następnie używa `Exit Function` instrukcji do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="d63bc-190">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 <span data-ttu-id="d63bc-191">`Exit Function` i `Return` instrukcje powoduje natychmiastowe wyjście z `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="d63bc-191">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="d63bc-192">Dowolną liczbę `Exit Function` i `Return` instrukcje mogą występować w dowolnym miejscu w procedurze, a można mieszać `Exit Function` i `Return` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="d63bc-192">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>  
  
 <span data-ttu-id="d63bc-193">Jeśli używasz `Exit Function` bez przypisywanie wartości do `name`, procedura zwraca wartość domyślna dla typu danych określonego w `returntype`.</span><span class="sxs-lookup"><span data-stu-id="d63bc-193">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="d63bc-194">Jeśli `returntype` nie zostanie określona, zwraca procedury `Nothing`, która jest wartością domyślną dla `Object`.</span><span class="sxs-lookup"><span data-stu-id="d63bc-194">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>  
  
## <a name="calling-a-function"></a><span data-ttu-id="d63bc-195">Wywołanie funkcji</span><span class="sxs-lookup"><span data-stu-id="d63bc-195">Calling a Function</span></span>  
 <span data-ttu-id="d63bc-196">Należy wywołać `Function` procedury przy użyciu nazwę procedury, a następnie listy argumentów w nawiasach w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="d63bc-196">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="d63bc-197">Można pominąć nawiasów, tylko wtedy, gdy nie udostępnia żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="d63bc-197">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="d63bc-198">Jednak kod jest bardziej przejrzysta zawsze używać nawiasów.</span><span class="sxs-lookup"><span data-stu-id="d63bc-198">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="d63bc-199">Należy wywołać `Function` procedury taki sam sposób, że można wywołać żadnej biblioteki funkcji, takich jak `Sqrt`, `Cos`, lub `ChrW`.</span><span class="sxs-lookup"><span data-stu-id="d63bc-199">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>  
  
 <span data-ttu-id="d63bc-200">Możesz także wywołać funkcję za pomocą `Call` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d63bc-200">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="d63bc-201">W takim przypadku wartość zwracana jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="d63bc-201">In that case, the return value is ignored.</span></span> <span data-ttu-id="d63bc-202">Użycie `Call` — słowo kluczowe nie jest zalecana w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="d63bc-202">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="d63bc-203">Aby uzyskać więcej informacji, zobacz [instrukcji Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-203">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="d63bc-204">Visual Basic Reorganizuje czasami wyrażenia arytmetyczne, aby zwiększyć wydajność wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d63bc-204">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="d63bc-205">Z tego powodu nie można używać `Function` procedury w wyrażeniach arytmetycznych zmiany funkcji wartości zmiennych w jednym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="d63bc-205">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>  
  
## <a name="async-functions"></a><span data-ttu-id="d63bc-206">Funkcje asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="d63bc-206">Async Functions</span></span>  
 <span data-ttu-id="d63bc-207">*Async* funkcja pozwala wywoływać funkcje asynchroniczne bez za pomocą jawnego wywołania zwrotne i ręcznie dzielenia kodu wielu funkcji lub wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="d63bc-207">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="d63bc-208">Po zaznaczeniu funkcji z [Async](../../../visual-basic/language-reference/modifiers/async.md) modyfikator, można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w funkcji.</span><span class="sxs-lookup"><span data-stu-id="d63bc-208">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="d63bc-209">Gdy kontrolować osiągnie `Await` wyrażenie w `Async` funkcji, zwraca sterowania do obiektu wywołującego i postępu w funkcji jest wstrzymana, aż do zakończenia oczekiwano zadań.</span><span class="sxs-lookup"><span data-stu-id="d63bc-209">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="d63bc-210">Po zakończeniu zadania wykonywania można wznowić w funkcji.</span><span class="sxs-lookup"><span data-stu-id="d63bc-210">When the task is complete, execution can resume in the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d63bc-211">`Async` Procedury zwraca do obiektu wywołującego po albo napotkaniu pierwszego oczekiwano obiekt, który nie został jeszcze ukończony lub pobiera na końcu `Async` procedury, w zależności od wykonane jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="d63bc-211">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>  
  
 <span data-ttu-id="d63bc-212">`Async` Funkcja może mieć typ zwracany <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="d63bc-212">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="d63bc-213">Przykład `Async` funkcja, która ma typ zwracany <xref:System.Threading.Tasks.Task%601> podano poniżej.</span><span class="sxs-lookup"><span data-stu-id="d63bc-213">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>  
  
 <span data-ttu-id="d63bc-214">`Async` Funkcji nie można zadeklarować żadnego [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametrów.</span><span class="sxs-lookup"><span data-stu-id="d63bc-214">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="d63bc-215">A [Sub — instrukcja](sub-statement.md) również może być oznaczony przez `Async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="d63bc-215">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="d63bc-216">To jest używany głównie dla programów obsługi zdarzeń, których nie można zwrócić wartość.</span><span class="sxs-lookup"><span data-stu-id="d63bc-216">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="d63bc-217">`Async``Sub` Procedura nie jest oczekiwane oraz funkcji wywołującej `Async``Sub` procedury nie przechwytuje wyjątków, które są generowane przez `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="d63bc-217">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>  
  
 <span data-ttu-id="d63bc-218">Aby uzyskać więcej informacji na temat `Async` funkcji, zobacz [programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md), [przepływ sterowania w aplikacjach asynchronicznych](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async zwracać typów](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-218">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="iterator-functions"></a><span data-ttu-id="d63bc-219">Funkcje iteracyjne</span><span class="sxs-lookup"><span data-stu-id="d63bc-219">Iterator Functions</span></span>  
 <span data-ttu-id="d63bc-220">*Iterator* funkcja wykonuje niestandardowych iteracji w kolekcji, takie jak listy lub tablicy.</span><span class="sxs-lookup"><span data-stu-id="d63bc-220">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="d63bc-221">Korzysta z funkcji iteracyjnej [Yield](yield-statement.md) instrukcji, aby zwracany był każdy element jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="d63bc-221">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="d63bc-222">Gdy [Yield](yield-statement.md) osiągnięciu instrukcji zapamiętanych bieżącej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d63bc-222">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="d63bc-223">Wykonanie jest uruchamiany ponownie z tej lokalizacji w następnym razem, gdy zostanie wywołana funkcja iteratora.</span><span class="sxs-lookup"><span data-stu-id="d63bc-223">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="d63bc-224">Wywołaj iteratora z kodu klienta przy użyciu [For Each... Następny](for-each-next-statement.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d63bc-224">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>  
  
 <span data-ttu-id="d63bc-225">Może być zwracany typ funkcji iteracyjnej <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="d63bc-225">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="d63bc-226">Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="d63bc-226">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d63bc-227">Przykład</span><span class="sxs-lookup"><span data-stu-id="d63bc-227">Example</span></span>  
 <span data-ttu-id="d63bc-228">W poniższym przykładzie użyto `Function` instrukcji, aby zadeklarować nazwę, parametry i kod, który tworzą treści `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="d63bc-228">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="d63bc-229">`ParamArray` Modyfikator włącza funkcję zaakceptować zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="d63bc-229">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="d63bc-230">Przykład</span><span class="sxs-lookup"><span data-stu-id="d63bc-230">Example</span></span>  
 <span data-ttu-id="d63bc-231">Poniższy przykład przedstawia wywoływanie funkcji zadeklarowany w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d63bc-231">The following example invokes the function declared in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="d63bc-232">Przykład</span><span class="sxs-lookup"><span data-stu-id="d63bc-232">Example</span></span>  
 <span data-ttu-id="d63bc-233">W poniższym przykładzie `DelayAsync` jest `Async``Function` mający typ zwracany <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="d63bc-233">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="d63bc-234">`DelayAsync` ma `Return` instrukcji, która zwraca liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="d63bc-234">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="d63bc-235">W związku z tym funkcja deklaracja `DelayAsync` musi mieć typ zwracany `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="d63bc-235">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="d63bc-236">Ponieważ typ zwracany jest `Task(Of Integer)`, oceny `Await` wyrażenie w `DoSomethingAsync` tworzy liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="d63bc-236">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="d63bc-237">Zostało to przedstawione w tej instrukcji: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="d63bc-237">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="d63bc-238">`startButton_Click` Procedura jest przykładem `Async Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="d63bc-238">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="d63bc-239">Ponieważ `DoSomethingAsync` jest `Async` funkcji, zadanie dla wywołania `DoSomethingAsync` musi być oczekiwane, jak pokazano następująca instrukcja: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="d63bc-239">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="d63bc-240">`startButton_Click``Sub` Procedury musi być zdefiniowany za pomocą `Async` modyfikator ponieważ ma ona `Await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d63bc-240">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d63bc-241">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d63bc-241">See Also</span></span>  
 [<span data-ttu-id="d63bc-242">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d63bc-242">Sub Statement</span></span>](sub-statement.md)  
 [<span data-ttu-id="d63bc-243">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="d63bc-243">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [<span data-ttu-id="d63bc-244">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="d63bc-244">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="d63bc-245">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d63bc-245">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="d63bc-246">Call, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d63bc-246">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="d63bc-247">z</span><span class="sxs-lookup"><span data-stu-id="d63bc-247">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="d63bc-248">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="d63bc-248">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="d63bc-249">Instrukcje: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="d63bc-249">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="d63bc-250">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="d63bc-250">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="d63bc-251">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="d63bc-251">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="d63bc-252">Function, wyrażenie</span><span class="sxs-lookup"><span data-stu-id="d63bc-252">Function Expression</span></span>](../../../visual-basic/language-reference/operators/function-expression.md)
