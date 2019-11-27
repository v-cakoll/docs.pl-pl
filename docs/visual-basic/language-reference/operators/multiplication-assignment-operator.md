---
title: '*=, operator'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 4b60fa44a92bff683e13f850da025d7fe753618d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349786"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="42fb5-102">\*= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42fb5-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="42fb5-103">Mnoży wartość zmiennej lub właściwości przez wartość wyrażenia i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="42fb5-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42fb5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="42fb5-104">Syntax</span></span>  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="42fb5-105">Części</span><span class="sxs-lookup"><span data-stu-id="42fb5-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="42fb5-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="42fb5-106">Required.</span></span> <span data-ttu-id="42fb5-107">Dowolna zmienna lub właściwość numeryczna.</span><span class="sxs-lookup"><span data-stu-id="42fb5-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="42fb5-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="42fb5-108">Required.</span></span> <span data-ttu-id="42fb5-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="42fb5-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42fb5-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42fb5-110">Remarks</span></span>  
 <span data-ttu-id="42fb5-111">Element po lewej stronie operatora `*=` może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="42fb5-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="42fb5-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="42fb5-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="42fb5-113">Operator `*=` najpierw mnoży wartość wyrażenia (po prawej stronie operatora) przez wartość zmiennej lub właściwości (po lewej stronie operatora), która jest równa.</span><span class="sxs-lookup"><span data-stu-id="42fb5-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="42fb5-114">Następnie operator przypisuje wynik tej operacji do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="42fb5-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="42fb5-115">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="42fb5-115">Overloading</span></span>  
 <span data-ttu-id="42fb5-116">[Operator \*](../../../visual-basic/language-reference/operators/multiplication-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="42fb5-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="42fb5-117">Przeciążanie operatora `*` ma wpływ na zachowanie operatora `*=`.</span><span class="sxs-lookup"><span data-stu-id="42fb5-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="42fb5-118">Jeśli kod używa `*=` na klasie lub strukturze, która przeciąża `*`, należy zapoznać się z jego ponownie zdefiniowanym zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="42fb5-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="42fb5-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="42fb5-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42fb5-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="42fb5-120">Example</span></span>  
 <span data-ttu-id="42fb5-121">Poniższy przykład używa operatora `*=`, aby pomnożyć jedną zmienną `Integer` przez sekundę i przypisać wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="42fb5-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="42fb5-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42fb5-122">See also</span></span>

- [<span data-ttu-id="42fb5-123">\*, operator</span><span class="sxs-lookup"><span data-stu-id="42fb5-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [<span data-ttu-id="42fb5-124">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="42fb5-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="42fb5-125">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="42fb5-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="42fb5-126">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42fb5-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="42fb5-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="42fb5-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="42fb5-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="42fb5-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
