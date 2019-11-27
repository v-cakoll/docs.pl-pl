---
title: 'Porady: zwracanie wartości z procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 1371e4ed0ff28f9caf56eabf2a1bb9290edbe75c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346026"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="3e659-102">Porady: zwracanie wartości z procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e659-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="3e659-103">Procedura `Function` zwraca wartość do wywołującego kodu przez wykonanie instrukcji `Return` lub napotkanie instrukcji `Exit Function` lub `End Function`.</span><span class="sxs-lookup"><span data-stu-id="3e659-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="3e659-104">Aby zwrócić wartość przy użyciu instrukcji return</span><span class="sxs-lookup"><span data-stu-id="3e659-104">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="3e659-105">Umieść instrukcję `Return` w punkcie, w którym wykonano zadanie procedury.</span><span class="sxs-lookup"><span data-stu-id="3e659-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="3e659-106">Obserwuj `Return` słowo kluczowe z wyrażeniem, które zwraca wartość, która ma zostać zwrócona do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="3e659-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="3e659-107">W tej samej procedurze można mieć więcej niż jedną instrukcję `Return`.</span><span class="sxs-lookup"><span data-stu-id="3e659-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="3e659-108">Poniższa procedura `Function` oblicza najdłuższy Trójkąt lub przeciwprostokątnej, z prawej strony, i zwraca go do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="3e659-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="3e659-109">W poniższym przykładzie przedstawiono typowe wywołanie `hypotenuse`, w którym jest przechowywana zwrócona wartość.</span><span class="sxs-lookup"><span data-stu-id="3e659-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="3e659-110">Aby zwrócić wartość przy użyciu funkcji Exit lub End Function</span><span class="sxs-lookup"><span data-stu-id="3e659-110">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="3e659-111">W co najmniej jednym miejscu procedury `Function` Przypisz wartość do nazwy procedury.</span><span class="sxs-lookup"><span data-stu-id="3e659-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="3e659-112">Podczas wykonywania instrukcji `Exit Function` lub `End Function`, Visual Basic zwraca wartość ostatnio przypisaną do nazwy procedury.</span><span class="sxs-lookup"><span data-stu-id="3e659-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="3e659-113">W tej samej procedurze można mieć więcej niż jedną instrukcję `Exit Function` i można mieszać instrukcje `Return` i `Exit Function` w tej samej procedurze.</span><span class="sxs-lookup"><span data-stu-id="3e659-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="3e659-114">W procedurze `Function` można mieć tylko jedną instrukcję `End Function`.</span><span class="sxs-lookup"><span data-stu-id="3e659-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="3e659-115">Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz "wartość zwracana" w [instrukcji funkcji](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3e659-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e659-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e659-116">See also</span></span>

- [<span data-ttu-id="3e659-117">Procedury</span><span class="sxs-lookup"><span data-stu-id="3e659-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="3e659-118">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="3e659-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="3e659-119">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="3e659-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="3e659-120">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="3e659-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="3e659-121">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="3e659-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="3e659-122">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3e659-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="3e659-123">Return, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3e659-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="3e659-124">Instrukcje: tworzenie procedury, która zwraca wartość</span><span class="sxs-lookup"><span data-stu-id="3e659-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="3e659-125">Instrukcje: wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="3e659-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
