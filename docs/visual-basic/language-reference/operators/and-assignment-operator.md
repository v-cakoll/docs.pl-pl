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
ms.openlocfilehash: fa009168be3781c727cd5a9cb6976b8c16fb2843
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967493"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="a1b83-102">&amp;= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1b83-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="a1b83-103">Łączy `String` wyrażenie `String` zmiennej lub właściwości i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="a1b83-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1b83-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1b83-104">Syntax</span></span>  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="a1b83-105">Części</span><span class="sxs-lookup"><span data-stu-id="a1b83-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="a1b83-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="a1b83-106">Required.</span></span> <span data-ttu-id="a1b83-107">Wszelkie `String` zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="a1b83-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="a1b83-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="a1b83-108">Required.</span></span> <span data-ttu-id="a1b83-109">Wszelkie `String` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a1b83-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1b83-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1b83-110">Remarks</span></span>  
 <span data-ttu-id="a1b83-111">Element w lewej części `&=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a1b83-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="a1b83-112">Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="a1b83-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="a1b83-113">`&=` Łączy operator `String` wyrażenie po jego prawej stronie, aby `String` zmiennej lub właściwości po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwość po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="a1b83-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a1b83-114">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="a1b83-114">Overloading</span></span>  
 <span data-ttu-id="a1b83-115">[& — Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="a1b83-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a1b83-116">Przeciążanie `&` operator ma wpływ na zachowanie `&=` operatora.</span><span class="sxs-lookup"><span data-stu-id="a1b83-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="a1b83-117">Jeśli kod używa `&=` dla klasy lub struktury, która przeciążenia `&`, należy zrozumieć zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="a1b83-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a1b83-118">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a1b83-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1b83-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1b83-119">Example</span></span>  
 <span data-ttu-id="a1b83-120">W poniższym przykładzie użyto `&=` operatora do łączenia dwóch `String` zmienne i przypisz wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a1b83-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a1b83-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1b83-121">See also</span></span>
- [<span data-ttu-id="a1b83-122">&, operator</span><span class="sxs-lookup"><span data-stu-id="a1b83-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="a1b83-123">+=, operator</span><span class="sxs-lookup"><span data-stu-id="a1b83-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="a1b83-124">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="a1b83-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="a1b83-125">Operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="a1b83-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="a1b83-126">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1b83-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="a1b83-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="a1b83-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="a1b83-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="a1b83-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
