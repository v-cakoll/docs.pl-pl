---
title: 'Porady: przekazywanie procedur do innej procedury w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e8e205f5238aab39aa92574bc5c680e68cc8a81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="d2dbf-102">Porady: przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2dbf-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="d2dbf-103">Ten przykład przedstawia sposób użycia delegatów do przekazania procedurę do innej procedury.</span><span class="sxs-lookup"><span data-stu-id="d2dbf-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="d2dbf-104">Delegat jest typem, który można użyć innych typów w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d2dbf-104">A delegate is a type that you can use like any other type in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="d2dbf-105">`AddressOf` Operator zwraca obiektu delegowanego, po zastosowaniu na nazwę procedury.</span><span class="sxs-lookup"><span data-stu-id="d2dbf-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="d2dbf-106">W tym przykładzie ma procedury z parametru delegata, który może zająć odwołanie do innej procedury uzyskany z `AddressOf` operatora.</span><span class="sxs-lookup"><span data-stu-id="d2dbf-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="d2dbf-107">Utwórz delegata i procedur dopasowania</span><span class="sxs-lookup"><span data-stu-id="d2dbf-107">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="d2dbf-108">Utworzenia delegata o nazwie `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="d2dbf-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  <span data-ttu-id="d2dbf-109">Tworzenie procedury o nazwie `AddNumbers` parametrów i wartości zwracanej, które pasują do właściwości `MathOperator`, dzięki czemu podpisy są zgodne.</span><span class="sxs-lookup"><span data-stu-id="d2dbf-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  <span data-ttu-id="d2dbf-110">Tworzenie procedury o nazwie `SubtractNumbers` za pomocą podpisu, który odpowiada `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="d2dbf-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  <span data-ttu-id="d2dbf-111">Tworzenie procedury o nazwie `DelegateTest` pobierającej delegata jako parametr.</span><span class="sxs-lookup"><span data-stu-id="d2dbf-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="d2dbf-112">Ta procedura może akceptować odwołanie do `AddNumbers` lub `SubtractNumbers`, ponieważ ich podpisy są zgodne `MathOperator` podpisu.</span><span class="sxs-lookup"><span data-stu-id="d2dbf-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  <span data-ttu-id="d2dbf-113">Tworzenie procedury o nazwie `Test` wywołującym `DelegateTest` drugi raz z delegowanie dla `AddNumbers` jako parametru i ponownie z obiektem delegowanym dla `SubtractNumbers` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="d2dbf-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     <span data-ttu-id="d2dbf-114">Gdy `Test` jest wywoływana, najpierw wyświetla wynik `AddNumbers` działające na `5` i `3`, czyli 8.</span><span class="sxs-lookup"><span data-stu-id="d2dbf-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="d2dbf-115">Następnie wynik `SubtractNumbers` na `9` i `3` jest wyświetlany, który jest 6.</span><span class="sxs-lookup"><span data-stu-id="d2dbf-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2dbf-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2dbf-116">See Also</span></span>  
 [<span data-ttu-id="d2dbf-117">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="d2dbf-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="d2dbf-118">AddressOf — Operator</span><span class="sxs-lookup"><span data-stu-id="d2dbf-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="d2dbf-119">Delegate — instrukcja</span><span class="sxs-lookup"><span data-stu-id="d2dbf-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="d2dbf-120">Porady: wywoływanie metody delegata</span><span class="sxs-lookup"><span data-stu-id="d2dbf-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
