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
ms.openlocfilehash: 1f386694bd7425ee530b9305ab684b730f9b73c8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832635"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="89ce1-102">Exit — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89ce1-102">Exit Statement (Visual Basic)</span></span>
<span data-ttu-id="89ce1-103">Opuszcza procedurę lub blok i natychmiast przekazuje sterowanie do instrukcji następującej po wywołaniu procedury lub definicji bloku.</span><span class="sxs-lookup"><span data-stu-id="89ce1-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89ce1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="89ce1-104">Syntax</span></span>  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a><span data-ttu-id="89ce1-105">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="89ce1-105">Statements</span></span>  
 `Exit Do`  
 <span data-ttu-id="89ce1-106">Natychmiast kończy działanie `Do` pętli, w którym pojawia się.</span><span class="sxs-lookup"><span data-stu-id="89ce1-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="89ce1-107">Wykonywanie jest kontynuowane przy użyciu następujących instrukcji `Loop` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="89ce1-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="89ce1-108">`Exit Do` można używać tylko wewnątrz `Do` pętli.</span><span class="sxs-lookup"><span data-stu-id="89ce1-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="89ce1-109">Gdy jest używana w ramach zagnieżdżonych `Do` pętli, `Exit Do` opuszcza pętlę najbardziej i przekazuje sterowanie do następnego wyższy poziom zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="89ce1-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit For`  
 <span data-ttu-id="89ce1-110">Natychmiast kończy działanie `For` pętli, w którym pojawia się.</span><span class="sxs-lookup"><span data-stu-id="89ce1-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="89ce1-111">Wykonywanie jest kontynuowane przy użyciu następujących instrukcji `Next` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="89ce1-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="89ce1-112">`Exit For` można używać tylko wewnątrz `For`... `Next` lub `For Each`... `Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="89ce1-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="89ce1-113">Gdy jest używana w ramach zagnieżdżonych `For` pętli, `Exit For` opuszcza pętlę najbardziej i przekazuje sterowanie do następnego wyższy poziom zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="89ce1-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit Function`  
 <span data-ttu-id="89ce1-114">Natychmiast kończy działanie `Function` procedury, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="89ce1-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="89ce1-115">Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji, która wywołała `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="89ce1-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="89ce1-116">`Exit Function` można używać tylko wewnątrz `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="89ce1-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>  
  
 <span data-ttu-id="89ce1-117">Aby określić wartość zwracana, można przypisać wartości do nazwy funkcji w wierszu przed `Exit Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="89ce1-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="89ce1-118">Aby przypisać wartość zwracaną i zakończyć działanie funkcji w jednej instrukcji, należy użyć [instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="89ce1-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 `Exit Property`  
 <span data-ttu-id="89ce1-119">Natychmiast kończy działanie `Property` procedury, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="89ce1-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="89ce1-120">Wykonywanie jest kontynuowane przy użyciu instrukcji, która wywołuje `Property` procedura, oznacza to, za pomocą instrukcji żądania lub ustawiania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="89ce1-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="89ce1-121">`Exit Property` można używać tylko wewnątrz właściwości `Get` lub `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="89ce1-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>  
  
 <span data-ttu-id="89ce1-122">Aby określić wartości zwracanej w `Get` procedury, można przypisać wartości do nazwy funkcji w wierszu przed `Exit Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="89ce1-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="89ce1-123">Aby przypisać wartość zwracaną i zakończenia `Get` procedury w jednej instrukcji, należy użyć `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="89ce1-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>  
  
 <span data-ttu-id="89ce1-124">W `Set` procedury `Exit Property` instrukcja jest odpowiednikiem `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="89ce1-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Select`  
 <span data-ttu-id="89ce1-125">Natychmiast kończy działanie `Select Case` bloku, w którym pojawia się.</span><span class="sxs-lookup"><span data-stu-id="89ce1-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="89ce1-126">Wykonywanie jest kontynuowane przy użyciu następujących instrukcji `End Select` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="89ce1-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="89ce1-127">`Exit Select` można używać tylko wewnątrz `Select Case` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="89ce1-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>  
  
 `Exit Sub`  
 <span data-ttu-id="89ce1-128">Natychmiast kończy działanie `Sub` procedury, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="89ce1-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="89ce1-129">Wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji, która wywołała `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="89ce1-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="89ce1-130">`Exit Sub` można używać tylko wewnątrz `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="89ce1-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="89ce1-131">W `Sub` procedury `Exit Sub` instrukcja jest odpowiednikiem `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="89ce1-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Try`  
 <span data-ttu-id="89ce1-132">Natychmiast kończy działanie `Try` lub `Catch` bloku, w którym pojawia się.</span><span class="sxs-lookup"><span data-stu-id="89ce1-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="89ce1-133">Wykonywanie jest kontynuowane przy użyciu `Finally` zablokować, jeśli istnieje, lub przy użyciu następujących instrukcji `End Try` instrukcji, w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="89ce1-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="89ce1-134">`Exit Try` można używać tylko wewnątrz `Try` lub `Catch` bloku, a nie w obrębie `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="89ce1-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>  
  
 `Exit While`  
 <span data-ttu-id="89ce1-135">Natychmiast kończy działanie `While` pętli, w którym pojawia się.</span><span class="sxs-lookup"><span data-stu-id="89ce1-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="89ce1-136">Wykonywanie jest kontynuowane przy użyciu następujących instrukcji `End While` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="89ce1-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="89ce1-137">`Exit While` można używać tylko wewnątrz `While` pętli.</span><span class="sxs-lookup"><span data-stu-id="89ce1-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="89ce1-138">Gdy jest używana w ramach zagnieżdżonych `While` pętli, `Exit While` przekazuje sterowanie do pętli, która znajduje się na poziomie zagnieżdżonych powyżej pętli gdzie `Exit While` występuje.</span><span class="sxs-lookup"><span data-stu-id="89ce1-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89ce1-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89ce1-139">Remarks</span></span>  
 <span data-ttu-id="89ce1-140">Nie należy mylić `Exit` instrukcje `End` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="89ce1-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="89ce1-141">`Exit` Definiuje końcem instrukcji.</span><span class="sxs-lookup"><span data-stu-id="89ce1-141">`Exit` does not define the end of a statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89ce1-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="89ce1-142">Example</span></span>  
 <span data-ttu-id="89ce1-143">W poniższym przykładzie, warunek pętli zatrzymuje pętli po `index` zmiennej jest większa niż 100.</span><span class="sxs-lookup"><span data-stu-id="89ce1-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="89ce1-144">`If` Instrukcji w pętli, jednak powoduje `Exit Do` instrukcję, aby zatrzymanie pętli, gdy zmienna index jest większy niż 10.</span><span class="sxs-lookup"><span data-stu-id="89ce1-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="89ce1-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="89ce1-145">Example</span></span>  
 <span data-ttu-id="89ce1-146">Poniższy przykład przypisuje wartość zwracaną do nazwy funkcji `myFunction`, a następnie używa `Exit Function` zostać zwrócony przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="89ce1-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="89ce1-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="89ce1-147">Example</span></span>  
 <span data-ttu-id="89ce1-148">W poniższym przykładzie użyto [instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md) do przypisywania wartości zwracanej i zakończyć działanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="89ce1-148">The following example uses the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) to assign the return value and exit the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="89ce1-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89ce1-149">See also</span></span>

- [<span data-ttu-id="89ce1-150">Continue, instrukcja</span><span class="sxs-lookup"><span data-stu-id="89ce1-150">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
- [<span data-ttu-id="89ce1-151">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="89ce1-151">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="89ce1-152">Instrukcja End</span><span class="sxs-lookup"><span data-stu-id="89ce1-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
- [<span data-ttu-id="89ce1-153">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="89ce1-153">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="89ce1-154">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="89ce1-154">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="89ce1-155">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="89ce1-155">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="89ce1-156">Return, instrukcja</span><span class="sxs-lookup"><span data-stu-id="89ce1-156">Return Statement</span></span>](../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="89ce1-157">Stop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="89ce1-157">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="89ce1-158">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="89ce1-158">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="89ce1-159">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="89ce1-159">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
