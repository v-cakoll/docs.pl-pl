---
title: Exit — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 9c25653809c51662ea5b606ab97be6a9b50d5986
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956932"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="29d0a-102">Exit — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29d0a-102">Exit Statement (Visual Basic)</span></span>

<span data-ttu-id="29d0a-103">Zamyka procedurę lub blok i natychmiast przenosi kontrolę do instrukcji następującej po wywołaniu procedury lub definicji bloku.</span><span class="sxs-lookup"><span data-stu-id="29d0a-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="29d0a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29d0a-104">Syntax</span></span>

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a><span data-ttu-id="29d0a-105">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="29d0a-105">Statements</span></span>

 `Exit Do`  
 <span data-ttu-id="29d0a-106">Natychmiast opuszcza pętlę `Do`, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="29d0a-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="29d0a-107">Wykonywanie jest kontynuowane za pomocą instrukcji następującej po instrukcji `Loop`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="29d0a-108">`Exit Do` można używać tylko wewnątrz pętli `Do`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="29d0a-109">W przypadku użycia w zagnieżdżonych pętlach `Do` `Exit Do` opuszcza wewnętrzna pętla i przenosi kontrolę na następny wyższy poziom zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="29d0a-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit For`  
 <span data-ttu-id="29d0a-110">Natychmiast opuszcza pętlę `For`, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="29d0a-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="29d0a-111">Wykonywanie jest kontynuowane za pomocą instrukcji następującej po instrukcji `Next`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="29d0a-112">`Exit For` może być używany tylko wewnątrz `For`... `Next` lub `For Each`... `Next` pętla.</span><span class="sxs-lookup"><span data-stu-id="29d0a-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="29d0a-113">W przypadku użycia w zagnieżdżonych pętlach `For` `Exit For` opuszcza wewnętrzna pętla i przenosi kontrolę na następny wyższy poziom zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="29d0a-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit Function`  
 <span data-ttu-id="29d0a-114">Natychmiast opuszcza procedurę `Function`, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="29d0a-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="29d0a-115">Wykonywanie jest kontynuowane przy użyciu instrukcji, która wywołała procedurę `Function`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="29d0a-116">`Exit Function` może być używany tylko w procedurze `Function`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>

 <span data-ttu-id="29d0a-117">Aby określić wartość zwracaną, można przypisać wartość do nazwy funkcji w wierszu przed instrukcją `Exit Function`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="29d0a-118">Aby przypisać wartość zwracaną i zamknąć funkcję w jednej instrukcji, zamiast tego można użyć [instrukcji return](return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29d0a-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).</span></span>

 `Exit Property`  
 <span data-ttu-id="29d0a-119">Natychmiast opuszcza procedurę `Property`, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="29d0a-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="29d0a-120">Wykonywanie jest kontynuowane przy użyciu instrukcji, która wywołała procedurę `Property`, czyli z instrukcją żądającą lub ustawieniem wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="29d0a-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="29d0a-121">`Exit Property` może być używany tylko w procedurze `Get` lub `Set`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>

 <span data-ttu-id="29d0a-122">Aby określić wartość zwracaną w procedurze `Get`, można przypisać wartość do nazwy funkcji w wierszu przed instrukcją `Exit Property`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="29d0a-123">Aby przypisać wartość zwracaną i zamknąć procedurę `Get` w jednej instrukcji, można zamiast tego użyć instrukcji `Return`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>

 <span data-ttu-id="29d0a-124">W procedurze `Set` instrukcja `Exit Property` jest równoważna instrukcji `Return`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>

 `Exit Select`  
 <span data-ttu-id="29d0a-125">Natychmiast zamyka blok `Select Case`, w którym występuje.</span><span class="sxs-lookup"><span data-stu-id="29d0a-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="29d0a-126">Wykonywanie jest kontynuowane za pomocą instrukcji następującej po instrukcji `End Select`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="29d0a-127">`Exit Select` można używać tylko wewnątrz instrukcji `Select Case`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>

 `Exit Sub`  
 <span data-ttu-id="29d0a-128">Natychmiast opuszcza procedurę `Sub`, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="29d0a-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="29d0a-129">Wykonywanie jest kontynuowane przy użyciu instrukcji, która wywołała procedurę `Sub`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="29d0a-130">`Exit Sub` może być używany tylko w procedurze `Sub`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>

 <span data-ttu-id="29d0a-131">W procedurze `Sub` instrukcja `Exit Sub` jest równoważna instrukcji `Return`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>

 `Exit Try`  
 <span data-ttu-id="29d0a-132">Natychmiast zamyka blok `Try` lub `Catch`, w którym występuje.</span><span class="sxs-lookup"><span data-stu-id="29d0a-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="29d0a-133">Wykonywanie jest kontynuowane z blokiem `Finally`, jeśli istnieje, lub instrukcji następującej po instrukcji `End Try` inaczej.</span><span class="sxs-lookup"><span data-stu-id="29d0a-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="29d0a-134">`Exit Try` można używać tylko wewnątrz bloku `Try` lub `Catch`, a nie wewnątrz bloku `Finally`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>

 `Exit While`  
 <span data-ttu-id="29d0a-135">Natychmiast opuszcza pętlę `While`, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="29d0a-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="29d0a-136">Wykonywanie jest kontynuowane za pomocą instrukcji następującej po instrukcji `End While`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="29d0a-137">`Exit While` można używać tylko wewnątrz pętli `While`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="29d0a-138">Gdy jest używany w zagnieżdżonych pętlach `While`, `Exit While` przenosi kontrolkę do pętli, która jest jednym zagnieżdżonym poziomem powyżej pętli, w której występuje `Exit While`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>

