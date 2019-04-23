---
title: 'Instrukcje: Utwórz procedurę, która zwraca wartość (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 115c1df4bd49d5848d72c4cbd0242a49a12740c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335501"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="d768f-102">Instrukcje: Utwórz procedurę, która zwraca wartość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d768f-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="d768f-103">Możesz użyć `Function` procedury w celu zwrócenia wartości do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="d768f-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="d768f-104">Aby utworzyć procedurę, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="d768f-104">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="d768f-105">Poza innej procedury, należy użyć `Function` instrukcji, następuje `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d768f-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="d768f-106">W `Function` instrukcji, postępuj zgodnie z `Function` — słowo kluczowe o nazwie procedury oraz lista parametrów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="d768f-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="d768f-107">Postępuj zgodnie z nawiasów za pomocą `As` klauzuli, aby określić typ danych zwróconej wartości.</span><span class="sxs-lookup"><span data-stu-id="d768f-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="d768f-108">Umieść instrukcje kod procedury między `Function` i `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d768f-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="d768f-109">Użyj `Return` instrukcji, aby zwrócić wartości do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="d768f-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="d768f-110">Następujące `Function` procedury oblicza najdłuższy bok lub przeciwprostokątnej trójkąta prostokątnego, biorąc pod uwagę wartości dla obu stron.</span><span class="sxs-lookup"><span data-stu-id="d768f-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="d768f-111">W poniższym przykładzie przedstawiono typowe wywołanie `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="d768f-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="d768f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d768f-112">See also</span></span>

- [<span data-ttu-id="d768f-113">Procedury</span><span class="sxs-lookup"><span data-stu-id="d768f-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d768f-114">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="d768f-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="d768f-115">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="d768f-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="d768f-116">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="d768f-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="d768f-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="d768f-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d768f-118">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d768f-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="d768f-119">Instrukcje: Zwracanie wartości z procedury</span><span class="sxs-lookup"><span data-stu-id="d768f-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="d768f-120">Instrukcje: Wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="d768f-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
