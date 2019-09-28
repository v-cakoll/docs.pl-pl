---
title: ^= — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: 382e0b27c2dbf27e5acccf29f1b8d2b002cb6664
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592233"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="76267-102">^= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76267-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="76267-103">Podnosi wartość zmiennej lub właściwości do potęgi wyrażenia i przypisuje wynik z powrotem do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="76267-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76267-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76267-104">Syntax</span></span>  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="76267-105">Części</span><span class="sxs-lookup"><span data-stu-id="76267-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="76267-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="76267-106">Required.</span></span> <span data-ttu-id="76267-107">Dowolna zmienna lub właściwość numeryczna.</span><span class="sxs-lookup"><span data-stu-id="76267-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="76267-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="76267-108">Required.</span></span> <span data-ttu-id="76267-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="76267-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76267-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76267-110">Remarks</span></span>  
 <span data-ttu-id="76267-111">Element po lewej stronie operatora `^=` może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="76267-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="76267-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="76267-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="76267-113">Operator `^=` po raz pierwszy podnosi wartość zmiennej lub właściwości (po lewej stronie operatora) do potęgi wartości wyrażenia (po prawej stronie operatora)...</span><span class="sxs-lookup"><span data-stu-id="76267-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="76267-114">Następnie operator przypisuje wynik tej operacji z powrotem do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="76267-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="76267-115">Visual Basic zawsze wykonuje potęgowanie w [podwójnym typie danych](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="76267-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="76267-116">Operandy dowolnego typu są konwertowane na `Double`, a wynikiem jest zawsze `Double`.</span><span class="sxs-lookup"><span data-stu-id="76267-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="76267-117">Wartość `expression` może być ułamkowa, ujemna lub jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="76267-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="76267-118">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="76267-118">Overloading</span></span>  
 <span data-ttu-id="76267-119">[Operator ^](../../../visual-basic/language-reference/operators/exponentiation-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="76267-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="76267-120">Przeciążanie operatora `^` wpływa na zachowanie operatora `^=`.</span><span class="sxs-lookup"><span data-stu-id="76267-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="76267-121">Jeśli kod używa `^=` na klasie lub strukturze, która przeciąża `^`, należy zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="76267-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="76267-122">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="76267-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76267-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="76267-123">Example</span></span>  
 <span data-ttu-id="76267-124">Poniższy przykład używa operatora `^=`, aby podnieść wartość jednej zmiennej `Integer` do potęgi drugiej zmiennej i przypisać wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="76267-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="76267-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76267-125">See also</span></span>

- [<span data-ttu-id="76267-126">^, operator</span><span class="sxs-lookup"><span data-stu-id="76267-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [<span data-ttu-id="76267-127">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="76267-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="76267-128">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="76267-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="76267-129">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="76267-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="76267-130">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="76267-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="76267-131">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="76267-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
