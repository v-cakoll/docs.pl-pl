---
title: 'Porady: definiowanie wielu wersji procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 83e96e271f6613aa325d59a0ca2fce9fc69fe059
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350487"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="89b51-102">Porady: definiowanie wielu wersji procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89b51-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="89b51-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span><span class="sxs-lookup"><span data-stu-id="89b51-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="89b51-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span><span class="sxs-lookup"><span data-stu-id="89b51-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="89b51-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="89b51-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="89b51-106">To define multiple versions of a procedure</span><span class="sxs-lookup"><span data-stu-id="89b51-106">To define multiple versions of a procedure</span></span>  
  
1. <span data-ttu-id="89b51-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span><span class="sxs-lookup"><span data-stu-id="89b51-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="89b51-108">Use the same procedure name in every declaration.</span><span class="sxs-lookup"><span data-stu-id="89b51-108">Use the same procedure name in every declaration.</span></span>  
  
2. <span data-ttu-id="89b51-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span><span class="sxs-lookup"><span data-stu-id="89b51-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="89b51-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span><span class="sxs-lookup"><span data-stu-id="89b51-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3. <span data-ttu-id="89b51-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span><span class="sxs-lookup"><span data-stu-id="89b51-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="89b51-112">You do not have to test for which parameters the calling code has supplied.</span><span class="sxs-lookup"><span data-stu-id="89b51-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="89b51-113">Visual Basic passes control to the matching version of your procedure.</span><span class="sxs-lookup"><span data-stu-id="89b51-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4. <span data-ttu-id="89b51-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span><span class="sxs-lookup"><span data-stu-id="89b51-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89b51-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="89b51-115">Example</span></span>  
 <span data-ttu-id="89b51-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span><span class="sxs-lookup"><span data-stu-id="89b51-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="89b51-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span><span class="sxs-lookup"><span data-stu-id="89b51-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="89b51-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span><span class="sxs-lookup"><span data-stu-id="89b51-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="89b51-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="89b51-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89b51-120">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="89b51-120">Compiling the Code</span></span>  
 <span data-ttu-id="89b51-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span><span class="sxs-lookup"><span data-stu-id="89b51-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b51-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89b51-122">See also</span></span>

- [<span data-ttu-id="89b51-123">Procedury</span><span class="sxs-lookup"><span data-stu-id="89b51-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="89b51-124">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="89b51-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="89b51-125">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="89b51-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="89b51-126">Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="89b51-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="89b51-127">Instrukcje: przeciążanie procedury korzystającej z nieokreślonej liczby parametrów</span><span class="sxs-lookup"><span data-stu-id="89b51-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="89b51-128">Zagadnienia dotyczące przeciążania procedur</span><span class="sxs-lookup"><span data-stu-id="89b51-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="89b51-129">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="89b51-129">Overload Resolution</span></span>](./overload-resolution.md)
