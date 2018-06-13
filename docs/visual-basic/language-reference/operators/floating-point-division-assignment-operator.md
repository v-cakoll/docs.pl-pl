---
title: /= — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 642307bc531e7d9ce21a932b112795b35e7b3182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604097"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="d5beb-102">/= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5beb-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="d5beb-103">Dzieli wartość zmiennej lub właściwość przez wartość wyrażenia i przypisuje wynik zmiennoprzecinkowy do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5beb-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5beb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5beb-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d5beb-105">Części</span><span class="sxs-lookup"><span data-stu-id="d5beb-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="d5beb-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d5beb-106">Required.</span></span> <span data-ttu-id="d5beb-107">Zmienna numeryczna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="d5beb-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="d5beb-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d5beb-108">Required.</span></span> <span data-ttu-id="d5beb-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="d5beb-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5beb-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5beb-110">Remarks</span></span>  
 <span data-ttu-id="d5beb-111">Element po lewej stronie `/=` operator może być zmienną skalarną proste, właściwością lub element tablicy.</span><span class="sxs-lookup"><span data-stu-id="d5beb-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="d5beb-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="d5beb-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="d5beb-113">`/=` Operator najpierw dzieli wartość zmiennej lub właściwości (po lewej stronie operatora) przez wartość wyrażenia (po prawej stronie operatora).</span><span class="sxs-lookup"><span data-stu-id="d5beb-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="d5beb-114">Operator następnie przypisuje zmiennoprzecinkowe wynik tej operacji do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5beb-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="d5beb-115">Ta instrukcja przypisuje `Double` wartość do zmiennej lub właściwość po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="d5beb-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="d5beb-116">Jeśli `Option Strict` jest `On`, `variableorproperty` musi być `Double`.</span><span class="sxs-lookup"><span data-stu-id="d5beb-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="d5beb-117">Jeśli `Option Strict` jest `Off`, Visual Basic wykonuje niejawna konwersja i przypisuje wynikowej wartości do `variableorproperty`, z możliwy błąd w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d5beb-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="d5beb-118">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) i [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d5beb-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d5beb-119">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="d5beb-119">Overloading</span></span>  
 <span data-ttu-id="d5beb-120">[/ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="d5beb-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d5beb-121">Przeciążanie `/` operator wpływa na działanie `/=` operatora.</span><span class="sxs-lookup"><span data-stu-id="d5beb-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="d5beb-122">Jeśli używa Twój kod `/=` na klasę lub strukturę, która overloads `/`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="d5beb-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d5beb-123">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d5beb-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5beb-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5beb-124">Example</span></span>  
 <span data-ttu-id="d5beb-125">W poniższym przykładzie użyto `/=` operatora, aby podzielić jedną `Integer` zmiennej sekundę i przypisz iloraz do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d5beb-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d5beb-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5beb-126">See Also</span></span>  
 [<span data-ttu-id="d5beb-127">/ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5beb-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [<span data-ttu-id="d5beb-128">\\= — Operator</span><span class="sxs-lookup"><span data-stu-id="d5beb-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="d5beb-129">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="d5beb-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="d5beb-130">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="d5beb-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="d5beb-131">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5beb-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="d5beb-132">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="d5beb-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="d5beb-133">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="d5beb-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
