---
title: 'Instrukcje: Definiowanie operatora konwersji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: fe5c314fe4e39c8a06803037da29b51148188e14
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974643"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="3ba13-102">Instrukcje: Definiowanie operatora konwersji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ba13-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="3ba13-103">Jeśli zdefiniowano klasy lub struktury, można zdefiniować typ operatora konwersji między typem klasy lub struktury i inny typ danych (takich jak `Integer`, `Double`, lub `String`).</span><span class="sxs-lookup"><span data-stu-id="3ba13-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="3ba13-104">Zdefiniuj konwersji typu jako [funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md) procedury w obrębie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="3ba13-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="3ba13-105">Wszystkie procedury konwersji muszą być `Public Shared`, a każdy z nich należy określić [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) lub [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="3ba13-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="3ba13-106">Definiowanie operatora dla klasy lub struktury jest również nazywany *przeciążenie* operatora.</span><span class="sxs-lookup"><span data-stu-id="3ba13-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ba13-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ba13-107">Example</span></span>  
 <span data-ttu-id="3ba13-108">W poniższym przykładzie zdefiniowano operatory konwersji między strukturę o nazwie `digit` i `Byte`.</span><span class="sxs-lookup"><span data-stu-id="3ba13-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="3ba13-109">Możesz przetestować struktury `digit` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="3ba13-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="3ba13-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ba13-110">See also</span></span>
- [<span data-ttu-id="3ba13-111">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="3ba13-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="3ba13-112">Instrukcje: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="3ba13-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="3ba13-113">Instrukcje: Wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="3ba13-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="3ba13-114">Instrukcje: Używanie klasy definiującej operatory</span><span class="sxs-lookup"><span data-stu-id="3ba13-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="3ba13-115">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3ba13-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="3ba13-116">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3ba13-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="3ba13-117">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="3ba13-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="3ba13-118">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="3ba13-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="3ba13-119">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="3ba13-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
