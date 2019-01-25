---
title: 'Instrukcje: Definiowanie operatora (Visual Basic)'
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
ms.openlocfilehash: fb150298562c1ec91f73f3c8075f4f8a4fc20b27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679529"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="d8641-102">Instrukcje: Definiowanie operatora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8641-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="d8641-103">Jeśli zdefiniowano klasy lub struktury, można zdefiniować zachowanie standardowego operatora (takie jak `*`, `<>`, lub `And`) gdy co najmniej jeden z operandów jest typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="d8641-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="d8641-104">Zdefiniuj operator standardowego jako procedury operatora w obrębie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="d8641-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="d8641-105">Wszystkie procedury operatora musi być `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="d8641-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="d8641-106">Definiowanie operatora dla klasy lub struktury jest również nazywany *przeciążenie* operatora.</span><span class="sxs-lookup"><span data-stu-id="d8641-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8641-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8641-107">Example</span></span>  
 <span data-ttu-id="d8641-108">W poniższym przykładzie zdefiniowano `+` operator dla struktury o nazwie `height`.</span><span class="sxs-lookup"><span data-stu-id="d8641-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="d8641-109">Struktura używa mierzoną w stopach i cali wysokości.</span><span class="sxs-lookup"><span data-stu-id="d8641-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="d8641-110">Jeden *CAL* jest 2,54 cm, a drugi *i stopka* jest cala 12.</span><span class="sxs-lookup"><span data-stu-id="d8641-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="d8641-111">Aby zapewnić znormalizowane wartości (w calach < 12.0), Konstruktor wykonuje *modulo* 12 arytmetyczne.</span><span class="sxs-lookup"><span data-stu-id="d8641-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="d8641-112">`+` Operator używa konstruktora do generowania wartości znormalizowana.</span><span class="sxs-lookup"><span data-stu-id="d8641-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 <span data-ttu-id="d8641-113">Możesz przetestować struktury `height` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="d8641-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 <span data-ttu-id="d8641-114">Aby uzyskać więcej informacji i przykładów, zobacz [przeciążania operatora w języku Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span><span class="sxs-lookup"><span data-stu-id="d8641-114">For more information and examples, see [Operator Overloading in Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8641-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8641-115">See also</span></span>
- [<span data-ttu-id="d8641-116">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="d8641-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="d8641-117">Instrukcje: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="d8641-117">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="d8641-118">Instrukcje: Wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="d8641-118">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="d8641-119">Instrukcje: Używanie klasy definiującej operatory</span><span class="sxs-lookup"><span data-stu-id="d8641-119">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="d8641-120">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d8641-120">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="d8641-121">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d8641-121">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="d8641-122">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="d8641-122">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="d8641-123">Mod, operator</span><span class="sxs-lookup"><span data-stu-id="d8641-123">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
