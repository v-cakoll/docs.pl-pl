---
title: '&amp;= — Operator (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 929a9e8c3384451679fc52ad478eb03219d67192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="fdd55-102">&amp;= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdd55-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="fdd55-103">Łączy `String` wyrażenie `String` zmienna lub właściwość i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="fdd55-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdd55-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdd55-104">Syntax</span></span>  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="fdd55-105">Części</span><span class="sxs-lookup"><span data-stu-id="fdd55-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="fdd55-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="fdd55-106">Required.</span></span> <span data-ttu-id="fdd55-107">Wszelkie `String` zmienna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="fdd55-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="fdd55-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="fdd55-108">Required.</span></span> <span data-ttu-id="fdd55-109">Wszelkie `String` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fdd55-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdd55-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fdd55-110">Remarks</span></span>  
 <span data-ttu-id="fdd55-111">Element po lewej stronie `&=` operator może być zmienną skalarną proste, właściwością lub element tablicy.</span><span class="sxs-lookup"><span data-stu-id="fdd55-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="fdd55-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="fdd55-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="fdd55-113">`&=` Łączy operator `String` wyrażenie jego prawej strony, aby `String` zmienna lub właściwość po lewej stronie i przypisuje wynik do zmiennej lub właściwości po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="fdd55-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="fdd55-114">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="fdd55-114">Overloading</span></span>  
 <span data-ttu-id="fdd55-115">[& — Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fdd55-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="fdd55-116">Przeciążanie `&` operator wpływa na działanie `&=` operatora.</span><span class="sxs-lookup"><span data-stu-id="fdd55-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="fdd55-117">Jeśli używa Twój kod `&=` na klasę lub strukturę, która overloads `&`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="fdd55-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="fdd55-118">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="fdd55-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdd55-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="fdd55-119">Example</span></span>  
 <span data-ttu-id="fdd55-120">W poniższym przykładzie użyto `&=` operator do łączenia dwóch `String` zmiennych i przypisz wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fdd55-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fdd55-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fdd55-121">See Also</span></span>  
 [<span data-ttu-id="fdd55-122">& — Operator</span><span class="sxs-lookup"><span data-stu-id="fdd55-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [<span data-ttu-id="fdd55-123">+= — Operator</span><span class="sxs-lookup"><span data-stu-id="fdd55-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [<span data-ttu-id="fdd55-124">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="fdd55-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="fdd55-125">Operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="fdd55-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="fdd55-126">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fdd55-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="fdd55-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="fdd55-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="fdd55-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="fdd55-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
