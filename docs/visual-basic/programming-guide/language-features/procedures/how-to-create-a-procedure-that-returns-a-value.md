---
title: 'Porady: tworzenie procedury, która zwraca wartość (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 472f55173a4897a23a82812a2b24bf1646c1a6ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648440"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="8f392-102">Porady: tworzenie procedury, która zwraca wartość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f392-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="8f392-103">Możesz użyć `Function` procedury, aby zwrócić wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="8f392-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="8f392-104">Aby utworzyć procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="8f392-104">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="8f392-105">Poza innej procedury należy użyć `Function` instrukcji, a następnie `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8f392-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="8f392-106">W `Function` instrukcji, wykonaj `Function` — słowo kluczowe o nazwie procedury i listy parametrów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="8f392-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="8f392-107">Postępuj zgodnie z nawiasy `As` klauzuli, aby określić typ danych wartości zwróconej.</span><span class="sxs-lookup"><span data-stu-id="8f392-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4.  <span data-ttu-id="8f392-108">Umieść instrukcji kodu procedury między `Function` i `End Function` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="8f392-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5.  <span data-ttu-id="8f392-109">Użyj `Return` instrukcji, aby zwrócić wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="8f392-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="8f392-110">Następujące `Function` procedury oblicza najdłuższego boku lub przeciwprostokątnej trójkąta prawo podanych wartości dla obu stron.</span><span class="sxs-lookup"><span data-stu-id="8f392-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     <span data-ttu-id="8f392-111">W poniższym przykładzie przedstawiono typowe wywołania `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="8f392-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8f392-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f392-112">See Also</span></span>  
 [<span data-ttu-id="8f392-113">Procedury</span><span class="sxs-lookup"><span data-stu-id="8f392-113">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="8f392-114">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="8f392-114">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="8f392-115">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="8f392-115">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="8f392-116">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="8f392-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="8f392-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="8f392-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="8f392-118">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8f392-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="8f392-119">Instrukcje: zwracanie wartości z procedury</span><span class="sxs-lookup"><span data-stu-id="8f392-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="8f392-120">Instrukcje: wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="8f392-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
