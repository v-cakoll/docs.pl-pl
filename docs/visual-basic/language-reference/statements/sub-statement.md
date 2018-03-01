---
title: "Sub — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0a2d0d5ffdca857a3a5ca58cd38b0930f254526f
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="0de19-102">Sub — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0de19-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="0de19-103">Deklaruje nazwę, parametry i kod, który definiuje `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="0de19-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0de19-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0de19-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="0de19-105">Części</span><span class="sxs-lookup"><span data-stu-id="0de19-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="0de19-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0de19-106">Optional.</span></span> <span data-ttu-id="0de19-107">Zobacz [listę atrybutów](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="0de19-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0de19-108">Optional.</span></span> <span data-ttu-id="0de19-109">Wskazuje definicję metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="0de19-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="0de19-110">Zobacz [metody częściowe](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="0de19-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0de19-111">Optional.</span></span> <span data-ttu-id="0de19-112">Może to być jedna z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="0de19-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="0de19-113">Public</span><span class="sxs-lookup"><span data-stu-id="0de19-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="0de19-114">Protected</span><span class="sxs-lookup"><span data-stu-id="0de19-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="0de19-115">Friend</span><span class="sxs-lookup"><span data-stu-id="0de19-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="0de19-116">Private</span><span class="sxs-lookup"><span data-stu-id="0de19-116">Private</span></span>](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="0de19-117">Zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-117">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="0de19-118">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0de19-118">Optional.</span></span> <span data-ttu-id="0de19-119">Może to być jedna z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="0de19-119">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="0de19-120">Overloads</span><span class="sxs-lookup"><span data-stu-id="0de19-120">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="0de19-121">Overrides</span><span class="sxs-lookup"><span data-stu-id="0de19-121">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="0de19-122">Overridable</span><span class="sxs-lookup"><span data-stu-id="0de19-122">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="0de19-123">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="0de19-123">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="0de19-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="0de19-124">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="0de19-125">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0de19-125">Optional.</span></span> <span data-ttu-id="0de19-126">Zobacz [udostępnionych](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-126">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="0de19-127">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0de19-127">Optional.</span></span> <span data-ttu-id="0de19-128">Zobacz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-128">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="0de19-129">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0de19-129">Optional.</span></span> <span data-ttu-id="0de19-130">Zobacz [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-130">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="0de19-131">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="0de19-131">Required.</span></span> <span data-ttu-id="0de19-132">Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="0de19-132">Name of the procedure.</span></span> <span data-ttu-id="0de19-133">Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-133">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="0de19-134">Aby utworzyć procedury konstruktora dla klasy, ustaw nazwę `Sub` procedura `New` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="0de19-134">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="0de19-135">Aby uzyskać więcej informacji, zobacz [okres istnienia obiektów: sposób obiekty są utworzone i Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-135">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="0de19-136">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0de19-136">Optional.</span></span> <span data-ttu-id="0de19-137">Lista parametrów typu ogólnego procedurę.</span><span class="sxs-lookup"><span data-stu-id="0de19-137">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="0de19-138">Zobacz [typu listy](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-138">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="0de19-139">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0de19-139">Optional.</span></span> <span data-ttu-id="0de19-140">Lista nazwy zmiennych lokalnych reprezentujący parametry tej procedury.</span><span class="sxs-lookup"><span data-stu-id="0de19-140">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="0de19-141">Zobacz [listy parametrów](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-141">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="0de19-142">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0de19-142">Optional.</span></span> <span data-ttu-id="0de19-143">Wskazuje, że ta procedura implementuje co najmniej jeden `Sub` procedur, każdą z nich zdefiniowane w interfejsie zaimplementowany przez klasę lub strukturę zawierającego tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="0de19-143">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="0de19-144">Zobacz [implementuje instrukcji](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-144">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="0de19-145">Jeśli wymagane `Implements` podano.</span><span class="sxs-lookup"><span data-stu-id="0de19-145">Required if `Implements` is supplied.</span></span> <span data-ttu-id="0de19-146">Lista `Sub` procedury implementowana.</span><span class="sxs-lookup"><span data-stu-id="0de19-146">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="0de19-147">Każdy `implementedprocedure` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="0de19-147">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="0de19-148">Część</span><span class="sxs-lookup"><span data-stu-id="0de19-148">Part</span></span>|<span data-ttu-id="0de19-149">Opis</span><span class="sxs-lookup"><span data-stu-id="0de19-149">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="0de19-150">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="0de19-150">Required.</span></span> <span data-ttu-id="0de19-151">Nazwa interfejsu implementowanego przez tej procedury zawierający klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0de19-151">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="0de19-152">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="0de19-152">Required.</span></span> <span data-ttu-id="0de19-153">Za pomocą którego procedura została określona w nazwie `interface`.</span><span class="sxs-lookup"><span data-stu-id="0de19-153">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="0de19-154">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0de19-154">Optional.</span></span> <span data-ttu-id="0de19-155">Wskazuje, że ta procedura może obsługiwać jeden lub więcej określonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0de19-155">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="0de19-156">Zobacz [obsługuje](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-156">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="0de19-157">Jeśli wymagane `Handles` podano.</span><span class="sxs-lookup"><span data-stu-id="0de19-157">Required if `Handles` is supplied.</span></span> <span data-ttu-id="0de19-158">Lista zdarzeń, które obsługuje tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="0de19-158">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="0de19-159">Każdy `eventspecifier` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="0de19-159">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="0de19-160">Część</span><span class="sxs-lookup"><span data-stu-id="0de19-160">Part</span></span>|<span data-ttu-id="0de19-161">Opis</span><span class="sxs-lookup"><span data-stu-id="0de19-161">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="0de19-162">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="0de19-162">Required.</span></span> <span data-ttu-id="0de19-163">Zmienna obiektu zadeklarowane z typem danych klasy lub struktury, który wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0de19-163">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="0de19-164">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="0de19-164">Required.</span></span> <span data-ttu-id="0de19-165">Nazwa zdarzenia, które obsługuje tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="0de19-165">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="0de19-166">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0de19-166">Optional.</span></span> <span data-ttu-id="0de19-167">Blok instrukcji do uruchomienia w ramach tej procedury.</span><span class="sxs-lookup"><span data-stu-id="0de19-167">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="0de19-168">Kończy definicję tej procedury.</span><span class="sxs-lookup"><span data-stu-id="0de19-168">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0de19-169">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0de19-169">Remarks</span></span>  
 <span data-ttu-id="0de19-170">Cały kod wykonywalny musi znajdować się w procedurze.</span><span class="sxs-lookup"><span data-stu-id="0de19-170">All executable code must be inside a procedure.</span></span> <span data-ttu-id="0de19-171">Użyj `Sub` procedury, jeśli nie chcesz zwrócić wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="0de19-171">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="0de19-172">Użyj `Function` procedury, jeśli chcesz zwrócić wartość.</span><span class="sxs-lookup"><span data-stu-id="0de19-172">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="0de19-173">Definiowanie procedury Sub</span><span class="sxs-lookup"><span data-stu-id="0de19-173">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="0de19-174">Można zdefiniować `Sub` procedury tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="0de19-174">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="0de19-175">Kontekst deklaracji procedurę sub dlatego należy klasy, struktury, modułu lub interfejsu i nie może być plik źródłowy, przestrzeni nazw, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="0de19-175">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="0de19-176">Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-176">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="0de19-177">`Sub`Domyślnie procedur dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="0de19-177">`Sub` procedures default to public access.</span></span> <span data-ttu-id="0de19-178">Modyfikatory dostępu można dostosować ich poziomy dostępu.</span><span class="sxs-lookup"><span data-stu-id="0de19-178">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="0de19-179">Jeśli procedura używa `Implements` — słowo kluczowe, zawierające klasy lub struktury musi mieć `Implements` instrukcji poniższą jego `Class` lub `Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0de19-179">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="0de19-180">`Implements` Instrukcja musi zawierać każdy interfejs, który jest określony w `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="0de19-180">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="0de19-181">Jednak nazwy za pomocą którego definiuje interfejs `Sub` (w `definedname`) nie musi być zgodna z nazwą w tej procedurze (w `name`).</span><span class="sxs-lookup"><span data-stu-id="0de19-181">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="0de19-182">Zwracanie z procedurę Sub</span><span class="sxs-lookup"><span data-stu-id="0de19-182">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="0de19-183">Gdy `Sub` procedura zwraca do kodu wywołującego, wykonanie będzie kontynuowane przy użyciu instrukcji następującej po instrukcji, która ją.</span><span class="sxs-lookup"><span data-stu-id="0de19-183">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="0de19-184">W poniższym przykładzie przedstawiono typ zwracany `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="0de19-184">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="0de19-185">`Exit Sub` i `Return` instrukcje powoduje natychmiastowe wyjście z `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="0de19-185">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="0de19-186">Dowolną liczbę `Exit Sub` i `Return` instrukcje mogą występować w dowolnym miejscu w procedurze, a można mieszać `Exit Sub` i `Return` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="0de19-186">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="0de19-187">Wywołanie procedury Sub</span><span class="sxs-lookup"><span data-stu-id="0de19-187">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="0de19-188">Należy wywołać `Sub` procedury przy użyciu nazwy procedury w instrukcji i następnie wykonując tej nazwy z listą argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="0de19-188">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="0de19-189">Można pominąć nawiasów, tylko wtedy, gdy nie podawaj żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="0de19-189">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="0de19-190">Jednak kod jest bardziej przejrzysta zawsze używać nawiasów.</span><span class="sxs-lookup"><span data-stu-id="0de19-190">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="0de19-191">A `Sub` procedury i `Function` procedura może mieć parametrów i wykonać serię instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0de19-191">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="0de19-192">Jednak `Function` procedury zwraca wartość i a `Sub` nie procedury.</span><span class="sxs-lookup"><span data-stu-id="0de19-192">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="0de19-193">W związku z tym nie można użyć `Sub` procedury w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="0de19-193">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="0de19-194">Można użyć `Call` — słowo kluczowe podczas wywoływania `Sub` procedura, ale tego słowa kluczowego nie jest zalecane w przypadku zastosowań.</span><span class="sxs-lookup"><span data-stu-id="0de19-194">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="0de19-195">Aby uzyskać więcej informacji, zobacz [instrukcji Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-195">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="0de19-196">Visual Basic Reorganizuje czasami wyrażenia arytmetyczne, aby zwiększyć wydajność wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="0de19-196">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="0de19-197">Z tego powodu jeśli lista argumentów zawiera wyrażeń, które wywołują inne procedury możesz nie należy założyć, że te wyrażenia zostanie wywołana w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="0de19-197">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="0de19-198">Async Sub — procedury</span><span class="sxs-lookup"><span data-stu-id="0de19-198">Async Sub Procedures</span></span>  
 <span data-ttu-id="0de19-199">Korzystając z funkcji asynchronicznych, można wywołać funkcji asynchronicznych bez za pomocą jawnego wywołania zwrotne i ręcznie dzielenia kodu wielu funkcji lub wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="0de19-199">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="0de19-200">Jeśli procedura o [Async](../modifiers/async.md) modyfikator, można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w procedurze.</span><span class="sxs-lookup"><span data-stu-id="0de19-200">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="0de19-201">Gdy kontrolować osiągnie `Await` wyrażenie w `Async` procedury kontroli zwraca wywołującego i postępu w procedurze jest wstrzymana, aż do zakończenia zadań oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="0de19-201">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="0de19-202">Po zakończeniu zadania wykonywania można wznowić w procedurze.</span><span class="sxs-lookup"><span data-stu-id="0de19-202">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0de19-203">`Async` Procedury zwraca do wywołującego po napotkaniu albo pierwszego oczekiwano obiekt, który nie został jeszcze ukończony lub na końcu `Async` osiągnięciu procedury cokolwiek nastąpi najpierw.</span><span class="sxs-lookup"><span data-stu-id="0de19-203">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="0de19-204">Można również zaznaczyć [instrukcji Function](function-statement.md) z `Async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="0de19-204">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="0de19-205">`Async` Funkcja może mieć typ zwracany <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="0de19-205">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="0de19-206">Przykład później w tym temacie przedstawiono `Async` funkcja, która ma typ zwracany <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="0de19-206">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="0de19-207">`Async``Sub` procedury są używane przede wszystkim do obsługi zdarzeń, których nie można zwrócić wartość.</span><span class="sxs-lookup"><span data-stu-id="0de19-207">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="0de19-208">`Async``Sub` Procedura nie jest oczekiwane oraz funkcji wywołującej `Async``Sub` procedury nie przechwytuje wyjątków który `Sub` zgłasza procedury.</span><span class="sxs-lookup"><span data-stu-id="0de19-208">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="0de19-209">`Async` Procedury nie można zadeklarować żadnego [ByRef](../modifiers/byref.md) parametrów.</span><span class="sxs-lookup"><span data-stu-id="0de19-209">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="0de19-210">Aby uzyskać więcej informacji na temat `Async` procedury, zobacz [programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md), [przepływ sterowania w aplikacjach asynchronicznych](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async zwracać typów](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="0de19-210">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0de19-211">Przykład</span><span class="sxs-lookup"><span data-stu-id="0de19-211">Example</span></span>  
 <span data-ttu-id="0de19-212">W poniższym przykładzie użyto `Sub` instrukcji, aby zdefiniować nazwę, parametry i kod, który tworzą treści `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="0de19-212">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="0de19-213">Przykład</span><span class="sxs-lookup"><span data-stu-id="0de19-213">Example</span></span>  
 <span data-ttu-id="0de19-214">W poniższym przykładzie `DelayAsync` jest `Async``Function` mający typ zwracany <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="0de19-214">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="0de19-215">`DelayAsync`ma `Return` instrukcji, która zwraca liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="0de19-215">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="0de19-216">W związku z tym funkcja deklaracja `DelayAsync` musi mieć typ zwracany `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="0de19-216">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="0de19-217">Ponieważ typ zwracany jest `Task(Of Integer)`, oceny `Await` wyrażenie w `DoSomethingAsync` tworzy całkowitą, jak przedstawiono na poniższym instrukcji: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="0de19-217">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="0de19-218">`startButton_Click` Procedura jest przykładem `Async Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="0de19-218">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="0de19-219">Ponieważ `DoSomethingAsync` jest `Async` funkcji, zadanie dla wywołania `DoSomethingAsync` musi być oczekiwane, jak przedstawiono na poniższym instrukcji: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="0de19-219">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="0de19-220">`startButton_Click``Sub` Procedury musi być zdefiniowany za pomocą `Async` modyfikator ponieważ ma ona `Await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="0de19-220">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0de19-221">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0de19-221">See Also</span></span>  
 [<span data-ttu-id="0de19-222">Implements, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0de19-222">Implements Statement</span></span>](implements-statement.md)  
 [<span data-ttu-id="0de19-223">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0de19-223">Function Statement</span></span>](function-statement.md)  
 [<span data-ttu-id="0de19-224">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="0de19-224">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="0de19-225">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0de19-225">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="0de19-226">Call, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0de19-226">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="0de19-227">Z</span><span class="sxs-lookup"><span data-stu-id="0de19-227">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="0de19-228">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="0de19-228">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="0de19-229">Instrukcje: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="0de19-229">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="0de19-230">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="0de19-230">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="0de19-231">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="0de19-231">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