## <a name="remarks"></a><span data-ttu-id="29d0a-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29d0a-139">Remarks</span></span>

<span data-ttu-id="29d0a-140">Nie należy mylić instrukcji `Exit` z instrukcjami `End`.</span><span class="sxs-lookup"><span data-stu-id="29d0a-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="29d0a-141">`Exit` nie definiuje końca instrukcji.</span><span class="sxs-lookup"><span data-stu-id="29d0a-141">`Exit` does not define the end of a statement.</span></span>

## <a name="example"></a><span data-ttu-id="29d0a-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="29d0a-142">Example</span></span>

<span data-ttu-id="29d0a-143">W poniższym przykładzie warunek pętli przerywa pętlę, gdy zmienna `index` jest większa niż 100.</span><span class="sxs-lookup"><span data-stu-id="29d0a-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="29d0a-144">Instrukcja `If` w pętli, jednak powoduje, że instrukcja `Exit Do` zatrzyma pętlę, gdy zmienna indeksu jest większa niż 10.</span><span class="sxs-lookup"><span data-stu-id="29d0a-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a><span data-ttu-id="29d0a-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="29d0a-145">Example</span></span>

<span data-ttu-id="29d0a-146">Poniższy przykład przypisuje wartość zwracaną do nazwy funkcji `myFunction`, a następnie używa `Exit Function` do zwrócenia z funkcji:</span><span class="sxs-lookup"><span data-stu-id="29d0a-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a><span data-ttu-id="29d0a-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="29d0a-147">Example</span></span>

<span data-ttu-id="29d0a-148">Poniższy przykład używa [instrukcji return](return-statement.md) do przypisania wartości zwracanej i opuszczenia funkcji:</span><span class="sxs-lookup"><span data-stu-id="29d0a-148">The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="29d0a-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29d0a-149">See also</span></span>

- [<span data-ttu-id="29d0a-150">Continue, instrukcja</span><span class="sxs-lookup"><span data-stu-id="29d0a-150">Continue Statement</span></span>](continue-statement.md)
- [<span data-ttu-id="29d0a-151">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="29d0a-151">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="29d0a-152">End, instrukcja</span><span class="sxs-lookup"><span data-stu-id="29d0a-152">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="29d0a-153">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="29d0a-153">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="29d0a-154">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="29d0a-154">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="29d0a-155">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="29d0a-155">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="29d0a-156">Return, instrukcja</span><span class="sxs-lookup"><span data-stu-id="29d0a-156">Return Statement</span></span>](return-statement.md)
- [<span data-ttu-id="29d0a-157">Stop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="29d0a-157">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="29d0a-158">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="29d0a-158">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="29d0a-159">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="29d0a-159">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
