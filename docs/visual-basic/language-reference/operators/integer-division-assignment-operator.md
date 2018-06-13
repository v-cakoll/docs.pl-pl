---
title: '\= Operator'
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
ms.openlocfilehash: 4ebbf2eca7fb3cd208d979d7f3c77aa106569119
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603564"
---
# <a name="-operator"></a><span data-ttu-id="d7f08-102">\\= — Operator</span><span class="sxs-lookup"><span data-stu-id="d7f08-102">\\= Operator</span></span>
<span data-ttu-id="d7f08-103">Dzieli wartość zmiennej lub właściwość przez wartość wyrażenia i przypisuje całkowitą wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="d7f08-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7f08-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7f08-104">Syntax</span></span>  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d7f08-105">Części</span><span class="sxs-lookup"><span data-stu-id="d7f08-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="d7f08-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d7f08-106">Required.</span></span> <span data-ttu-id="d7f08-107">Zmienna numeryczna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="d7f08-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="d7f08-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d7f08-108">Required.</span></span> <span data-ttu-id="d7f08-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="d7f08-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7f08-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7f08-110">Remarks</span></span>  
 <span data-ttu-id="d7f08-111">Element po lewej stronie `\=` operator może być zmienną skalarną proste, właściwością lub element tablicy.</span><span class="sxs-lookup"><span data-stu-id="d7f08-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="d7f08-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="d7f08-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="d7f08-113">`\=` Operator dzieli wartość zmiennej lub właściwość po lewej stronie przez wartość jego prawej stronie i przypisuje wynik całkowitą zmienna lub właściwość po lewej stronie</span><span class="sxs-lookup"><span data-stu-id="d7f08-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="d7f08-114">Aby uzyskać więcej informacji na dzielenie liczby całkowitej, zobacz [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d7f08-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d7f08-115">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="d7f08-115">Overloading</span></span>  
 <span data-ttu-id="d7f08-116">`\` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="d7f08-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d7f08-117">Przeciążanie `\` operator wpływa na działanie `\=` operatora.</span><span class="sxs-lookup"><span data-stu-id="d7f08-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="d7f08-118">Jeśli używa Twój kod `\=` na klasę lub strukturę, która overloads `\`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="d7f08-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d7f08-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d7f08-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7f08-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7f08-120">Example</span></span>  
 <span data-ttu-id="d7f08-121">W poniższym przykładzie użyto `\=` operatora, aby podzielić jedną `Integer` zmiennej sekundę i Przypisz liczbę całkowitą wyniku do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d7f08-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](codesnippet/VisualBasic/integer-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d7f08-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7f08-122">See Also</span></span>  
 [<span data-ttu-id="d7f08-123">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7f08-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [<span data-ttu-id="d7f08-124">/ = — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7f08-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="d7f08-125">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="d7f08-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="d7f08-126">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="d7f08-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="d7f08-127">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7f08-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="d7f08-128">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="d7f08-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="d7f08-129">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="d7f08-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
