---
title: '&amp; = — operator (Visual Basic)'
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
ms.openlocfilehash: 82d791e5d66c301442c99d2cc73e3172c3e30f17
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591638"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="09792-102">&amp; = — operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09792-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="09792-103">Łączy wyrażenie `String` z zmienną lub właściwością `String` i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="09792-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09792-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09792-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="09792-105">Części</span><span class="sxs-lookup"><span data-stu-id="09792-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="09792-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="09792-106">Required.</span></span> <span data-ttu-id="09792-107">Dowolna `String` zmienna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="09792-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="09792-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="09792-108">Required.</span></span> <span data-ttu-id="09792-109">Dowolne wyrażenie `String`.</span><span class="sxs-lookup"><span data-stu-id="09792-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09792-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09792-110">Remarks</span></span>  
 <span data-ttu-id="09792-111">Element po lewej stronie operatora `&=` może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="09792-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="09792-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="09792-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="09792-113">Operator `&=` łączy wyrażenie `String` po prawej stronie z zmienną `String` lub właściwością po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwości po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="09792-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="09792-114">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="09792-114">Overloading</span></span>  
 <span data-ttu-id="09792-115">[Operator &](../../../visual-basic/language-reference/operators/concatenation-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="09792-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="09792-116">Przeciążanie operatora `&` wpływa na zachowanie operatora `&=`.</span><span class="sxs-lookup"><span data-stu-id="09792-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="09792-117">Jeśli kod używa `&=` na klasie lub strukturze, która przeciąża `&`, należy zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="09792-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="09792-118">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="09792-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09792-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="09792-119">Example</span></span>  
 <span data-ttu-id="09792-120">Poniższy przykład używa operatora `&=`, aby połączyć dwie zmienne `String` i przypisać wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="09792-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="09792-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09792-121">See also</span></span>

- [<span data-ttu-id="09792-122">&, operator</span><span class="sxs-lookup"><span data-stu-id="09792-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="09792-123">+=, operator</span><span class="sxs-lookup"><span data-stu-id="09792-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="09792-124">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="09792-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="09792-125">Operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="09792-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="09792-126">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="09792-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="09792-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="09792-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="09792-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="09792-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
