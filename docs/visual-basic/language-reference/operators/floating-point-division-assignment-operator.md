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
ms.openlocfilehash: b4855e8270a329f9345339060a323b5ca9cd9792
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592176"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="6ba9c-102">/= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ba9c-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="6ba9c-103">Dzieli wartość zmiennej lub właściwości przez wartość wyrażenia i przypisuje wynik zmiennoprzecinkowy do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ba9c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ba9c-104">Syntax</span></span>  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="6ba9c-105">Części</span><span class="sxs-lookup"><span data-stu-id="6ba9c-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="6ba9c-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-106">Required.</span></span> <span data-ttu-id="6ba9c-107">Dowolna zmienna lub właściwość numeryczna.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="6ba9c-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-108">Required.</span></span> <span data-ttu-id="6ba9c-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ba9c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ba9c-110">Remarks</span></span>  
 <span data-ttu-id="6ba9c-111">Element po lewej stronie operatora `/=` może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="6ba9c-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="6ba9c-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="6ba9c-113">Operator `/=` w pierwszej kolejności dzieli wartość zmiennej lub właściwości (po lewej stronie operatora) przez wartość wyrażenia (po prawej stronie operatora).</span><span class="sxs-lookup"><span data-stu-id="6ba9c-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="6ba9c-114">Następnie operator przypisuje wynik zmiennoprzecinkowy tej operacji do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="6ba9c-115">Ta instrukcja przypisuje wartość `Double` do zmiennej lub właściwości po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="6ba9c-116">Jeśli `Option Strict` jest `On`, `variableorproperty` musi być `Double`.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="6ba9c-117">Jeśli `Option Strict` jest `Off`, Visual Basic wykonuje niejawną konwersję i przypisze wartość wyniku do `variableorproperty`, z możliwym błędem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="6ba9c-118">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) oraz [ścisłe instrukcje Option](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6ba9c-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="6ba9c-119">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="6ba9c-119">Overloading</span></span>  
 <span data-ttu-id="6ba9c-120">[Operator/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="6ba9c-121">Przeciążanie operatora `/` wpływa na zachowanie operatora `/=`.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="6ba9c-122">Jeśli kod używa `/=` na klasie lub strukturze, która przeciąża `/`, należy zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="6ba9c-123">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="6ba9c-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ba9c-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ba9c-124">Example</span></span>  
 <span data-ttu-id="6ba9c-125">Poniższy przykład używa operatora `/=` w celu podzielenia jednej zmiennej `Integer` przez sekundę i przypisanie ilorazu do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6ba9c-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="6ba9c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ba9c-126">See also</span></span>

- [<span data-ttu-id="6ba9c-127">/— Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ba9c-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="6ba9c-128">\\ = — operator</span><span class="sxs-lookup"><span data-stu-id="6ba9c-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="6ba9c-129">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="6ba9c-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="6ba9c-130">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="6ba9c-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="6ba9c-131">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6ba9c-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="6ba9c-132">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="6ba9c-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="6ba9c-133">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="6ba9c-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
