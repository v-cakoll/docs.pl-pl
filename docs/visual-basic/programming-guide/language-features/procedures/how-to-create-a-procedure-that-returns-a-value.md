---
title: 'Porady: tworzenie procedury, która zwraca wartość'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 218dbb52abc0100724d38d10be91ef24252d5226
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349723"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="1763f-102">Porady: tworzenie procedury, która zwraca wartość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1763f-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="1763f-103">Użyj procedury `Function`, aby zwrócić wartość do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="1763f-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="1763f-104">Aby utworzyć procedurę zwracającą wartość</span><span class="sxs-lookup"><span data-stu-id="1763f-104">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="1763f-105">Poza każdą inną procedurę Użyj instrukcji `Function`, a po niej instrukcji `End Function`.</span><span class="sxs-lookup"><span data-stu-id="1763f-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="1763f-106">W instrukcji `Function` postępuj według słowa kluczowego `Function` z nazwą procedury, a następnie listę parametrów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="1763f-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="1763f-107">Użyj nawiasów z klauzulą `As`, aby określić typ danych zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="1763f-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="1763f-108">Umieść instrukcje kodu procedury między instrukcjami `Function` i `End Function`.</span><span class="sxs-lookup"><span data-stu-id="1763f-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="1763f-109">Użyj instrukcji `Return`, aby zwrócić wartość do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="1763f-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="1763f-110">Poniższa procedura `Function` oblicza najdłuższy bok lub przeciwprostokątnej w prawym trójkątze, uwzględniając wartości pozostałych dwóch stron.</span><span class="sxs-lookup"><span data-stu-id="1763f-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="1763f-111">Poniższy przykład przedstawia typowe wywołanie do `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="1763f-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="1763f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1763f-112">See also</span></span>

- [<span data-ttu-id="1763f-113">Procedury</span><span class="sxs-lookup"><span data-stu-id="1763f-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="1763f-114">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="1763f-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="1763f-115">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="1763f-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="1763f-116">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="1763f-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="1763f-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="1763f-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1763f-118">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1763f-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="1763f-119">Instrukcje: zwracanie wartości z procedury</span><span class="sxs-lookup"><span data-stu-id="1763f-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="1763f-120">Instrukcje: wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="1763f-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
