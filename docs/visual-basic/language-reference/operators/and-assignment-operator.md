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
ms.openlocfilehash: c3db2d4095600f32af92d1a4ce1f806a3f032af0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601884"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="141bb-102">&amp;= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="141bb-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="141bb-103">Łączy `String` wyrażenie `String` zmienna lub właściwość i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="141bb-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="141bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="141bb-104">Syntax</span></span>  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="141bb-105">Części</span><span class="sxs-lookup"><span data-stu-id="141bb-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="141bb-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="141bb-106">Required.</span></span> <span data-ttu-id="141bb-107">Wszelkie `String` zmienna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="141bb-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="141bb-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="141bb-108">Required.</span></span> <span data-ttu-id="141bb-109">Wszelkie `String` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="141bb-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="141bb-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="141bb-110">Remarks</span></span>  
 <span data-ttu-id="141bb-111">Element po lewej stronie `&=` operator może być zmienną skalarną proste, właściwością lub element tablicy.</span><span class="sxs-lookup"><span data-stu-id="141bb-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="141bb-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="141bb-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="141bb-113">`&=` Łączy operator `String` wyrażenie jego prawej strony, aby `String` zmienna lub właściwość po lewej stronie i przypisuje wynik do zmiennej lub właściwości po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="141bb-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="141bb-114">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="141bb-114">Overloading</span></span>  
 <span data-ttu-id="141bb-115">[& — Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="141bb-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="141bb-116">Przeciążanie `&` operator wpływa na działanie `&=` operatora.</span><span class="sxs-lookup"><span data-stu-id="141bb-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="141bb-117">Jeśli używa Twój kod `&=` na klasę lub strukturę, która overloads `&`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="141bb-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="141bb-118">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="141bb-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="141bb-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="141bb-119">Example</span></span>  
 <span data-ttu-id="141bb-120">W poniższym przykładzie użyto `&=` operator do łączenia dwóch `String` zmiennych i przypisz wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="141bb-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="141bb-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="141bb-121">See Also</span></span>  
 [<span data-ttu-id="141bb-122">&, operator</span><span class="sxs-lookup"><span data-stu-id="141bb-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [<span data-ttu-id="141bb-123">+=, operator</span><span class="sxs-lookup"><span data-stu-id="141bb-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [<span data-ttu-id="141bb-124">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="141bb-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="141bb-125">Operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="141bb-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="141bb-126">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="141bb-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="141bb-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="141bb-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="141bb-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="141bb-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
