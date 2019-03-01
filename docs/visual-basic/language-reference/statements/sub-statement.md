---
title: Sub — Instrukcja (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: 6984e7e9f8695ff5bccdde01171733e740a5d6a7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965959"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="5cfc6-102">Sub — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cfc6-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="5cfc6-103">Deklaruje nazwę, parametry i kod, który definiuje `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cfc6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5cfc6-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="5cfc6-105">Części</span><span class="sxs-lookup"><span data-stu-id="5cfc6-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="5cfc6-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-106">Optional.</span></span> <span data-ttu-id="5cfc6-107">Zobacz [Lista atrybutów](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="5cfc6-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-108">Optional.</span></span> <span data-ttu-id="5cfc6-109">Wskazuje definicji metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="5cfc6-110">Zobacz [metod częściowych](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="5cfc6-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-111">Optional.</span></span> <span data-ttu-id="5cfc6-112">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="5cfc6-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="5cfc6-113">Public</span><span class="sxs-lookup"><span data-stu-id="5cfc6-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="5cfc6-114">Protected</span><span class="sxs-lookup"><span data-stu-id="5cfc6-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="5cfc6-115">Friend</span><span class="sxs-lookup"><span data-stu-id="5cfc6-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="5cfc6-116">Private</span><span class="sxs-lookup"><span data-stu-id="5cfc6-116">Private</span></span>](../modifiers/private.md)  
  
    - [<span data-ttu-id="5cfc6-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="5cfc6-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

    - [<span data-ttu-id="5cfc6-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="5cfc6-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="5cfc6-119">Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="5cfc6-120">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-120">Optional.</span></span> <span data-ttu-id="5cfc6-121">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="5cfc6-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="5cfc6-122">Overloads</span><span class="sxs-lookup"><span data-stu-id="5cfc6-122">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="5cfc6-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="5cfc6-123">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="5cfc6-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="5cfc6-124">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="5cfc6-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="5cfc6-125">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="5cfc6-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="5cfc6-126">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="5cfc6-127">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-127">Optional.</span></span> <span data-ttu-id="5cfc6-128">Zobacz [udostępnione](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-128">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="5cfc6-129">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-129">Optional.</span></span> <span data-ttu-id="5cfc6-130">Zobacz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-130">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="5cfc6-131">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-131">Optional.</span></span> <span data-ttu-id="5cfc6-132">Zobacz [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-132">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="5cfc6-133">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-133">Required.</span></span> <span data-ttu-id="5cfc6-134">Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-134">Name of the procedure.</span></span> <span data-ttu-id="5cfc6-135">Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-135">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="5cfc6-136">Aby utworzyć procedurę konstruktora dla klasy, ustaw nazwę `Sub` procedury, aby `New` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="5cfc6-137">Aby uzyskać więcej informacji, zobacz [okres istnienia obiektów: Jak obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="5cfc6-138">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-138">Optional.</span></span> <span data-ttu-id="5cfc6-139">Lista parametrów typu ogólnego procedury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="5cfc6-140">Zobacz [Lista typów](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-140">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="5cfc6-141">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-141">Optional.</span></span> <span data-ttu-id="5cfc6-142">Lista nazwy zmiennych lokalnych reprezentującą parametry tej procedury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="5cfc6-143">Zobacz [listy parametrów](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-143">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="5cfc6-144">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-144">Optional.</span></span> <span data-ttu-id="5cfc6-145">Wskazuje, że ta procedura implementuje co najmniej jeden `Sub` procedury, każdy z nich zdefiniowane w interfejsie zaimplementowany przez klasę lub strukturę zawierającego tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="5cfc6-146">Zobacz [Implements, instrukcja](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-146">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="5cfc6-147">Jeśli wymagane `Implements` podano.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="5cfc6-148">Lista `Sub` procedury są wdrożone.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-148">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="5cfc6-149">Każdy `implementedprocedure` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="5cfc6-149">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="5cfc6-150">Część</span><span class="sxs-lookup"><span data-stu-id="5cfc6-150">Part</span></span>|<span data-ttu-id="5cfc6-151">Opis</span><span class="sxs-lookup"><span data-stu-id="5cfc6-151">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="5cfc6-152">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-152">Required.</span></span> <span data-ttu-id="5cfc6-153">Nazwa interfejsu implementowany przez tej procedury zawierający klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="5cfc6-154">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-154">Required.</span></span> <span data-ttu-id="5cfc6-155">Nazwa, za pomocą którego procedura jest zdefiniowany w `interface`.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-155">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="5cfc6-156">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-156">Optional.</span></span> <span data-ttu-id="5cfc6-157">Wskazuje, że ta procedura może obsługiwać jeden lub więcej określonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="5cfc6-158">Zobacz [obsługuje](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-158">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="5cfc6-159">Jeśli wymagane `Handles` podano.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="5cfc6-160">Lista zdarzeń, które obsługuje tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-160">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="5cfc6-161">Każdy `eventspecifier` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="5cfc6-161">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="5cfc6-162">Część</span><span class="sxs-lookup"><span data-stu-id="5cfc6-162">Part</span></span>|<span data-ttu-id="5cfc6-163">Opis</span><span class="sxs-lookup"><span data-stu-id="5cfc6-163">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="5cfc6-164">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-164">Required.</span></span> <span data-ttu-id="5cfc6-165">Zmienna obiektu zadeklarowane z typem danych klasy lub struktury, która wywołuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="5cfc6-166">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-166">Required.</span></span> <span data-ttu-id="5cfc6-167">Nazwa zdarzenia, które obsługuje tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-167">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="5cfc6-168">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-168">Optional.</span></span> <span data-ttu-id="5cfc6-169">Blok instrukcji do uruchomienia w ramach tej procedury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-169">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="5cfc6-170">Kończy definicję tej procedury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-170">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cfc6-171">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5cfc6-171">Remarks</span></span>  
 <span data-ttu-id="5cfc6-172">Cały kod wykonywalny musi być wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="5cfc6-173">Użyj `Sub` procedury, jeśli nie chcesz zwracać wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="5cfc6-174">Użyj `Function` procedury zwracać wartość.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-174">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="5cfc6-175">Definiujący procedurę Sub</span><span class="sxs-lookup"><span data-stu-id="5cfc6-175">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="5cfc6-176">Można zdefiniować `Sub` procedury tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="5cfc6-177">Kontekst deklaracji procedurę sub dlatego należy klasy, struktury, modułem lub interfejsem, a nie może być plikiem źródłowym, przestrzeń nazw, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="5cfc6-178">Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="5cfc6-179">`Sub` Domyślnie procedur dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="5cfc6-180">Modyfikatory dostępu można dostosować ich poziomy dostępu.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-180">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="5cfc6-181">Jeśli w procedurze użyto `Implements` — słowo kluczowe, zawierający klasy lub struktury, musi mieć `Implements` instrukcji, który następuje bezpośrednio po jego `Class` lub `Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="5cfc6-182">`Implements` Instrukcja musi zawierać każdego interfejsu, który jest określony w `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="5cfc6-183">Jednak nazwy za pomocą którego interfejs definiuje `Sub` (w `definedname`) nie musi być zgodna z nazwą w tej procedurze (w `name`).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="5cfc6-184">Zwracanie z procedurę Sub</span><span class="sxs-lookup"><span data-stu-id="5cfc6-184">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="5cfc6-185">Gdy `Sub` procedury zwraca do kodu wywołującego, wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji, która nazwała go.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="5cfc6-186">W poniższym przykładzie pokazano zwracany `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-186">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="5cfc6-187">`Exit Sub` i `Return` instrukcji powodują natychmiastowego wyjścia z `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="5cfc6-188">Dowolną liczbę `Exit Sub` i `Return` instrukcji może występować w dowolnym miejscu w ramach procedury i możesz mieszać `Exit Sub` i `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="5cfc6-189">Wywoływanie procedury Sub</span><span class="sxs-lookup"><span data-stu-id="5cfc6-189">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="5cfc6-190">Należy wywołać `Sub` procedury przy użyciu nazwy procedury w instrukcji i postępuj zgodnie z tej nazwy z listą argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="5cfc6-191">Nawiasy można pominąć, tylko, jeśli nie podasz żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="5cfc6-192">Jednak kod jest bardziej czytelny, jeśli zawsze zawierać nawiasy.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-192">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="5cfc6-193">A `Sub` procedury i `Function` procedury mogą mieć parametry i wykonać serię instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="5cfc6-194">Jednak `Function` procedury zwraca wartość, a w `Sub` nie procedury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="5cfc6-195">W związku z tym, nie można użyć `Sub` procedury w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="5cfc6-196">Możesz użyć `Call` — słowo kluczowe po wywołaniu `Sub` procedura, ale że — słowo kluczowe nie jest zalecany dla większości zastosowań.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="5cfc6-197">Aby uzyskać więcej informacji, zobacz [instrukcji Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-197">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="5cfc6-198">Visual Basic Reorganizuje czasami wyrażenia arytmetyczne, aby zwiększyć wydajność wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="5cfc6-199">Z tego powodu jeśli lista argumentów zawiera wyrażenia, które wywołują innych procedur, nie należy zakładać, że że te wyrażenia zostaną wywołane w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="5cfc6-200">Async Sub — procedury</span><span class="sxs-lookup"><span data-stu-id="5cfc6-200">Async Sub Procedures</span></span>  
 <span data-ttu-id="5cfc6-201">Za pomocą funkcji asynchronicznych, można wywoływać funkcje asynchroniczne bez za pomocą jawnego wywołania zwrotne lub ręcznego podziału kodu na wielu funkcji lub wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="5cfc6-202">Po oznaczeniu procedury z [Async](../modifiers/async.md) modyfikator, można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w procedurze.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="5cfc6-203">Gdy kontrola osiąga `Await` wyrażenia w `Async` procedury, sterowanie powraca do obiektu wywołującego, a postęp w procedurze jest wstrzymana, dopóki nie zakończy się oczekiwane zadanie.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="5cfc6-204">Kiedy zadanie zostanie ukończone, wykonanie można wznowić w procedurze.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-204">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cfc6-205">`Async` Procedury powraca do obiektu wywołującego, po napotkaniu albo pierwszego oczekiwane obiekt, który nie został jeszcze ukończony lub na końcu `Async` procedury zostanie osiągnięty, zależnie co nastąpi wcześniej.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="5cfc6-206">Można również oznaczyć [Function — instrukcja](function-statement.md) z `Async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="5cfc6-207">`Async` Funkcji może mieć typ zwracany <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="5cfc6-208">Przykład później w tym temacie przedstawiono `Async` funkcję, która ma typ zwracany <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="5cfc6-209">`Async` `Sub` procedury są głównie używane do obsługi zdarzeń, których nie można zwrócić wartość.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="5cfc6-210">`Async` `Sub` Procedura nie może być oczekiwany, a obiekt wywołujący `Async` `Sub` procedura nie może przechwytywać wyjątków, `Sub` zgłasza procedury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-210">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="5cfc6-211">`Async` Procedura nie może deklarować [ByRef](../modifiers/byref.md) parametrów.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="5cfc6-212">Aby uzyskać więcej informacji na temat `Async` procedury, zobacz [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc6-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cfc6-213">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cfc6-213">Example</span></span>  
 <span data-ttu-id="5cfc6-214">W poniższym przykładzie użyto `Sub` instrukcji, aby zdefiniować nazwę, parametry i kod, który tworzą treści `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="5cfc6-215">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cfc6-215">Example</span></span>  
 <span data-ttu-id="5cfc6-216">W poniższym przykładzie `DelayAsync` jest `Async` `Function` zawierający typ zwracany <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-216">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="5cfc6-217">`DelayAsync` ma `Return` instrukcję, która zwraca liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="5cfc6-218">W związku z tym, funkcja deklaracji `DelayAsync` musi mieć typ zwracany `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="5cfc6-219">Ponieważ typem zwracanym jest `Task(Of Integer)`, oceny `Await` wyrażenia w `DoSomethingAsync` tworzy liczbą całkowitą, co pokazuje poniższa instrukcja: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="5cfc6-220">`startButton_Click` Procedura to przykład `Async Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="5cfc6-221">Ponieważ `DoSomethingAsync` jest `Async` funkcji, zadanie do wywołań `DoSomethingAsync` musi być oczekiwana, co pokazuje poniższa instrukcja: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="5cfc6-222">`startButton_Click` `Sub` Procedury muszą być zdefiniowane przy użyciu `Async` modyfikator ponieważ ma ona `Await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5cfc6-222">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5cfc6-223">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cfc6-223">See also</span></span>
- [<span data-ttu-id="5cfc6-224">Implements, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5cfc6-224">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="5cfc6-225">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5cfc6-225">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="5cfc6-226">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="5cfc6-226">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="5cfc6-227">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5cfc6-227">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="5cfc6-228">Call, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5cfc6-228">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="5cfc6-229">z</span><span class="sxs-lookup"><span data-stu-id="5cfc6-229">Of</span></span>](of-clause.md)
- [<span data-ttu-id="5cfc6-230">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="5cfc6-230">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="5cfc6-231">Instrukcje: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="5cfc6-231">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="5cfc6-232">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="5cfc6-232">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="5cfc6-233">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="5cfc6-233">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
