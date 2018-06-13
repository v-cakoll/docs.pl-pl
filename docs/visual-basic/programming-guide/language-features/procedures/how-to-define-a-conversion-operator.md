---
title: 'Porady: definiowanie operatora konwersji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 24bbe41af67f757cae661a78d482a423ff0ffd85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648476"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="f29ed-102">Porady: definiowanie operatora konwersji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f29ed-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="f29ed-103">Jeśli zdefiniowano klasę lub strukturę można zdefiniować typu operatora konwersji między typem klasy lub struktury i inny typ danych (takich jak `Integer`, `Double`, lub `String`).</span><span class="sxs-lookup"><span data-stu-id="f29ed-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="f29ed-104">Zdefiniuj konwersji typu jako [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md) procedury w obrębie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f29ed-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="f29ed-105">Wszystkie procedury konwersji muszą być `Public Shared`, a każda z nich należy określić albo [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) lub [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="f29ed-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="f29ed-106">Definiowanie operatora w klasie lub strukturze jest również nazywany *przeładowanie* operatora.</span><span class="sxs-lookup"><span data-stu-id="f29ed-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f29ed-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f29ed-107">Example</span></span>  
 <span data-ttu-id="f29ed-108">W poniższym przykładzie zdefiniowano operatory konwersji między strukturę o nazwie `digit` i `Byte`.</span><span class="sxs-lookup"><span data-stu-id="f29ed-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 <span data-ttu-id="f29ed-109">Można przetestować struktury `digit` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="f29ed-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f29ed-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f29ed-110">See Also</span></span>  
 [<span data-ttu-id="f29ed-111">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="f29ed-111">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="f29ed-112">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="f29ed-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="f29ed-113">Instrukcje: wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="f29ed-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="f29ed-114">Instrukcje: używanie klasy definiującej operatory</span><span class="sxs-lookup"><span data-stu-id="f29ed-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="f29ed-115">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f29ed-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="f29ed-116">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f29ed-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="f29ed-117">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="f29ed-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="f29ed-118">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="f29ed-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="f29ed-119">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="f29ed-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
