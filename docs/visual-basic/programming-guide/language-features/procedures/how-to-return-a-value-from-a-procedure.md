---
title: 'Instrukcje: Zwracanie wartości z procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 45f175de647887a406f8ae87dae492a5fe58cca9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976736"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="cbe83-102">Instrukcje: Zwracanie wartości z procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbe83-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="cbe83-103">A `Function` procedury zwraca wartość do wywołującego kodu albo wykonując `Return` instrukcji lub napotkania `Exit Function` lub `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cbe83-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="cbe83-104">Zwraca wartość, przy użyciu instrukcji Return</span><span class="sxs-lookup"><span data-stu-id="cbe83-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="cbe83-105">Umieść `Return` instrukcji w punkcie, w której procedury zadanie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="cbe83-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="cbe83-106">Postępuj zgodnie z `Return` — słowo kluczowe z wyrażeniem, które zwracają wartości mają być zwracane do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="cbe83-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="cbe83-107">Masz więcej niż jedną `Return` instrukcji w tej samej procedury.</span><span class="sxs-lookup"><span data-stu-id="cbe83-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="cbe83-108">Następujące `Function` procedury oblicza najdłuższy bok lub przeciwprostokątnej trójkąta prostokątnego i zwraca go do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="cbe83-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="cbe83-109">W poniższym przykładzie przedstawiono typowe wywołanie `hypotenuse`, która przechowuje zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="cbe83-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="cbe83-110">Zwraca wartość, przy użyciu funkcji Exit lub End</span><span class="sxs-lookup"><span data-stu-id="cbe83-110">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="cbe83-111">W co najmniej jednym miejscu `Function` procedury, przypisz wartość nazwy procedury.</span><span class="sxs-lookup"><span data-stu-id="cbe83-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="cbe83-112">Podczas wykonywania `Exit Function` lub `End Function` instrukcji, Visual Basic zwraca wartość ostatnio przypisana do nazwy procedury.</span><span class="sxs-lookup"><span data-stu-id="cbe83-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="cbe83-113">Masz więcej niż jedną `Exit Function` można łączyć instrukcji w tej samej procedury, a `Return` i `Exit Function` instrukcje w tej samej procedury.</span><span class="sxs-lookup"><span data-stu-id="cbe83-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="cbe83-114">Może mieć tylko jeden `End Function` instrukcji w `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="cbe83-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="cbe83-115">Aby uzyskać więcej informacji i obejrzeć przykład, zobacz "Zwraca wartość" w [Function — instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cbe83-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe83-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbe83-116">See also</span></span>
- [<span data-ttu-id="cbe83-117">Procedury</span><span class="sxs-lookup"><span data-stu-id="cbe83-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="cbe83-118">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="cbe83-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="cbe83-119">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="cbe83-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="cbe83-120">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="cbe83-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="cbe83-121">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="cbe83-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="cbe83-122">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbe83-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="cbe83-123">Return, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cbe83-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="cbe83-124">Instrukcje: Utwórz procedurę, która zwraca wartość</span><span class="sxs-lookup"><span data-stu-id="cbe83-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="cbe83-125">Instrukcje: Wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="cbe83-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
