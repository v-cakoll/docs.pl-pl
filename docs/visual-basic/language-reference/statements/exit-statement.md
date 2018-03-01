---
title: "Exit — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2df63ecbf0605d07296e1692f18b1b015e27cd03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="5f6b9-102">Exit — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f6b9-102">Exit Statement (Visual Basic)</span></span>
<span data-ttu-id="5f6b9-103">Opuszcza procedurę lub blok i natychmiast przenosi formantu do instrukcji następującej wywołanie procedury lub definicji bloku.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f6b9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f6b9-104">Syntax</span></span>  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a><span data-ttu-id="5f6b9-105">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="5f6b9-105">Statements</span></span>  
 `Exit Do`  
 <span data-ttu-id="5f6b9-106">Natychmiast kończy pracę `Do` pętli, w którym pojawi się.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="5f6b9-107">Kontynuuje wykonywanie instrukcji następującej `Loop` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="5f6b9-108">`Exit Do`można używać tylko wewnątrz `Do` pętli.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="5f6b9-109">Gdy jest używany w zagnieżdżonych `Do` pętli, `Exit Do` kończy tryb pętli najbardziej i przekazuje sterowanie do następnego wyższego poziomu zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit For`  
 <span data-ttu-id="5f6b9-110">Natychmiast kończy pracę `For` pętli, w którym pojawi się.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="5f6b9-111">Kontynuuje wykonywanie instrukcji następującej `Next` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="5f6b9-112">`Exit For`można używać tylko wewnątrz `For`... `Next` lub `For Each`... `Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="5f6b9-113">Gdy jest używany w zagnieżdżonych `For` pętli, `Exit For` kończy tryb pętli najbardziej i przekazuje sterowanie do następnego wyższego poziomu zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit Function`  
 <span data-ttu-id="5f6b9-114">Natychmiast kończy pracę `Function` procedury, w których występuje.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="5f6b9-115">Kontynuuje wykonywanie instrukcji następującej po instrukcji, która wywołała `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="5f6b9-116">`Exit Function`można używać tylko wewnątrz `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>  
  
 <span data-ttu-id="5f6b9-117">Aby określić wartość zwracaną, można przypisać wartość Nazwa funkcji w wierszu przed `Exit Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="5f6b9-118">Aby przypisać wartości zwracanej i zakończyć działanie funkcji w jednej instrukcji, należy użyć [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5f6b9-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 `Exit Property`  
 <span data-ttu-id="5f6b9-119">Natychmiast kończy pracę `Property` procedury, w których występuje.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="5f6b9-120">Kontynuuje wykonywanie instrukcji, która wywołuje `Property` procedury, czyli z instrukcją żądania lub ustawiania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="5f6b9-121">`Exit Property`można używać tylko wewnątrz właściwości `Get` lub `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>  
  
 <span data-ttu-id="5f6b9-122">Aby określić wartości zwracanej w `Get` procedury, można przypisać wartość Nazwa funkcji w wierszu przed `Exit Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="5f6b9-123">Można przypisać wartości zwracanej i zakończenia `Get` procedury w jednej instrukcji, należy użyć `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>  
  
 <span data-ttu-id="5f6b9-124">W `Set` procedury `Exit Property` instrukcja jest odpowiednikiem `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Select`  
 <span data-ttu-id="5f6b9-125">Natychmiast kończy pracę `Select Case` blok, w którym pojawi się.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="5f6b9-126">Kontynuuje wykonywanie instrukcji następującej `End Select` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="5f6b9-127">`Exit Select`można używać tylko wewnątrz `Select Case` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>  
  
 `Exit Sub`  
 <span data-ttu-id="5f6b9-128">Natychmiast kończy pracę `Sub` procedury, w których występuje.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="5f6b9-129">Kontynuuje wykonywanie instrukcji następującej po instrukcji, która wywołała `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="5f6b9-130">`Exit Sub`można używać tylko wewnątrz `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="5f6b9-131">W `Sub` procedury `Exit Sub` instrukcja jest odpowiednikiem `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Try`  
 <span data-ttu-id="5f6b9-132">Natychmiast kończy pracę `Try` lub `Catch` blok, w którym pojawi się.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="5f6b9-133">Kontynuuje wykonywanie `Finally` zablokować, jeśli istnieje, lub z następujących instrukcji `End Try` instrukcji w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="5f6b9-134">`Exit Try`można używać tylko wewnątrz `Try` lub `Catch` bloku, a nie do wewnątrz `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>  
  
 `Exit While`  
 <span data-ttu-id="5f6b9-135">Natychmiast kończy pracę `While` pętli, w którym pojawi się.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="5f6b9-136">Kontynuuje wykonywanie instrukcji następującej `End While` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="5f6b9-137">`Exit While`można używać tylko wewnątrz `While` pętli.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="5f6b9-138">Gdy jest używany w zagnieżdżonych `While` pętle, `Exit While` przekazuje sterowanie do pętli o jeden poziom zagnieżdżony powyżej pętli gdzie `Exit While` występuje.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f6b9-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f6b9-139">Remarks</span></span>  
 <span data-ttu-id="5f6b9-140">Nie należy mylić `Exit` instrukcji z `End` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="5f6b9-141">`Exit`nie definiuje końca instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-141">`Exit` does not define the end of a statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f6b9-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f6b9-142">Example</span></span>  
 <span data-ttu-id="5f6b9-143">W poniższym przykładzie warunek pętli zatrzymuje pętli podczas `index` zmiennej jest większa niż 100.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="5f6b9-144">`If` Instrukcji w pętli, jednak powoduje `Exit Do` instrukcji, aby zatrzymać pętli, gdy zmienna indeksu jest większa niż 10.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="5f6b9-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f6b9-145">Example</span></span>  
 <span data-ttu-id="5f6b9-146">Poniższy przykład przypisuje wartość zwracaną nazwą funkcji `myFunction`, a następnie używa `Exit Function` ma zostać zwrócony przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="5f6b9-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f6b9-147">Example</span></span>  
 <span data-ttu-id="5f6b9-148">W poniższym przykładzie użyto [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md) do przypisywania wartości zwracanej i zakończyć działanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="5f6b9-148">The following example uses the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) to assign the return value and exit the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5f6b9-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f6b9-149">See Also</span></span>  
 [<span data-ttu-id="5f6b9-150">Continue — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5f6b9-150">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)  
 [<span data-ttu-id="5f6b9-151">Czy... Loop — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5f6b9-151">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="5f6b9-152">End — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5f6b9-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)  
 [<span data-ttu-id="5f6b9-153">For Each... Next — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5f6b9-153">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="5f6b9-154">Dla... Next — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5f6b9-154">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="5f6b9-155">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5f6b9-155">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="5f6b9-156">Return — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5f6b9-156">Return Statement</span></span>](../../../visual-basic/language-reference/statements/return-statement.md)  
 [<span data-ttu-id="5f6b9-157">Stop — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5f6b9-157">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [<span data-ttu-id="5f6b9-158">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5f6b9-158">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="5f6b9-159">Try... CATCH... Finally — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5f6b9-159">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
