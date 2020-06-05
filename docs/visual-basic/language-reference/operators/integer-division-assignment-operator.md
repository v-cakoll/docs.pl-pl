---
title: '\=, operator'
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
ms.openlocfilehash: a546d8b0c9b3852386970f80d3da96794da2351c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370950"
---
# <a name="-operator"></a><span data-ttu-id="8cca4-102">\\= — Operator</span><span class="sxs-lookup"><span data-stu-id="8cca4-102">\\= Operator</span></span>
<span data-ttu-id="8cca4-103">Dzieli wartość zmiennej lub właściwości przez wartość wyrażenia i przypisuje wynik całkowity do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cca4-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cca4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8cca4-104">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="8cca4-105">Części</span><span class="sxs-lookup"><span data-stu-id="8cca4-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="8cca4-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8cca4-106">Required.</span></span> <span data-ttu-id="8cca4-107">Dowolna zmienna lub właściwość numeryczna.</span><span class="sxs-lookup"><span data-stu-id="8cca4-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="8cca4-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8cca4-108">Required.</span></span> <span data-ttu-id="8cca4-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="8cca4-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cca4-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8cca4-110">Remarks</span></span>  
 <span data-ttu-id="8cca4-111">Element po lewej stronie `\=` operatora może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="8cca4-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="8cca4-112">Zmienna lub właściwość nie może być [tylko do odczytu](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="8cca4-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="8cca4-113">`\=`Operator dzieli wartość zmiennej lub właściwości po lewej stronie przez wartość po prawej stronie, a następnie przypisuje wynik całkowity do zmiennej lub właściwości po jej lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="8cca4-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="8cca4-114">Aby uzyskać więcej informacji na temat dzielenia liczb całkowitych, zobacz element [\ operator (Visual Basic)](integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="8cca4-114">For further information on integer division, see [\ Operator (Visual Basic)](integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8cca4-115">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="8cca4-115">Overloading</span></span>  
 <span data-ttu-id="8cca4-116">`\`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="8cca4-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8cca4-117">Przeciążanie `\` operatora ma wpływ na zachowanie `\=` operatora.</span><span class="sxs-lookup"><span data-stu-id="8cca4-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="8cca4-118">Jeśli kod korzysta z `\=` klasy lub struktury, która przeciążania `\` , należy poznać jej ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8cca4-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8cca4-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8cca4-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cca4-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="8cca4-120">Example</span></span>  
 <span data-ttu-id="8cca4-121">Poniższy przykład używa `\=` operatora do dzielenia jednej `Integer` zmiennej przez sekundę i przypisywania wyniku liczby całkowitej do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8cca4-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="8cca4-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8cca4-122">See also</span></span>

- [<span data-ttu-id="8cca4-123">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cca4-123">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="8cca4-124">Operator/= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cca4-124">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="8cca4-125">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="8cca4-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="8cca4-126">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="8cca4-126">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="8cca4-127">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cca4-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="8cca4-128">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="8cca4-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="8cca4-129">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="8cca4-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
