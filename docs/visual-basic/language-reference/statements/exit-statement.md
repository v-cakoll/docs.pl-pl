---
title: Exit, instrukcja
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
ms.openlocfilehash: 1bfe81428fd3c50663fd8978e05c6a945cd47df8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345938"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="54fd9-102">Exit — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54fd9-102">Exit Statement (Visual Basic)</span></span>

<span data-ttu-id="54fd9-103">Zamyka procedurę lub blok i natychmiast przenosi kontrolę do instrukcji następującej po wywołaniu procedury lub definicji bloku.</span><span class="sxs-lookup"><span data-stu-id="54fd9-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="54fd9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54fd9-104">Syntax</span></span>

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a><span data-ttu-id="54fd9-105">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="54fd9-105">Statements</span></span>

 `Exit Do`  
 <span data-ttu-id="54fd9-106">Natychmiast zamyka pętlę `Do`, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="54fd9-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="54fd9-107">Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji `Loop`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="54fd9-108">`Exit Do` można używać tylko wewnątrz pętli `Do`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="54fd9-109">W przypadku użycia w zagnieżdżonych pętlach `Do` `Exit Do` opuszcza najbardziej zachodzącą pętlę i przenosi kontrolę na następny wyższy poziom zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="54fd9-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit For`  
 <span data-ttu-id="54fd9-110">Natychmiast zamyka pętlę `For`, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="54fd9-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="54fd9-111">Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji `Next`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="54fd9-112">`Exit For` można używać tylko wewnątrz pętli `For`...`Next` lub `For Each`...`Next`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="54fd9-113">W przypadku użycia w zagnieżdżonych pętlach `For` `Exit For` opuszcza najbardziej zachodzącą pętlę i przenosi kontrolę na następny wyższy poziom zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="54fd9-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit Function`  
 <span data-ttu-id="54fd9-114">Natychmiast opuszcza procedurę `Function`, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="54fd9-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="54fd9-115">Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji, która wywołała procedurę `Function`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="54fd9-116">`Exit Function` można używać tylko wewnątrz procedury `Function`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>

 <span data-ttu-id="54fd9-117">Aby określić wartość zwracaną, można przypisać wartość do nazwy funkcji w wierszu przed instrukcją `Exit Function`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="54fd9-118">Aby przypisać wartość zwracaną i zamknąć funkcję w jednej instrukcji, zamiast tego można użyć [instrukcji return](return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="54fd9-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).</span></span>

 `Exit Property`  
 <span data-ttu-id="54fd9-119">Natychmiast opuszcza procedurę `Property`, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="54fd9-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="54fd9-120">Wykonywanie jest kontynuowane przy użyciu instrukcji, która wywołała procedurę `Property`, czyli z instrukcją żądającą lub ustawieniem wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="54fd9-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="54fd9-121">`Exit Property` można używać tylko wewnątrz procedury `Get` lub `Set`j właściwości.</span><span class="sxs-lookup"><span data-stu-id="54fd9-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>

 <span data-ttu-id="54fd9-122">Aby określić wartość zwracaną w procedurze `Get`, można przypisać wartość do nazwy funkcji w wierszu przed instrukcją `Exit Property`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="54fd9-123">Aby przypisać wartość zwracaną i zamknąć procedurę `Get` w jednej instrukcji, można zamiast tego użyć instrukcji `Return`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>

 <span data-ttu-id="54fd9-124">W procedurze `Set` instrukcja `Exit Property` jest równoważna instrukcji `Return`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>

 `Exit Select`  
 <span data-ttu-id="54fd9-125">Natychmiast zamyka blok `Select Case`, w którym występuje.</span><span class="sxs-lookup"><span data-stu-id="54fd9-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="54fd9-126">Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji `End Select`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="54fd9-127">`Exit Select` można używać tylko wewnątrz instrukcji `Select Case`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>

 `Exit Sub`  
 <span data-ttu-id="54fd9-128">Natychmiast opuszcza procedurę `Sub`, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="54fd9-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="54fd9-129">Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji, która wywołała procedurę `Sub`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="54fd9-130">`Exit Sub` można używać tylko wewnątrz procedury `Sub`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>

 <span data-ttu-id="54fd9-131">W procedurze `Sub` instrukcja `Exit Sub` jest równoważna instrukcji `Return`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>

 `Exit Try`  
 <span data-ttu-id="54fd9-132">Natychmiast zamyka blok `Try` lub `Catch`, w którym występuje.</span><span class="sxs-lookup"><span data-stu-id="54fd9-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="54fd9-133">Wykonywanie jest kontynuowane z blokiem `Finally`, jeśli istnieje, lub instrukcji po instrukcji `End Try` w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="54fd9-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="54fd9-134">`Exit Try` można używać tylko wewnątrz bloku `Try` lub `Catch`, a nie wewnątrz bloku `Finally`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>

 `Exit While`  
 <span data-ttu-id="54fd9-135">Natychmiast zamyka pętlę `While`, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="54fd9-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="54fd9-136">Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji `End While`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="54fd9-137">`Exit While` można używać tylko wewnątrz pętli `While`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="54fd9-138">Gdy jest używany w zagnieżdżonych pętlach `While`, `Exit While` przenosi kontrolkę do pętli, która jest jednym zagnieżdżonym poziomem powyżej pętli, w której występuje `Exit While`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>

## <a name="remarks"></a><span data-ttu-id="54fd9-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54fd9-139">Remarks</span></span>

<span data-ttu-id="54fd9-140">Nie należy mylić instrukcji `Exit` z instrukcjami `End`.</span><span class="sxs-lookup"><span data-stu-id="54fd9-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="54fd9-141">`Exit` nie definiuje końca instrukcji.</span><span class="sxs-lookup"><span data-stu-id="54fd9-141">`Exit` does not define the end of a statement.</span></span>

## <a name="example"></a><span data-ttu-id="54fd9-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="54fd9-142">Example</span></span>

<span data-ttu-id="54fd9-143">W poniższym przykładzie warunek pętli przerywa pętlę, gdy zmienna `index` jest większa niż 100.</span><span class="sxs-lookup"><span data-stu-id="54fd9-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="54fd9-144">Instrukcja `If` w pętli, jednak powoduje, że instrukcja `Exit Do` przerywa pętlę, gdy zmienna indeksu jest większa niż 10.</span><span class="sxs-lookup"><span data-stu-id="54fd9-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a><span data-ttu-id="54fd9-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="54fd9-145">Example</span></span>

<span data-ttu-id="54fd9-146">Poniższy przykład przypisuje wartość zwracaną do nazwy funkcji `myFunction`, a następnie używa `Exit Function` do powrotu z funkcji:</span><span class="sxs-lookup"><span data-stu-id="54fd9-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a><span data-ttu-id="54fd9-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="54fd9-147">Example</span></span>

<span data-ttu-id="54fd9-148">Poniższy przykład używa [instrukcji return](return-statement.md) do przypisania wartości zwracanej i opuszczenia funkcji:</span><span class="sxs-lookup"><span data-stu-id="54fd9-148">The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="54fd9-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54fd9-149">See also</span></span>

- [<span data-ttu-id="54fd9-150">Continue, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fd9-150">Continue Statement</span></span>](continue-statement.md)
- [<span data-ttu-id="54fd9-151">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fd9-151">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="54fd9-152">End, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fd9-152">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="54fd9-153">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fd9-153">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="54fd9-154">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fd9-154">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="54fd9-155">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fd9-155">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="54fd9-156">Return, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fd9-156">Return Statement</span></span>](return-statement.md)
- [<span data-ttu-id="54fd9-157">Stop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fd9-157">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="54fd9-158">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fd9-158">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="54fd9-159">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54fd9-159">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
