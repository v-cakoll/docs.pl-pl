---
title: '&amp;= — Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: dee30096f244adc34b83fdfdc6af0baabd372b4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672412"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="07a90-102">&amp;= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07a90-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="07a90-103">Łączy `String` wyrażenie `String` zmiennej lub właściwości i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="07a90-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07a90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07a90-104">Syntax</span></span>  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="07a90-105">Części</span><span class="sxs-lookup"><span data-stu-id="07a90-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="07a90-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="07a90-106">Required.</span></span> <span data-ttu-id="07a90-107">Wszelkie `String` zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="07a90-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="07a90-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="07a90-108">Required.</span></span> <span data-ttu-id="07a90-109">Wszelkie `String` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="07a90-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07a90-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07a90-110">Remarks</span></span>  
 <span data-ttu-id="07a90-111">Element w lewej części `&=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="07a90-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="07a90-112">Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="07a90-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="07a90-113">`&=` Łączy operator `String` wyrażenie po jego prawej stronie, aby `String` zmiennej lub właściwości po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwość po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="07a90-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="07a90-114">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="07a90-114">Overloading</span></span>  
 <span data-ttu-id="07a90-115">[& — Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="07a90-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="07a90-116">Przeciążanie `&` operator ma wpływ na zachowanie `&=` operatora.</span><span class="sxs-lookup"><span data-stu-id="07a90-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="07a90-117">Jeśli kod używa `&=` dla klasy lub struktury, która przeciążenia `&`, należy zrozumieć zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="07a90-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="07a90-118">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="07a90-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="07a90-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="07a90-119">Example</span></span>  
 <span data-ttu-id="07a90-120">W poniższym przykładzie użyto `&=` operatora do łączenia dwóch `String` zmienne i przypisz wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="07a90-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="07a90-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07a90-121">See also</span></span>
- [<span data-ttu-id="07a90-122">&, operator</span><span class="sxs-lookup"><span data-stu-id="07a90-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="07a90-123">+=, operator</span><span class="sxs-lookup"><span data-stu-id="07a90-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="07a90-124">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="07a90-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="07a90-125">Operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="07a90-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="07a90-126">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07a90-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="07a90-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="07a90-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="07a90-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="07a90-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
