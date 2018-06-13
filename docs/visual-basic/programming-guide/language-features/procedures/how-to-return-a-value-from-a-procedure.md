---
title: 'Porady: zwracanie wartości z procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 62e8a52e488247d4dfcde2a560920447abe1c182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651837"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="706d8-102">Porady: zwracanie wartości z procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="706d8-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="706d8-103">A `Function` procedury zwraca wartość do wywołującego kodu albo wykonując `Return` instrukcji lub napotkania `Exit Function` lub `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="706d8-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="706d8-104">Aby zwrócić wartość przy użyciu instrukcji Return</span><span class="sxs-lookup"><span data-stu-id="706d8-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="706d8-105">Umieść `Return` instrukcji w momencie, gdy procedury zadanie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="706d8-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="706d8-106">Wykonaj `Return` — słowo kluczowe z dowolne wyrażenie zwracające wartość ma być zwrócona do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="706d8-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="706d8-107">Może mieć więcej niż jeden `Return` instrukcji w tej samej procedury.</span><span class="sxs-lookup"><span data-stu-id="706d8-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="706d8-108">Następujące `Function` procedury oblicza najdłuższego boku lub przeciwprostokątnej trójkąta prostokątnego i zwraca go do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="706d8-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     <span data-ttu-id="706d8-109">W poniższym przykładzie przedstawiono typowe wywołania `hypotenuse`, która przechowuje zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="706d8-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="706d8-110">Aby zwrócić wartość przy użyciu funkcji zakończenia lub End</span><span class="sxs-lookup"><span data-stu-id="706d8-110">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="706d8-111">W co najmniej jednym miejscu `Function` procedury, przypisz wartość na nazwę procedury.</span><span class="sxs-lookup"><span data-stu-id="706d8-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="706d8-112">Podczas wykonywania `Exit Function` lub `End Function` instrukcji języka Visual Basic zwraca wartość ostatnio przypisane do Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="706d8-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="706d8-113">Może mieć więcej niż jeden `Exit Function` można łączyć instrukcji w tej samej procedury, a `Return` i `Exit Function` instrukcje w tej samej procedury.</span><span class="sxs-lookup"><span data-stu-id="706d8-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="706d8-114">Może mieć tylko jeden `End Function` instrukcji w `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="706d8-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="706d8-115">Na przykład i więcej informacji, zobacz "Zwraca wartość" w [instrukcji Function](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="706d8-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="706d8-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="706d8-116">See Also</span></span>  
 [<span data-ttu-id="706d8-117">Procedury</span><span class="sxs-lookup"><span data-stu-id="706d8-117">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="706d8-118">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="706d8-118">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="706d8-119">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="706d8-119">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="706d8-120">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="706d8-120">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="706d8-121">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="706d8-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="706d8-122">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="706d8-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="706d8-123">Return, instrukcja</span><span class="sxs-lookup"><span data-stu-id="706d8-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [<span data-ttu-id="706d8-124">Instrukcje: tworzenie procedury, która zwraca wartość</span><span class="sxs-lookup"><span data-stu-id="706d8-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="706d8-125">Instrukcje: wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="706d8-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
