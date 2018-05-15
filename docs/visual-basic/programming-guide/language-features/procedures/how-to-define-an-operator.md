---
title: 'Porady: definiowanie operatora (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: c759ebf38ab0727aeada218d288b5ac01e3ecd03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="06f6b-102">Porady: definiowanie operatora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06f6b-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="06f6b-103">Jeśli zdefiniowano klasę lub strukturę można zdefiniować zachowanie standardowe — operator (takich jak `*`, `<>`, lub `And`) po co najmniej jeden z argumentów operacji typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="06f6b-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="06f6b-104">Zdefiniować operator standardowe procedury operatora w obrębie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="06f6b-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="06f6b-105">Wszystkie procedury operatora musi być `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="06f6b-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="06f6b-106">Definiowanie operatora w klasie lub strukturze jest również nazywany *przeładowanie* operatora.</span><span class="sxs-lookup"><span data-stu-id="06f6b-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06f6b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="06f6b-107">Example</span></span>  
 <span data-ttu-id="06f6b-108">W poniższym przykładzie zdefiniowano `+` wywołać operatora dla struktury `height`.</span><span class="sxs-lookup"><span data-stu-id="06f6b-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="06f6b-109">Struktura używa mierzony w stopy i cale wysokości.</span><span class="sxs-lookup"><span data-stu-id="06f6b-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="06f6b-110">Jeden *CAL* jest 2,54 cm, a drugi *stopka* jest 12 cala.</span><span class="sxs-lookup"><span data-stu-id="06f6b-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="06f6b-111">W celu zapewnienia znormalizowane wartości (cali < 12.0), wykonuje konstruktora *modulo* 12 arytmetyczne.</span><span class="sxs-lookup"><span data-stu-id="06f6b-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="06f6b-112">`+` Operator używa konstruktora do generowania wartości znormalizowana.</span><span class="sxs-lookup"><span data-stu-id="06f6b-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 <span data-ttu-id="06f6b-113">Można przetestować struktury `height` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="06f6b-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 <span data-ttu-id="06f6b-114">Aby uzyskać dodatkowe informacje i przykłady, zobacz [przeciążanie operatora w Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span><span class="sxs-lookup"><span data-stu-id="06f6b-114">For more information and examples, see [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f6b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06f6b-115">See Also</span></span>  
 [<span data-ttu-id="06f6b-116">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="06f6b-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="06f6b-117">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="06f6b-117">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="06f6b-118">Instrukcje: wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="06f6b-118">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="06f6b-119">Instrukcje: używanie klasy definiującej operatory</span><span class="sxs-lookup"><span data-stu-id="06f6b-119">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="06f6b-120">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="06f6b-120">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="06f6b-121">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="06f6b-121">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="06f6b-122">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="06f6b-122">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="06f6b-123">Mod, operator</span><span class="sxs-lookup"><span data-stu-id="06f6b-123">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
