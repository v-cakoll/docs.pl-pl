---
title: ^=, operator
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: fe5e8fc2b64b9e7c33483612071d338a0ee22768
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331295"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b8964-102">^= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8964-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="b8964-103">Podnosi wartość zmiennej lub właściwości do potęgi wyrażenia i przypisuje wynik z powrotem do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="b8964-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8964-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8964-104">Syntax</span></span>  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="b8964-105">Części</span><span class="sxs-lookup"><span data-stu-id="b8964-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="b8964-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b8964-106">Required.</span></span> <span data-ttu-id="b8964-107">Dowolna zmienna lub właściwość numeryczna.</span><span class="sxs-lookup"><span data-stu-id="b8964-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="b8964-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b8964-108">Required.</span></span> <span data-ttu-id="b8964-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="b8964-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8964-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8964-110">Remarks</span></span>  
 <span data-ttu-id="b8964-111">Element po lewej stronie operatora `^=` może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="b8964-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="b8964-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="b8964-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="b8964-113">Operator `^=` najpierw podnosi wartość zmiennej lub właściwości (po lewej stronie operatora) do potęgi wartości wyrażenia (po prawej stronie operatora)....</span><span class="sxs-lookup"><span data-stu-id="b8964-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="b8964-114">Następnie operator przypisuje wynik tej operacji z powrotem do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="b8964-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="b8964-115">Visual Basic zawsze wykonuje potęgowanie w [podwójnym typie danych](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="b8964-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="b8964-116">Operandy dowolnego typu są konwertowane na `Double`, a wynik jest zawsze `Double`.</span><span class="sxs-lookup"><span data-stu-id="b8964-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="b8964-117">Wartość `expression` może być ułamkowa, ujemna lub obie.</span><span class="sxs-lookup"><span data-stu-id="b8964-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b8964-118">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="b8964-118">Overloading</span></span>  
 <span data-ttu-id="b8964-119">[Operator ^](../../../visual-basic/language-reference/operators/exponentiation-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="b8964-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b8964-120">Przeciążanie operatora `^` ma wpływ na zachowanie operatora `^=`.</span><span class="sxs-lookup"><span data-stu-id="b8964-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="b8964-121">Jeśli kod używa `^=` na klasie lub strukturze, która przeciąża `^`, należy zapoznać się z jego ponownie zdefiniowanym zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="b8964-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b8964-122">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b8964-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8964-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8964-123">Example</span></span>  
 <span data-ttu-id="b8964-124">Poniższy przykład używa operatora `^=`, aby podnieść wartość jednej zmiennej `Integer` do potęgi drugiej zmiennej i przypisać wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b8964-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="b8964-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8964-125">See also</span></span>

- [<span data-ttu-id="b8964-126">^, operator</span><span class="sxs-lookup"><span data-stu-id="b8964-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [<span data-ttu-id="b8964-127">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="b8964-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="b8964-128">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="b8964-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="b8964-129">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b8964-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="b8964-130">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="b8964-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="b8964-131">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="b8964-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
