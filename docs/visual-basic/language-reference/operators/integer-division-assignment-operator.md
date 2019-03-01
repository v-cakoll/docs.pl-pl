---
title: '\= — Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: 2b24cfe3357bfe5be213464facd9f9db0a5e27e0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977993"
---
# <a name="-operator"></a><span data-ttu-id="1bec6-102">\\= — Operator</span><span class="sxs-lookup"><span data-stu-id="1bec6-102">\\= Operator</span></span>
<span data-ttu-id="1bec6-103">Dzieli wartość zmiennej lub właściwości przez wartość wyrażenia i przypisuje wyniku liczby całkowitej do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="1bec6-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bec6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1bec6-104">Syntax</span></span>  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="1bec6-105">Części</span><span class="sxs-lookup"><span data-stu-id="1bec6-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="1bec6-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1bec6-106">Required.</span></span> <span data-ttu-id="1bec6-107">Zmienna numeryczna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="1bec6-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="1bec6-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1bec6-108">Required.</span></span> <span data-ttu-id="1bec6-109">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="1bec6-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bec6-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1bec6-110">Remarks</span></span>  
 <span data-ttu-id="1bec6-111">Element w lewej części `\=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="1bec6-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="1bec6-112">Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="1bec6-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="1bec6-113">`\=` Operator dzieli wartość zmiennej lub właściwość po lewej stronie według wartości w jego prawej stronie, a następnie przypisuje wyniku liczby całkowitej, zmienna lub właściwość po lewej stronie</span><span class="sxs-lookup"><span data-stu-id="1bec6-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="1bec6-114">Aby uzyskać więcej informacji na temat dzielenie liczby całkowitej, zobacz [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="1bec6-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="1bec6-115">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="1bec6-115">Overloading</span></span>  
 <span data-ttu-id="1bec6-116">`\` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="1bec6-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1bec6-117">Przeciążanie `\` operator ma wpływ na zachowanie `\=` operatora.</span><span class="sxs-lookup"><span data-stu-id="1bec6-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="1bec6-118">Jeśli kod używa `\=` dla klasy lub struktury, która przeciążenia `\`, należy zrozumieć zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="1bec6-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1bec6-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1bec6-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bec6-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="1bec6-120">Example</span></span>  
 <span data-ttu-id="1bec6-121">W poniższym przykładzie użyto `\=` operator podziału jeden `Integer` zmiennej, sekundy i Przypisz liczbę całkowitą wyniku do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1bec6-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="1bec6-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1bec6-122">See also</span></span>
- [<span data-ttu-id="1bec6-123">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bec6-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="1bec6-124">/ = — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bec6-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="1bec6-125">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="1bec6-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="1bec6-126">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="1bec6-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="1bec6-127">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1bec6-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="1bec6-128">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="1bec6-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="1bec6-129">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="1bec6-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
