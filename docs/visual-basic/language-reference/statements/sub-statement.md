---
title: Sub — Instrukcja
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
ms.openlocfilehash: da498a5e0a3633eb98882aaed145fcd21ab169fd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346440"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="4fc8c-102">Sub — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fc8c-102">Sub Statement (Visual Basic)</span></span>

<span data-ttu-id="4fc8c-103">Deklaruje nazwę, parametry i kod definiujący procedurę `Sub`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="4fc8c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4fc8c-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a><span data-ttu-id="4fc8c-105">Części</span><span class="sxs-lookup"><span data-stu-id="4fc8c-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="4fc8c-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-106">Optional.</span></span> <span data-ttu-id="4fc8c-107">Zobacz [listę atrybutów](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-107">See [Attribute List](attribute-list.md).</span></span>

- `Partial`

  <span data-ttu-id="4fc8c-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-108">Optional.</span></span> <span data-ttu-id="4fc8c-109">Wskazuje definicję metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="4fc8c-110">Zobacz [metody częściowe](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="4fc8c-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-111">Optional.</span></span> <span data-ttu-id="4fc8c-112">Może to być jeden z następujących modyfikatorów dostępu:</span><span class="sxs-lookup"><span data-stu-id="4fc8c-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="4fc8c-113">Public</span><span class="sxs-lookup"><span data-stu-id="4fc8c-113">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="4fc8c-114">Protected</span><span class="sxs-lookup"><span data-stu-id="4fc8c-114">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="4fc8c-115">Friend</span><span class="sxs-lookup"><span data-stu-id="4fc8c-115">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="4fc8c-116">Private</span><span class="sxs-lookup"><span data-stu-id="4fc8c-116">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="4fc8c-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="4fc8c-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="4fc8c-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="4fc8c-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

  <span data-ttu-id="4fc8c-119">Zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="4fc8c-120">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-120">Optional.</span></span> <span data-ttu-id="4fc8c-121">Może to być jeden z następujących modyfikatorów dostępu:</span><span class="sxs-lookup"><span data-stu-id="4fc8c-121">Can be one of the following:</span></span>

  - [<span data-ttu-id="4fc8c-122">Overloads</span><span class="sxs-lookup"><span data-stu-id="4fc8c-122">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="4fc8c-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="4fc8c-123">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="4fc8c-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="4fc8c-124">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="4fc8c-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="4fc8c-125">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="4fc8c-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="4fc8c-126">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="4fc8c-127">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-127">Optional.</span></span> <span data-ttu-id="4fc8c-128">Zobacz [udostępnianie](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-128">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="4fc8c-129">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-129">Optional.</span></span> <span data-ttu-id="4fc8c-130">Zobacz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-130">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="4fc8c-131">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-131">Optional.</span></span> <span data-ttu-id="4fc8c-132">Zobacz [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-132">See [Async](../modifiers/async.md).</span></span>

- `name`

  <span data-ttu-id="4fc8c-133">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-133">Required.</span></span> <span data-ttu-id="4fc8c-134">Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-134">Name of the procedure.</span></span> <span data-ttu-id="4fc8c-135">Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-135">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="4fc8c-136">Aby utworzyć procedurę konstruktora dla klasy, należy ustawić nazwę procedury `Sub` na słowo kluczowe `New`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="4fc8c-137">Aby uzyskać więcej informacji, zobacz [okres istnienia obiektu: sposób tworzenia i zniszczenia obiektów](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="4fc8c-138">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-138">Optional.</span></span> <span data-ttu-id="4fc8c-139">Lista parametrów typu dla procedury ogólnej.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="4fc8c-140">Zobacz [Lista typów](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-140">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="4fc8c-141">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-141">Optional.</span></span> <span data-ttu-id="4fc8c-142">Lista nazw zmiennych lokalnych reprezentujących parametry tej procedury.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="4fc8c-143">Zobacz [listę parametrów](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-143">See [Parameter List](parameter-list.md).</span></span>

- `Implements`

  <span data-ttu-id="4fc8c-144">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-144">Optional.</span></span> <span data-ttu-id="4fc8c-145">Wskazuje, że ta procedura implementuje co najmniej jedną `Sub` procedury, każda z nich zdefiniowana w interfejsie zaimplementowanym przez tę procedurę zawierającą klasę lub strukturę.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="4fc8c-146">Zobacz [instrukcja Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-146">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="4fc8c-147">Wymagane, jeśli podano `Implements`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="4fc8c-148">Lista implementowanych procedur `Sub`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-148">List of `Sub` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="4fc8c-149">Każda `implementedprocedure` ma następującą składnię i części:</span><span class="sxs-lookup"><span data-stu-id="4fc8c-149">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="4fc8c-150">Części</span><span class="sxs-lookup"><span data-stu-id="4fc8c-150">Part</span></span>|<span data-ttu-id="4fc8c-151">Opis</span><span class="sxs-lookup"><span data-stu-id="4fc8c-151">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="4fc8c-152">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-152">Required.</span></span> <span data-ttu-id="4fc8c-153">Nazwa interfejsu implementowanego przez tę procedurę zawierającą klasę lub strukturę.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="4fc8c-154">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-154">Required.</span></span> <span data-ttu-id="4fc8c-155">Nazwa, przez którą procedura jest definiowana w `interface`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-155">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="4fc8c-156">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-156">Optional.</span></span> <span data-ttu-id="4fc8c-157">Wskazuje, że ta procedura może obsłużyć jedno lub więcej konkretnych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="4fc8c-158">Zobacz [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-158">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="4fc8c-159">Wymagane, jeśli podano `Handles`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="4fc8c-160">Lista zdarzeń, których dotyczy ta procedura.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-160">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="4fc8c-161">Każda `eventspecifier` ma następującą składnię i części:</span><span class="sxs-lookup"><span data-stu-id="4fc8c-161">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="4fc8c-162">Części</span><span class="sxs-lookup"><span data-stu-id="4fc8c-162">Part</span></span>|<span data-ttu-id="4fc8c-163">Opis</span><span class="sxs-lookup"><span data-stu-id="4fc8c-163">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="4fc8c-164">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-164">Required.</span></span> <span data-ttu-id="4fc8c-165">Zmienna obiektu zadeklarowana z typem danych klasy lub struktury, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="4fc8c-166">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-166">Required.</span></span> <span data-ttu-id="4fc8c-167">Nazwa zdarzenia, którego dotyczy ta procedura.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-167">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="4fc8c-168">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-168">Optional.</span></span> <span data-ttu-id="4fc8c-169">Blok instrukcji do uruchomienia w ramach tej procedury.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-169">Block of statements to run within this procedure.</span></span>

- `End Sub`

  <span data-ttu-id="4fc8c-170">Kończy definicję tej procedury.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-170">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="4fc8c-171">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4fc8c-171">Remarks</span></span>

<span data-ttu-id="4fc8c-172">Cały kod wykonywalny musi znajdować się wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="4fc8c-173">Użyj procedury `Sub`, jeśli nie chcesz zwracać wartości do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="4fc8c-174">Użyj procedury `Function`, jeśli chcesz zwrócić wartość.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-174">Use a `Function` procedure when you want to return a value.</span></span>

## <a name="defining-a-sub-procedure"></a><span data-ttu-id="4fc8c-175">Definiowanie procedury Sub</span><span class="sxs-lookup"><span data-stu-id="4fc8c-175">Defining a Sub Procedure</span></span>

<span data-ttu-id="4fc8c-176">Procedurę `Sub` można zdefiniować tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="4fc8c-177">Kontekst deklaracji procedury Sub musi, dlatego, być klasą, strukturą, modułem lub interfejsem i nie może być plikiem źródłowym, przestrzenią nazw, procedurą lub blokiem.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="4fc8c-178">Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="4fc8c-179">`Sub` procedury domyślne do dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="4fc8c-180">Poziomy dostępu można dostosować za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-180">You can adjust their access levels by using the access modifiers.</span></span>

<span data-ttu-id="4fc8c-181">Jeśli procedura używa słowa kluczowego `Implements`, zawierająca klasę lub strukturę musi mieć instrukcję `Implements`, która natychmiast następuje po `Class` lub `Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="4fc8c-182">Instrukcja `Implements` musi zawierać każdy interfejs, który jest określony w `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="4fc8c-183">Jednak nazwa, za pomocą której interfejs definiuje `Sub` (w `definedname`), nie musi być zgodna z nazwą tej procedury (w `name`).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>

## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="4fc8c-184">Powrót z procedury Sub</span><span class="sxs-lookup"><span data-stu-id="4fc8c-184">Returning from a Sub Procedure</span></span>

<span data-ttu-id="4fc8c-185">Gdy `Sub` procedura zwraca kod wywołujący, wykonywanie jest kontynuowane za pomocą instrukcji po instrukcji, która go wywołała.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>

<span data-ttu-id="4fc8c-186">Poniższy przykład przedstawia zwrot z procedury `Sub`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-186">The following example shows a return from a `Sub` procedure.</span></span>

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

<span data-ttu-id="4fc8c-187">Instrukcje `Exit Sub` i `Return` powodują natychmiastowe wyjście z procedury `Sub`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="4fc8c-188">Dowolna liczba instrukcji `Exit Sub` i `Return` może występować w dowolnym miejscu procedury i można mieszać instrukcje `Exit Sub` i `Return`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>

## <a name="calling-a-sub-procedure"></a><span data-ttu-id="4fc8c-189">Wywoływanie procedury Sub</span><span class="sxs-lookup"><span data-stu-id="4fc8c-189">Calling a Sub Procedure</span></span>

<span data-ttu-id="4fc8c-190">Procedurę `Sub` można wywołać przy użyciu nazwy procedury w instrukcji, a następnie po tej nazwie z listą argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="4fc8c-191">Nawiasy można pominąć tylko wtedy, gdy nie podasz żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="4fc8c-192">Jednak kod jest bardziej czytelny, jeśli zawsze zawiera nawiasy.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-192">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="4fc8c-193">Procedura `Sub` i procedura `Function` mogą mieć parametry i wykonywać serie instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="4fc8c-194">Jednak procedura `Function` zwraca wartość, a procedura `Sub`a nie.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="4fc8c-195">W związku z tym nie można użyć `Sub` procedury w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>

<span data-ttu-id="4fc8c-196">Można użyć słowa kluczowego `Call` podczas wywoływania procedury `Sub`, ale nie jest to zalecane w przypadku większości użycia.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="4fc8c-197">Aby uzyskać więcej informacji, zobacz [wywoływanie instrukcji](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-197">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="4fc8c-198">Visual Basic czasami ponownie rozmieszcza wyrażenia arytmetyczne w celu zwiększenia wydajności wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="4fc8c-199">Z tego powodu, jeśli lista argumentów zawiera wyrażenia, które wywołują inne procedury, nie należy zakładać, że te wyrażenia będą wywoływane w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>

## <a name="async-sub-procedures"></a><span data-ttu-id="4fc8c-200">Procedury podrzędne Async</span><span class="sxs-lookup"><span data-stu-id="4fc8c-200">Async Sub Procedures</span></span>

<span data-ttu-id="4fc8c-201">Za pomocą funkcji asynchronicznej można wywoływać funkcje asynchroniczne bez używania jawnych wywołań zwrotnych lub ręcznie podzielić kod w wielu funkcjach lub wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="4fc8c-202">Jeśli oznaczesz procedurę za pomocą modyfikatora [asynchronicznego](../modifiers/async.md) , możesz użyć operatora [await](../../../visual-basic/language-reference/operators/await-operator.md) w procedurze.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="4fc8c-203">Gdy kontrolka osiągnie wyrażenie `Await` w procedurze `Async`, sterowanie powraca do obiektu wywołującego, a postęp w procedurze jest zawieszony do momentu ukończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="4fc8c-204">Po zakończeniu zadania wykonanie może zostać wznowione w procedurze.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-204">When the task is complete, execution can resume in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="4fc8c-205">Procedura `Async` powraca do obiektu wywołującego, gdy wystąpił pierwszy oczekujący obiekt, który nie został jeszcze ukończony lub osiągnięto koniec procedury `Async`, w zależności od tego, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>

<span data-ttu-id="4fc8c-206">Można także oznaczyć [instrukcję Function](function-statement.md) z modyfikatorem `Async`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="4fc8c-207">Funkcja `Async` może mieć zwracany typ <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="4fc8c-208">Przykład w dalszej części tego tematu pokazuje funkcję `Async`, która ma zwracany typ <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="4fc8c-209">procedury `Sub` `Async` są używane głównie dla programów obsługi zdarzeń, w których nie można zwrócić wartości.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="4fc8c-210">Nie można oczekiwać `Async` procedury `Sub`, a obiekt wywołujący procedury `Async` `Sub` nie może przechwytywać wyjątków, które zgłasza procedura `Sub`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-210">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>

<span data-ttu-id="4fc8c-211">Procedura `Async` nie może zadeklarować żadnych parametrów [ByRef](../modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="4fc8c-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="4fc8c-212">Aby uzyskać więcej informacji na temat procedur `Async`, zobacz [programowanie asynchroniczne z asynchroniczne i await](../../../visual-basic/programming-guide/concepts/async/index.md), [przepływ sterowania w programach asynchronicznych](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)i [asynchroniczne typy zwracane](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="4fc8c-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="4fc8c-213">Przykład</span><span class="sxs-lookup"><span data-stu-id="4fc8c-213">Example</span></span>

<span data-ttu-id="4fc8c-214">Poniższy przykład używa instrukcji `Sub`, aby zdefiniować nazwę, parametry i kod, który stanowi treść procedury `Sub`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a><span data-ttu-id="4fc8c-215">Przykład</span><span class="sxs-lookup"><span data-stu-id="4fc8c-215">Example</span></span>

<span data-ttu-id="4fc8c-216">W poniższym przykładzie `DelayAsync` jest `Async` `Function`, który ma zwracany typ <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-216">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="4fc8c-217">`DelayAsync` zawiera instrukcję `Return`, która zwraca liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="4fc8c-218">W związku z tym deklaracja funkcji `DelayAsync` musi mieć typ zwracany `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="4fc8c-219">Ponieważ zwracany typ jest `Task(Of Integer)`, Obliczanie wyrażenia `Await` w `DoSomethingAsync` tworzy liczbę całkowitą, jak pokazano w poniższej instrukcji: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="4fc8c-220">Procedura `startButton_Click` jest przykładem procedury `Async Sub`owej.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="4fc8c-221">Ponieważ `DoSomethingAsync` jest funkcją `Async`, zadanie dla wywołania `DoSomethingAsync` musi być oczekiwane, jak pokazano w poniższej instrukcji: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="4fc8c-222">Procedura `startButton_Click` `Sub` musi być zdefiniowana za pomocą modyfikatora `Async`, ponieważ ma wyrażenie `Await`.</span><span class="sxs-lookup"><span data-stu-id="4fc8c-222">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="4fc8c-223">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4fc8c-223">See also</span></span>

- [<span data-ttu-id="4fc8c-224">Implements, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4fc8c-224">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="4fc8c-225">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4fc8c-225">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="4fc8c-226">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="4fc8c-226">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="4fc8c-227">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4fc8c-227">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="4fc8c-228">Call, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4fc8c-228">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="4fc8c-229">Z</span><span class="sxs-lookup"><span data-stu-id="4fc8c-229">Of</span></span>](of-clause.md)
- [<span data-ttu-id="4fc8c-230">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="4fc8c-230">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="4fc8c-231">Instrukcje: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="4fc8c-231">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="4fc8c-232">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="4fc8c-232">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="4fc8c-233">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="4fc8c-233">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
