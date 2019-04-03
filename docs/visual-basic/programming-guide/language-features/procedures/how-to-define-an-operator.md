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
ms.openlocfilehash: 3a09657ee7a79b7f590adba0e4fb0c04a8e89043
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843646"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="a5695-102">Instrukcje: Definiowanie operatora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5695-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="a5695-103">Jeśli zdefiniowano klasy lub struktury, można zdefiniować zachowanie standardowego operatora (takie jak `*`, `<>`, lub `And`) gdy co najmniej jeden z operandów jest typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="a5695-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="a5695-104">Zdefiniuj operator standardowego jako procedury operatora w obrębie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="a5695-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="a5695-105">Wszystkie procedury operatora musi być `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="a5695-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="a5695-106">Definiowanie operatora dla klasy lub struktury jest również nazywany *przeciążenie* operatora.</span><span class="sxs-lookup"><span data-stu-id="a5695-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5695-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5695-107">Example</span></span>  
 <span data-ttu-id="a5695-108">W poniższym przykładzie zdefiniowano `+` operator dla struktury o nazwie `height`.</span><span class="sxs-lookup"><span data-stu-id="a5695-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="a5695-109">Struktura używa mierzoną w stopach i cali wysokości.</span><span class="sxs-lookup"><span data-stu-id="a5695-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="a5695-110">Jeden *CAL* jest 2,54 cm, a drugi *i stopka* jest cala 12.</span><span class="sxs-lookup"><span data-stu-id="a5695-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="a5695-111">Aby zapewnić znormalizowane wartości (w calach < 12.0), Konstruktor wykonuje *modulo* 12 arytmetyczne.</span><span class="sxs-lookup"><span data-stu-id="a5695-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="a5695-112">`+` Operator używa konstruktora do generowania wartości znormalizowana.</span><span class="sxs-lookup"><span data-stu-id="a5695-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="a5695-113">Możesz przetestować struktury `height` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="a5695-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  
  
  
## <a name="see-also"></a><span data-ttu-id="a5695-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5695-114">See also</span></span>

- [<span data-ttu-id="a5695-115">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="a5695-115">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a5695-116">Instrukcje: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="a5695-116">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="a5695-117">Instrukcje: Wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="a5695-117">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="a5695-118">Instrukcje: Używanie klasy definiującej operatory</span><span class="sxs-lookup"><span data-stu-id="a5695-118">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="a5695-119">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a5695-119">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="a5695-120">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a5695-120">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="a5695-121">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="a5695-121">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="a5695-122">Mod, operator</span><span class="sxs-lookup"><span data-stu-id="a5695-122">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
