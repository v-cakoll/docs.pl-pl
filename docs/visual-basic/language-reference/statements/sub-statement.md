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
ms.openlocfilehash: 08be38cdbec82914b567ab5b86eed71181efcf57
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234179"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="23d93-102">Sub — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23d93-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="23d93-103">Deklaruje nazwę, parametry i kod, który definiuje `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="23d93-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23d93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23d93-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="23d93-105">Części</span><span class="sxs-lookup"><span data-stu-id="23d93-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="23d93-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="23d93-106">Optional.</span></span> <span data-ttu-id="23d93-107">Zobacz temat [Lista atrybutów](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="23d93-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="23d93-108">Optional.</span></span> <span data-ttu-id="23d93-109">Wskazuje definicję metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="23d93-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="23d93-110">Zobacz [metody częściowe](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="23d93-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="23d93-111">Optional.</span></span> <span data-ttu-id="23d93-112">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="23d93-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="23d93-113">Public</span><span class="sxs-lookup"><span data-stu-id="23d93-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="23d93-114">Protected</span><span class="sxs-lookup"><span data-stu-id="23d93-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="23d93-115">Friend</span><span class="sxs-lookup"><span data-stu-id="23d93-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="23d93-116">Private</span><span class="sxs-lookup"><span data-stu-id="23d93-116">Private</span></span>](../modifiers/private.md)  
  
    - [<span data-ttu-id="23d93-117">Friend chronionych</span><span class="sxs-lookup"><span data-stu-id="23d93-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

    - [<span data-ttu-id="23d93-118">Prywatne chronione</span><span class="sxs-lookup"><span data-stu-id="23d93-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="23d93-119">Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="23d93-120">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="23d93-120">Optional.</span></span> <span data-ttu-id="23d93-121">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="23d93-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="23d93-122">Overloads</span><span class="sxs-lookup"><span data-stu-id="23d93-122">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="23d93-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="23d93-123">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="23d93-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="23d93-124">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="23d93-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="23d93-125">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="23d93-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="23d93-126">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="23d93-127">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="23d93-127">Optional.</span></span> <span data-ttu-id="23d93-128">Zobacz [udostępnionych](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-128">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="23d93-129">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="23d93-129">Optional.</span></span> <span data-ttu-id="23d93-130">Zobacz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-130">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="23d93-131">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="23d93-131">Optional.</span></span> <span data-ttu-id="23d93-132">Zobacz [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-132">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="23d93-133">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="23d93-133">Required.</span></span> <span data-ttu-id="23d93-134">Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="23d93-134">Name of the procedure.</span></span> <span data-ttu-id="23d93-135">Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-135">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="23d93-136">Aby utworzyć procedury konstruktora dla klasy, ustaw nazwę `Sub` procedura `New` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="23d93-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="23d93-137">Aby uzyskać więcej informacji, zobacz [okres istnienia obiektów: sposób obiekty są utworzone i Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="23d93-138">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="23d93-138">Optional.</span></span> <span data-ttu-id="23d93-139">Lista parametrów typu ogólnego procedurę.</span><span class="sxs-lookup"><span data-stu-id="23d93-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="23d93-140">Zobacz [typu listy](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-140">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="23d93-141">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="23d93-141">Optional.</span></span> <span data-ttu-id="23d93-142">Lista nazwy zmiennych lokalnych reprezentujący parametry tej procedury.</span><span class="sxs-lookup"><span data-stu-id="23d93-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="23d93-143">Zobacz [listy parametrów](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-143">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="23d93-144">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="23d93-144">Optional.</span></span> <span data-ttu-id="23d93-145">Wskazuje, że ta procedura implementuje co najmniej jeden `Sub` procedur, każdą z nich zdefiniowane w interfejsie zaimplementowany przez klasę lub strukturę zawierającego tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="23d93-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="23d93-146">Zobacz [implementuje instrukcji](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-146">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="23d93-147">Jeśli wymagane `Implements` podano.</span><span class="sxs-lookup"><span data-stu-id="23d93-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="23d93-148">Lista `Sub` procedury implementowana.</span><span class="sxs-lookup"><span data-stu-id="23d93-148">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="23d93-149">Każdy `implementedprocedure` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="23d93-149">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="23d93-150">Część</span><span class="sxs-lookup"><span data-stu-id="23d93-150">Part</span></span>|<span data-ttu-id="23d93-151">Opis</span><span class="sxs-lookup"><span data-stu-id="23d93-151">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="23d93-152">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="23d93-152">Required.</span></span> <span data-ttu-id="23d93-153">Nazwa interfejsu implementowanego przez tej procedury zawierający klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="23d93-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="23d93-154">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="23d93-154">Required.</span></span> <span data-ttu-id="23d93-155">Za pomocą którego procedura została określona w nazwie `interface`.</span><span class="sxs-lookup"><span data-stu-id="23d93-155">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="23d93-156">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="23d93-156">Optional.</span></span> <span data-ttu-id="23d93-157">Wskazuje, że ta procedura może obsługiwać jeden lub więcej określonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="23d93-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="23d93-158">Zobacz [obsługuje](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-158">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="23d93-159">Jeśli wymagane `Handles` podano.</span><span class="sxs-lookup"><span data-stu-id="23d93-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="23d93-160">Lista zdarzeń, które obsługuje tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="23d93-160">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="23d93-161">Każdy `eventspecifier` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="23d93-161">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="23d93-162">Część</span><span class="sxs-lookup"><span data-stu-id="23d93-162">Part</span></span>|<span data-ttu-id="23d93-163">Opis</span><span class="sxs-lookup"><span data-stu-id="23d93-163">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="23d93-164">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="23d93-164">Required.</span></span> <span data-ttu-id="23d93-165">Zmienna obiektu zadeklarowane z typem danych klasy lub struktury, który wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="23d93-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="23d93-166">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="23d93-166">Required.</span></span> <span data-ttu-id="23d93-167">Nazwa zdarzenia, które obsługuje tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="23d93-167">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="23d93-168">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="23d93-168">Optional.</span></span> <span data-ttu-id="23d93-169">Blok instrukcji do uruchomienia w ramach tej procedury.</span><span class="sxs-lookup"><span data-stu-id="23d93-169">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="23d93-170">Kończy definicję tej procedury.</span><span class="sxs-lookup"><span data-stu-id="23d93-170">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23d93-171">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23d93-171">Remarks</span></span>  
 <span data-ttu-id="23d93-172">Cały kod wykonywalny musi znajdować się w procedurze.</span><span class="sxs-lookup"><span data-stu-id="23d93-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="23d93-173">Użyj `Sub` procedury, jeśli nie chcesz zwrócić wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="23d93-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="23d93-174">Użyj `Function` procedury, jeśli chcesz zwrócić wartość.</span><span class="sxs-lookup"><span data-stu-id="23d93-174">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="23d93-175">Definiowanie procedury Sub</span><span class="sxs-lookup"><span data-stu-id="23d93-175">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="23d93-176">Można zdefiniować `Sub` procedury tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="23d93-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="23d93-177">Kontekst deklaracji procedurę sub dlatego należy klasy, struktury, modułu lub interfejsu i nie może być plik źródłowy, przestrzeni nazw, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="23d93-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="23d93-178">Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).</span><span class="sxs-lookup"><span data-stu-id="23d93-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="23d93-179">`Sub` Domyślnie procedur dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="23d93-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="23d93-180">Modyfikatory dostępu można dostosować ich poziomy dostępu.</span><span class="sxs-lookup"><span data-stu-id="23d93-180">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="23d93-181">Jeśli procedura używa `Implements` — słowo kluczowe, zawierające klasy lub struktury musi mieć `Implements` instrukcji poniższą jego `Class` lub `Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="23d93-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="23d93-182">`Implements` Instrukcja musi zawierać każdy interfejs, który jest określony w `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="23d93-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="23d93-183">Jednak nazwy za pomocą którego definiuje interfejs `Sub` (w `definedname`) nie musi być zgodna z nazwą w tej procedurze (w `name`).</span><span class="sxs-lookup"><span data-stu-id="23d93-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="23d93-184">Zwracanie z procedurę Sub</span><span class="sxs-lookup"><span data-stu-id="23d93-184">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="23d93-185">Gdy `Sub` procedura zwraca do kodu wywołującego, wykonanie będzie kontynuowane przy użyciu instrukcji następującej po instrukcji, która ją.</span><span class="sxs-lookup"><span data-stu-id="23d93-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="23d93-186">W poniższym przykładzie przedstawiono typ zwracany `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="23d93-186">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="23d93-187">`Exit Sub` i `Return` instrukcje powoduje natychmiastowe wyjście z `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="23d93-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="23d93-188">Dowolną liczbę `Exit Sub` i `Return` instrukcje mogą występować w dowolnym miejscu w procedurze, a można mieszać `Exit Sub` i `Return` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="23d93-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="23d93-189">Wywołanie procedury Sub</span><span class="sxs-lookup"><span data-stu-id="23d93-189">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="23d93-190">Należy wywołać `Sub` procedury przy użyciu nazwy procedury w instrukcji i następnie wykonując tej nazwy z listą argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="23d93-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="23d93-191">Można pominąć nawiasów, tylko wtedy, gdy nie podawaj żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="23d93-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="23d93-192">Jednak kod jest bardziej przejrzysta zawsze używać nawiasów.</span><span class="sxs-lookup"><span data-stu-id="23d93-192">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="23d93-193">A `Sub` procedury i `Function` procedura może mieć parametrów i wykonać serię instrukcji.</span><span class="sxs-lookup"><span data-stu-id="23d93-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="23d93-194">Jednak `Function` procedury zwraca wartość i a `Sub` nie procedury.</span><span class="sxs-lookup"><span data-stu-id="23d93-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="23d93-195">W związku z tym nie można użyć `Sub` procedury w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="23d93-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="23d93-196">Można użyć `Call` — słowo kluczowe podczas wywoływania `Sub` procedura, ale tego słowa kluczowego nie jest zalecane w przypadku zastosowań.</span><span class="sxs-lookup"><span data-stu-id="23d93-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="23d93-197">Aby uzyskać więcej informacji, zobacz [instrukcji Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-197">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="23d93-198">Visual Basic Reorganizuje czasami wyrażenia arytmetyczne, aby zwiększyć wydajność wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="23d93-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="23d93-199">Z tego powodu jeśli lista argumentów zawiera wyrażeń, które wywołują inne procedury możesz nie należy założyć, że te wyrażenia zostanie wywołana w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="23d93-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="23d93-200">Async Sub — procedury</span><span class="sxs-lookup"><span data-stu-id="23d93-200">Async Sub Procedures</span></span>  
 <span data-ttu-id="23d93-201">Korzystając z funkcji asynchronicznych, można wywołać funkcji asynchronicznych bez za pomocą jawnego wywołania zwrotne i ręcznie dzielenia kodu wielu funkcji lub wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="23d93-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="23d93-202">Jeśli procedura o [Async](../modifiers/async.md) modyfikator, można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w procedurze.</span><span class="sxs-lookup"><span data-stu-id="23d93-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="23d93-203">Gdy kontrolować osiągnie `Await` wyrażenie w `Async` procedury kontroli zwraca wywołującego i postępu w procedurze jest wstrzymana, aż do zakończenia zadań oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="23d93-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="23d93-204">Po zakończeniu zadania wykonywania można wznowić w procedurze.</span><span class="sxs-lookup"><span data-stu-id="23d93-204">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23d93-205">`Async` Procedury zwraca do wywołującego po napotkaniu albo pierwszego oczekiwano obiekt, który nie został jeszcze ukończony lub na końcu `Async` osiągnięciu procedury cokolwiek nastąpi najpierw.</span><span class="sxs-lookup"><span data-stu-id="23d93-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="23d93-206">Można również zaznaczyć [instrukcji Function](function-statement.md) z `Async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="23d93-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="23d93-207">`Async` Funkcja może mieć typ zwracany <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="23d93-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="23d93-208">Przykład później w tym temacie przedstawiono `Async` funkcja, która ma typ zwracany <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="23d93-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="23d93-209">`Async` `Sub` procedury są używane głównie dla programów obsługi zdarzeń, których nie można zwrócić wartość.</span><span class="sxs-lookup"><span data-stu-id="23d93-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="23d93-210">`Async``Sub` Procedura nie jest oczekiwane oraz funkcji wywołującej `Async``Sub` procedury nie przechwytuje wyjątków który `Sub` zgłasza procedury.</span><span class="sxs-lookup"><span data-stu-id="23d93-210">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="23d93-211">`Async` Procedury nie można zadeklarować żadnego [ByRef](../modifiers/byref.md) parametrów.</span><span class="sxs-lookup"><span data-stu-id="23d93-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="23d93-212">Aby uzyskać więcej informacji na temat `Async` procedury, zobacz [programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md), [przepływ sterowania w aplikacjach asynchronicznych](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async zwracać typów](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="23d93-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23d93-213">Przykład</span><span class="sxs-lookup"><span data-stu-id="23d93-213">Example</span></span>  
 <span data-ttu-id="23d93-214">W poniższym przykładzie użyto `Sub` instrukcji, aby zdefiniować nazwę, parametry i kod, który tworzą treści `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="23d93-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="23d93-215">Przykład</span><span class="sxs-lookup"><span data-stu-id="23d93-215">Example</span></span>  
 <span data-ttu-id="23d93-216">W poniższym przykładzie `DelayAsync` jest `Async``Function` mający typ zwracany <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="23d93-216">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="23d93-217">`DelayAsync` ma `Return` instrukcji, która zwraca liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="23d93-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="23d93-218">W związku z tym funkcja deklaracja `DelayAsync` musi mieć typ zwracany `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="23d93-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="23d93-219">Ponieważ typ zwracany jest `Task(Of Integer)`, oceny `Await` wyrażenie w `DoSomethingAsync` tworzy całkowitą, jak przedstawiono na poniższym instrukcji: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="23d93-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="23d93-220">`startButton_Click` Procedura jest przykładem `Async Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="23d93-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="23d93-221">Ponieważ `DoSomethingAsync` jest `Async` funkcji, zadanie dla wywołania `DoSomethingAsync` musi być oczekiwane, jak przedstawiono na poniższym instrukcji: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="23d93-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="23d93-222">`startButton_Click``Sub` Procedury musi być zdefiniowany za pomocą `Async` modyfikator ponieważ ma ona `Await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="23d93-222">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="23d93-223">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23d93-223">See Also</span></span>  
 [<span data-ttu-id="23d93-224">Implements, instrukcja</span><span class="sxs-lookup"><span data-stu-id="23d93-224">Implements Statement</span></span>](implements-statement.md)  
 [<span data-ttu-id="23d93-225">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="23d93-225">Function Statement</span></span>](function-statement.md)  
 [<span data-ttu-id="23d93-226">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="23d93-226">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="23d93-227">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="23d93-227">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="23d93-228">Call, instrukcja</span><span class="sxs-lookup"><span data-stu-id="23d93-228">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="23d93-229">z</span><span class="sxs-lookup"><span data-stu-id="23d93-229">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="23d93-230">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="23d93-230">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="23d93-231">Instrukcje: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="23d93-231">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="23d93-232">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="23d93-232">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="23d93-233">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="23d93-233">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
