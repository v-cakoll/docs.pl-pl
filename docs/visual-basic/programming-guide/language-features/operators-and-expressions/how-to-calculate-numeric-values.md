---
title: 'Porady: obliczanie wartości liczbowych'
ms.date: 07/20/2015
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
ms.openlocfilehash: d213f6b5a4abf8c52d8872ae36e89796183ff27c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348970"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="3a727-102">Porady: obliczanie wartości liczbowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a727-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="3a727-103">Wartości liczbowe można obliczyć przy użyciu wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="3a727-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="3a727-104">*Wyrażenie liczbowe* jest wyrażeniem zawierającym literały, stałe i zmienne reprezentujące wartości liczbowe oraz operatory, które działają na tych wartościach.</span><span class="sxs-lookup"><span data-stu-id="3a727-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="3a727-105">Obliczanie wartości liczbowych</span><span class="sxs-lookup"><span data-stu-id="3a727-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="3a727-106">Aby obliczyć wartość liczbową</span><span class="sxs-lookup"><span data-stu-id="3a727-106">To calculate a numeric value</span></span>  
  
- <span data-ttu-id="3a727-107">Połącz jeden lub więcej literałów liczbowych, stałych i zmiennych w wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="3a727-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="3a727-108">Poniższy przykład pokazuje nieprawidłowe wyrażenia liczbowe.</span><span class="sxs-lookup"><span data-stu-id="3a727-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="3a727-109">Pierwsze trzy wiersze przedstawiają literał, stałą i zmienną.</span><span class="sxs-lookup"><span data-stu-id="3a727-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="3a727-110">Każdy z nich tworzy prawidłowe wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="3a727-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="3a727-111">Ostatni wiersz zawiera kombinację zmiennej z dwoma literałami.</span><span class="sxs-lookup"><span data-stu-id="3a727-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="3a727-112">Należy zauważyć, że wyrażenie liczbowe nie tworzy kompletnej instrukcji Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3a727-112">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span></span> <span data-ttu-id="3a727-113">Należy użyć wyrażenia jako części kompletnej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3a727-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="3a727-114">Aby zapisać wartość liczbową</span><span class="sxs-lookup"><span data-stu-id="3a727-114">To store a numeric value</span></span>  
  
- <span data-ttu-id="3a727-115">Można użyć instrukcji przypisania, aby przypisać wartość reprezentowaną przez wyrażenie liczbowe do zmiennej, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3a727-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     <span data-ttu-id="3a727-116">W powyższym przykładzie wartość wyrażenia po prawej stronie operatora równości (`=`) jest przypisana do zmiennej `j` po lewej stronie operatora, dlatego `j` oblicza do 276.</span><span class="sxs-lookup"><span data-stu-id="3a727-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="3a727-117">Aby uzyskać więcej informacji, zobacz [instrukcje](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="3a727-117">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="3a727-118">Wiele operatorów</span><span class="sxs-lookup"><span data-stu-id="3a727-118">Multiple Operators</span></span>  
 <span data-ttu-id="3a727-119">Jeśli wyrażenie liczbowe zawiera więcej niż jeden operator, kolejność, w której są oceniane, zależy od reguł pierwszeństwa operatora.</span><span class="sxs-lookup"><span data-stu-id="3a727-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="3a727-120">Aby zastąpić reguły pierwszeństwa operatorów, należy umieścić wyrażenia w nawiasach, jak w powyższym przykładzie. ujęte wyrażenia są oceniane jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="3a727-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="3a727-121">Aby zastąpić normalne pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="3a727-121">To override normal operator precedence</span></span>  
  
- <span data-ttu-id="3a727-122">Użyj nawiasów, aby ująć operacje, które mają zostać wykonane jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="3a727-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="3a727-123">Poniższy przykład przedstawia dwa różne wyniki z tymi samymi operandami i operatorami.</span><span class="sxs-lookup"><span data-stu-id="3a727-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     <span data-ttu-id="3a727-124">W poprzednim przykładzie, obliczenie dla `j` wykonuje najpierw operator dodawania (`+`), ponieważ nawiasy wokół `(67 + i)` przesłaniają normalne pierwszeństwo, a wartość przypisana do `j` to 276 (4 razy 69).</span><span class="sxs-lookup"><span data-stu-id="3a727-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="3a727-125">Obliczenie dla `k` wykonuje operatory w ich normalnym pierwszeństwie (`*` przed `+`), a wartość przypisana do `k` to 270 (268 plus 2).</span><span class="sxs-lookup"><span data-stu-id="3a727-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="3a727-126">Aby uzyskać więcej informacji, zobacz [pierwszeństwo operatorów w Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="3a727-126">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a727-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a727-127">See also</span></span>

- [<span data-ttu-id="3a727-128">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="3a727-128">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="3a727-129">Porównania wartości</span><span class="sxs-lookup"><span data-stu-id="3a727-129">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="3a727-130">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="3a727-130">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="3a727-131">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a727-131">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="3a727-132">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="3a727-132">Arithmetic Operators</span></span>](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="3a727-133">Skuteczna kombinacja operatorów</span><span class="sxs-lookup"><span data-stu-id="3a727-133">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
