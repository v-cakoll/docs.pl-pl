---
title: '&amp;= — operator'
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
ms.openlocfilehash: 8668bfcbf32bb34b422efe8116bbd12a2d80b1d4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350265"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="c6924-102">&amp;= — operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6924-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="c6924-103">Łączy wyrażenie `String` ze zmienną `String` lub właściwością i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="c6924-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6924-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6924-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="c6924-105">Części</span><span class="sxs-lookup"><span data-stu-id="c6924-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="c6924-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c6924-106">Required.</span></span> <span data-ttu-id="c6924-107">Dowolna `String` zmienna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="c6924-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="c6924-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c6924-108">Required.</span></span> <span data-ttu-id="c6924-109">Dowolne wyrażenie `String`.</span><span class="sxs-lookup"><span data-stu-id="c6924-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6924-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6924-110">Remarks</span></span>  
 <span data-ttu-id="c6924-111">Element po lewej stronie operatora `&=` może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="c6924-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="c6924-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="c6924-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="c6924-113">Operator `&=` łączy wyrażenie `String` po prawej stronie ze zmienną `String` lub właściwości po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwości po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="c6924-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c6924-114">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="c6924-114">Overloading</span></span>  
 <span data-ttu-id="c6924-115">[Operator &](../../../visual-basic/language-reference/operators/concatenation-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="c6924-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c6924-116">Przeciążanie operatora `&` ma wpływ na zachowanie operatora `&=`.</span><span class="sxs-lookup"><span data-stu-id="c6924-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="c6924-117">Jeśli kod używa `&=` na klasie lub strukturze, która przeciąża `&`, należy zapoznać się z jego ponownie zdefiniowanym zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="c6924-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c6924-118">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c6924-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6924-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="c6924-119">Example</span></span>  
 <span data-ttu-id="c6924-120">Poniższy przykład używa operatora `&=`, aby połączyć dwie zmienne `String` i przypisać wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c6924-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c6924-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6924-121">See also</span></span>

- [<span data-ttu-id="c6924-122">&, operator</span><span class="sxs-lookup"><span data-stu-id="c6924-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="c6924-123">+=, operator</span><span class="sxs-lookup"><span data-stu-id="c6924-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="c6924-124">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="c6924-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="c6924-125">Operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="c6924-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="c6924-126">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6924-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="c6924-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="c6924-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="c6924-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="c6924-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
