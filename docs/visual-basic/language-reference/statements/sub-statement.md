---
title: Sub, instrukcja
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
ms.openlocfilehash: e50b79c31c92ac116d6c82bcececba3340894d74
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404177"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="f5bfd-102">Sub — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5bfd-102">Sub Statement (Visual Basic)</span></span>

<span data-ttu-id="f5bfd-103">Deklaruje nazwę, parametry i kod definiujący `Sub` procedurę.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="f5bfd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5bfd-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a><span data-ttu-id="f5bfd-105">Części</span><span class="sxs-lookup"><span data-stu-id="f5bfd-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="f5bfd-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-106">Optional.</span></span> <span data-ttu-id="f5bfd-107">Zobacz [listę atrybutów](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-107">See [Attribute List](attribute-list.md).</span></span>

- `Partial`

  <span data-ttu-id="f5bfd-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-108">Optional.</span></span> <span data-ttu-id="f5bfd-109">Wskazuje definicję metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="f5bfd-110">Zobacz [metody częściowe](../../programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-110">See [Partial Methods](../../programming-guide/language-features/procedures/partial-methods.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="f5bfd-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-111">Optional.</span></span> <span data-ttu-id="f5bfd-112">Może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f5bfd-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="f5bfd-113">Społeczeństwo</span><span class="sxs-lookup"><span data-stu-id="f5bfd-113">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="f5bfd-114">Chronione</span><span class="sxs-lookup"><span data-stu-id="f5bfd-114">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="f5bfd-115">Osoby</span><span class="sxs-lookup"><span data-stu-id="f5bfd-115">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="f5bfd-116">Użytek</span><span class="sxs-lookup"><span data-stu-id="f5bfd-116">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="f5bfd-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="f5bfd-117">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="f5bfd-118">Prywatne chronione</span><span class="sxs-lookup"><span data-stu-id="f5bfd-118">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="f5bfd-119">Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-119">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="f5bfd-120">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-120">Optional.</span></span> <span data-ttu-id="f5bfd-121">Może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f5bfd-121">Can be one of the following:</span></span>

  - [<span data-ttu-id="f5bfd-122">Przeciążenia</span><span class="sxs-lookup"><span data-stu-id="f5bfd-122">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="f5bfd-123">Przesłonięcia</span><span class="sxs-lookup"><span data-stu-id="f5bfd-123">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="f5bfd-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="f5bfd-124">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="f5bfd-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="f5bfd-125">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="f5bfd-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="f5bfd-126">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="f5bfd-127">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-127">Optional.</span></span> <span data-ttu-id="f5bfd-128">Zobacz [udostępnianie](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-128">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="f5bfd-129">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-129">Optional.</span></span> <span data-ttu-id="f5bfd-130">Zobacz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-130">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="f5bfd-131">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-131">Optional.</span></span> <span data-ttu-id="f5bfd-132">Zobacz [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-132">See [Async](../modifiers/async.md).</span></span>

- `name`

  <span data-ttu-id="f5bfd-133">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-133">Required.</span></span> <span data-ttu-id="f5bfd-134">Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-134">Name of the procedure.</span></span> <span data-ttu-id="f5bfd-135">Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-135">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="f5bfd-136">Aby utworzyć procedurę konstruktora dla klasy, należy ustawić nazwę `Sub` procedury dla `New` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="f5bfd-137">Aby uzyskać więcej informacji, zobacz [okres istnienia obiektu: sposób tworzenia i zniszczenia obiektów](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="f5bfd-138">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-138">Optional.</span></span> <span data-ttu-id="f5bfd-139">Lista parametrów typu dla procedury ogólnej.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="f5bfd-140">Zobacz [Lista typów](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-140">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="f5bfd-141">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-141">Optional.</span></span> <span data-ttu-id="f5bfd-142">Lista nazw zmiennych lokalnych reprezentujących parametry tej procedury.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="f5bfd-143">Zobacz [listę parametrów](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-143">See [Parameter List](parameter-list.md).</span></span>

- `Implements`

  <span data-ttu-id="f5bfd-144">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-144">Optional.</span></span> <span data-ttu-id="f5bfd-145">Wskazuje, że ta procedura implementuje jedną lub więcej `Sub` procedur, każda zdefiniowana w interfejsie implementowanym przez tę procedurę zawierającą klasę lub strukturę.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="f5bfd-146">Zobacz [instrukcja Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-146">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="f5bfd-147">Wymagane, jeśli `Implements` jest podany.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="f5bfd-148">Lista `Sub` implementowanych procedur.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-148">List of `Sub` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="f5bfd-149">Każda `implementedprocedure` z nich ma następującą składnię i części:</span><span class="sxs-lookup"><span data-stu-id="f5bfd-149">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="f5bfd-150">Część</span><span class="sxs-lookup"><span data-stu-id="f5bfd-150">Part</span></span>|<span data-ttu-id="f5bfd-151">Opis</span><span class="sxs-lookup"><span data-stu-id="f5bfd-151">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="f5bfd-152">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-152">Required.</span></span> <span data-ttu-id="f5bfd-153">Nazwa interfejsu implementowanego przez tę procedurę zawierającą klasę lub strukturę.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="f5bfd-154">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-154">Required.</span></span> <span data-ttu-id="f5bfd-155">Nazwa, przez którą procedura jest zdefiniowana `interface` .</span><span class="sxs-lookup"><span data-stu-id="f5bfd-155">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="f5bfd-156">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-156">Optional.</span></span> <span data-ttu-id="f5bfd-157">Wskazuje, że ta procedura może obsłużyć jedno lub więcej konkretnych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="f5bfd-158">Zobacz [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-158">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="f5bfd-159">Wymagane, jeśli `Handles` jest podany.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="f5bfd-160">Lista zdarzeń, których dotyczy ta procedura.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-160">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="f5bfd-161">Każda `eventspecifier` z nich ma następującą składnię i części:</span><span class="sxs-lookup"><span data-stu-id="f5bfd-161">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="f5bfd-162">Część</span><span class="sxs-lookup"><span data-stu-id="f5bfd-162">Part</span></span>|<span data-ttu-id="f5bfd-163">Opis</span><span class="sxs-lookup"><span data-stu-id="f5bfd-163">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="f5bfd-164">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-164">Required.</span></span> <span data-ttu-id="f5bfd-165">Zmienna obiektu zadeklarowana z typem danych klasy lub struktury, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="f5bfd-166">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-166">Required.</span></span> <span data-ttu-id="f5bfd-167">Nazwa zdarzenia, którego dotyczy ta procedura.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-167">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="f5bfd-168">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-168">Optional.</span></span> <span data-ttu-id="f5bfd-169">Blok instrukcji do uruchomienia w ramach tej procedury.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-169">Block of statements to run within this procedure.</span></span>

- `End Sub`

  <span data-ttu-id="f5bfd-170">Kończy definicję tej procedury.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-170">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5bfd-171">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5bfd-171">Remarks</span></span>

<span data-ttu-id="f5bfd-172">Cały kod wykonywalny musi znajdować się wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="f5bfd-173">Użyj `Sub` procedury, gdy nie chcesz zwracać wartości do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="f5bfd-174">Użyj `Function` procedury, jeśli chcesz zwrócić wartość.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-174">Use a `Function` procedure when you want to return a value.</span></span>

## <a name="defining-a-sub-procedure"></a><span data-ttu-id="f5bfd-175">Definiowanie procedury Sub</span><span class="sxs-lookup"><span data-stu-id="f5bfd-175">Defining a Sub Procedure</span></span>

<span data-ttu-id="f5bfd-176">Procedurę można zdefiniować `Sub` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="f5bfd-177">Kontekst deklaracji procedury Sub musi, dlatego, być klasą, strukturą, modułem lub interfejsem i nie może być plikiem źródłowym, przestrzenią nazw, procedurą lub blokiem.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="f5bfd-178">Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="f5bfd-179">`Sub`procedury domyślne do dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="f5bfd-180">Poziomy dostępu można dostosować za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-180">You can adjust their access levels by using the access modifiers.</span></span>

<span data-ttu-id="f5bfd-181">Jeśli procedura używa `Implements` słowa kluczowego, Klasa lub struktura, która musi występować `Implements` bezpośrednio po `Class` `Structure` instrukcji or.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="f5bfd-182">`Implements`Instrukcja musi zawierać wszystkie interfejsy, które są określone w `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="f5bfd-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="f5bfd-183">Jednak nazwa, za pomocą której interfejs definiuje `Sub` (w), `definedname` nie musi być zgodna z nazwą tej procedury (w programie `name` ).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>

## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="f5bfd-184">Powrót z procedury Sub</span><span class="sxs-lookup"><span data-stu-id="f5bfd-184">Returning from a Sub Procedure</span></span>

<span data-ttu-id="f5bfd-185">Gdy `Sub` procedura zwraca kod wywołujący, wykonywanie jest kontynuowane za pomocą instrukcji po instrukcji, która go wywołała.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>

<span data-ttu-id="f5bfd-186">Poniższy przykład przedstawia powrót z `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-186">The following example shows a return from a `Sub` procedure.</span></span>

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

<span data-ttu-id="f5bfd-187">`Exit Sub`Instrukcje i `Return` powodują natychmiastowe wyjście z `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="f5bfd-188">Dowolna liczba `Exit Sub` `Return` instrukcji i może występować w dowolnym miejscu procedury i można mieszać i wypełniać `Exit Sub` `Return` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>

## <a name="calling-a-sub-procedure"></a><span data-ttu-id="f5bfd-189">Wywoływanie procedury Sub</span><span class="sxs-lookup"><span data-stu-id="f5bfd-189">Calling a Sub Procedure</span></span>

<span data-ttu-id="f5bfd-190">Należy wywołać `Sub` procedurę przy użyciu nazwy procedury w instrukcji, a następnie po tej nazwie z listą argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="f5bfd-191">Nawiasy można pominąć tylko wtedy, gdy nie podasz żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="f5bfd-192">Jednak kod jest bardziej czytelny, jeśli zawsze zawiera nawiasy.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-192">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="f5bfd-193">`Sub`Procedura i `Function` procedura mogą mieć parametry i wykonywać serie instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="f5bfd-194">Jednak `Function` procedura zwraca wartość, a `Sub` procedura nie jest.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="f5bfd-195">W związku z tym nie można użyć `Sub` procedury w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>

<span data-ttu-id="f5bfd-196">Możesz użyć `Call` słowa kluczowego podczas wywoływania `Sub` procedury, ale nie jest to zalecane w przypadku większości użycia.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="f5bfd-197">Aby uzyskać więcej informacji, zobacz [wywoływanie instrukcji](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-197">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="f5bfd-198">Visual Basic czasami ponownie rozmieszcza wyrażenia arytmetyczne w celu zwiększenia wydajności wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="f5bfd-199">Z tego powodu, jeśli lista argumentów zawiera wyrażenia, które wywołują inne procedury, nie należy zakładać, że te wyrażenia będą wywoływane w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>

## <a name="async-sub-procedures"></a><span data-ttu-id="f5bfd-200">Procedury podrzędne Async</span><span class="sxs-lookup"><span data-stu-id="f5bfd-200">Async Sub Procedures</span></span>

<span data-ttu-id="f5bfd-201">Za pomocą funkcji asynchronicznej można wywoływać funkcje asynchroniczne bez używania jawnych wywołań zwrotnych lub ręcznie podzielić kod w wielu funkcjach lub wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="f5bfd-202">Jeśli oznaczesz procedurę za pomocą modyfikatora [asynchronicznego](../modifiers/async.md) , możesz użyć operatora [await](../operators/await-operator.md) w procedurze.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="f5bfd-203">Gdy kontrolka osiągnie `Await` wyrażenie w `Async` procedurze, sterowanie powraca do obiektu wywołującego, a postęp w procedurze jest zawieszony do momentu zakończenia zadania oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="f5bfd-204">Po zakończeniu zadania wykonanie może zostać wznowione w procedurze.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-204">When the task is complete, execution can resume in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="f5bfd-205">`Async`Procedura powraca do obiektu wywołującego, gdy wystąpił pierwszy oczekujący obiekt, który nie został jeszcze ukończony lub `Async` osiągnięto koniec procedury, w zależności od tego, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>

<span data-ttu-id="f5bfd-206">Można także oznaczyć [instrukcję Function](function-statement.md) z `Async` modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="f5bfd-207">`Async`Funkcja może mieć zwracany typ <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="f5bfd-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="f5bfd-208">Przykład w dalszej części tego tematu pokazuje `Async` funkcję, która ma zwracany typ <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="f5bfd-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="f5bfd-209">`Async``Sub`procedury są używane głównie dla programów obsługi zdarzeń, w których nie można zwrócić wartości.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="f5bfd-210">`Async` `Sub` Nie można oczekiwać procedury, a obiekt wywołujący `Async` `Sub` procedury nie może przechwytywać wyjątków, które `Sub` procedura zgłasza.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-210">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>

<span data-ttu-id="f5bfd-211">`Async`Procedura nie może zadeklarować żadnych parametrów [ByRef](../modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="f5bfd-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="f5bfd-212">Aby uzyskać więcej informacji na temat `Async` procedur, zobacz [programowanie asynchroniczne przy użyciu asynchronicznych i oczekujących](../../programming-guide/concepts/async/index.md), [przepływu sterowania w programach asynchronicznych](../../programming-guide/concepts/async/control-flow-in-async-programs.md)i [asynchronicznych typów zwracanych](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfd-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="f5bfd-213">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5bfd-213">Example</span></span>

<span data-ttu-id="f5bfd-214">Poniższy przykład używa instrukcji, `Sub` Aby zdefiniować nazwę, parametry i kod, który stanowi treść `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a><span data-ttu-id="f5bfd-215">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5bfd-215">Example</span></span>

<span data-ttu-id="f5bfd-216">W poniższym przykładzie `DelayAsync` jest to, `Async` `Function` który ma zwracany typ <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="f5bfd-216">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="f5bfd-217">`DelayAsync`zawiera `Return` instrukcję zwracającą liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="f5bfd-218">W związku z tym, deklaracja funkcji `DelayAsync` musi mieć typ zwracany `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="f5bfd-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="f5bfd-219">Ponieważ typem zwracanym jest `Task(Of Integer)` , obliczanie `Await` wyrażenia w `DoSomethingAsync` tworzy liczbę całkowitą, jak pokazano w poniższej instrukcji: `Dim result As Integer = Await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="f5bfd-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="f5bfd-220">`startButton_Click`Procedura jest przykładem `Async Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="f5bfd-221">Ponieważ `DoSomethingAsync` jest `Async` funkcją, zadanie dla wywołania `DoSomethingAsync` musi być oczekiwane, jak pokazano w poniższej instrukcji: `Await DoSomethingAsync()` .</span><span class="sxs-lookup"><span data-stu-id="f5bfd-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="f5bfd-222">`startButton_Click` `Sub` Procedura musi być zdefiniowana z `Async` modyfikatorem, ponieważ ma `Await` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="f5bfd-222">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="f5bfd-223">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5bfd-223">See also</span></span>

- [<span data-ttu-id="f5bfd-224">Implements — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="f5bfd-224">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="f5bfd-225">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f5bfd-225">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="f5bfd-226">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="f5bfd-226">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="f5bfd-227">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f5bfd-227">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="f5bfd-228">Call, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f5bfd-228">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="f5bfd-229">Z</span><span class="sxs-lookup"><span data-stu-id="f5bfd-229">Of</span></span>](of-clause.md)
- [<span data-ttu-id="f5bfd-230">Parameter — Tablice</span><span class="sxs-lookup"><span data-stu-id="f5bfd-230">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="f5bfd-231">Instrukcje: Używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="f5bfd-231">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="f5bfd-232">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="f5bfd-232">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="f5bfd-233">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="f5bfd-233">Partial Methods</span></span>](../../programming-guide/language-features/procedures/partial-methods.md)
