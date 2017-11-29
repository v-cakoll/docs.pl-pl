---
title: "Porady: tworzenie procedury, która zwraca wartość (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 787eddc1fd1cdb9dd6b655a8556b75044b2a49dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="e3de6-102">Porady: tworzenie procedury, która zwraca wartość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3de6-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="e3de6-103">Możesz użyć `Function` procedury, aby zwrócić wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="e3de6-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="e3de6-104">Aby utworzyć procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="e3de6-104">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="e3de6-105">Poza innej procedury należy użyć `Function` instrukcji, a następnie `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e3de6-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="e3de6-106">W `Function` instrukcji, wykonaj `Function` — słowo kluczowe o nazwie procedury i listy parametrów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="e3de6-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="e3de6-107">Postępuj zgodnie z nawiasy `As` klauzuli, aby określić typ danych wartości zwróconej.</span><span class="sxs-lookup"><span data-stu-id="e3de6-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4.  <span data-ttu-id="e3de6-108">Umieść instrukcji kodu procedury między `Function` i `End Function` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="e3de6-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5.  <span data-ttu-id="e3de6-109">Użyj `Return` instrukcji, aby zwrócić wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="e3de6-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="e3de6-110">Następujące `Function` procedury oblicza najdłuższego boku lub przeciwprostokątnej trójkąta prawo podanych wartości dla obu stron.</span><span class="sxs-lookup"><span data-stu-id="e3de6-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     <span data-ttu-id="e3de6-111">W poniższym przykładzie przedstawiono typowe wywołania `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="e3de6-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e3de6-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3de6-112">See Also</span></span>  
 [<span data-ttu-id="e3de6-113">Procedury</span><span class="sxs-lookup"><span data-stu-id="e3de6-113">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="e3de6-114">Sub — procedury</span><span class="sxs-lookup"><span data-stu-id="e3de6-114">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="e3de6-115">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="e3de6-115">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="e3de6-116">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="e3de6-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="e3de6-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="e3de6-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="e3de6-118">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e3de6-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="e3de6-119">Porady: zwracanie wartości z procedury</span><span class="sxs-lookup"><span data-stu-id="e3de6-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="e3de6-120">Porady: wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="e3de6-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
