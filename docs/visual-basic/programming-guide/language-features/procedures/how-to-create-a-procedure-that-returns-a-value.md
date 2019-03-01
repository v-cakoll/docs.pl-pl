---
title: 'Instrukcje: Utwórz procedurę, która zwraca wartość (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: ce0010762374baf5b19ab2e64f50e12fefda2dee
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966981"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="0bc9c-102">Instrukcje: Utwórz procedurę, która zwraca wartość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bc9c-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="0bc9c-103">Możesz użyć `Function` procedury w celu zwrócenia wartości do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="0bc9c-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="0bc9c-104">Aby utworzyć procedurę, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="0bc9c-104">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="0bc9c-105">Poza innej procedury, należy użyć `Function` instrukcji, następuje `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0bc9c-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="0bc9c-106">W `Function` instrukcji, postępuj zgodnie z `Function` — słowo kluczowe o nazwie procedury oraz lista parametrów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="0bc9c-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="0bc9c-107">Postępuj zgodnie z nawiasów za pomocą `As` klauzuli, aby określić typ danych zwróconej wartości.</span><span class="sxs-lookup"><span data-stu-id="0bc9c-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4.  <span data-ttu-id="0bc9c-108">Umieść instrukcje kod procedury między `Function` i `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0bc9c-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5.  <span data-ttu-id="0bc9c-109">Użyj `Return` instrukcji, aby zwrócić wartości do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="0bc9c-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="0bc9c-110">Następujące `Function` procedury oblicza najdłuższy bok lub przeciwprostokątnej trójkąta prostokątnego, biorąc pod uwagę wartości dla obu stron.</span><span class="sxs-lookup"><span data-stu-id="0bc9c-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="0bc9c-111">W poniższym przykładzie przedstawiono typowe wywołanie `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="0bc9c-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0bc9c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0bc9c-112">See also</span></span>
- [<span data-ttu-id="0bc9c-113">Procedury</span><span class="sxs-lookup"><span data-stu-id="0bc9c-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="0bc9c-114">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="0bc9c-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="0bc9c-115">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="0bc9c-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="0bc9c-116">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="0bc9c-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="0bc9c-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="0bc9c-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0bc9c-118">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0bc9c-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="0bc9c-119">Instrukcje: Zwracanie wartości z procedury</span><span class="sxs-lookup"><span data-stu-id="0bc9c-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="0bc9c-120">Instrukcje: Wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="0bc9c-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
