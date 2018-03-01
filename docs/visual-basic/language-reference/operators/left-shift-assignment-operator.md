---
title: "&lt;&lt;= — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c5c36e4f91155c09d01b448777483941d018d9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="b0d82-102">&lt;&lt;= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0d82-102">&lt;&lt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="b0d82-103">Wykonuje arytmetyczne przesunięcie w lewo na wartość zmiennej lub właściwości i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0d82-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0d82-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0d82-104">Syntax</span></span>  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="b0d82-105">Części</span><span class="sxs-lookup"><span data-stu-id="b0d82-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="b0d82-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b0d82-106">Required.</span></span> <span data-ttu-id="b0d82-107">Zmienna lub właściwość typu całkowitego (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).</span><span class="sxs-lookup"><span data-stu-id="b0d82-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="b0d82-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b0d82-108">Required.</span></span> <span data-ttu-id="b0d82-109">Wyrażenia liczbowego typu danych rozszerzająca do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b0d82-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0d82-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0d82-110">Remarks</span></span>  
 <span data-ttu-id="b0d82-111">Element po lewej stronie `<<=` operator może być zmienną skalarną proste, właściwością lub element tablicy.</span><span class="sxs-lookup"><span data-stu-id="b0d82-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="b0d82-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="b0d82-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="b0d82-113">`<<=` Operator najpierw wykonuje arytmetyczne przesunięcie w lewo na wartość zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0d82-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="b0d82-114">Następnie operator przypisuje wynik tej operacji do tej zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0d82-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="b0d82-115">Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bitów przesunąć poza jednym zakończeniu wynik nie są ponownie na drugim końcu.</span><span class="sxs-lookup"><span data-stu-id="b0d82-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="b0d82-116">W arytmetyczne przesunięcie w lewo bitów przesunięty poza zakresem typu danych zostaną odrzucone i pozycji z bitowego vacated po prawej stronie zostaną ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="b0d82-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b0d82-117">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="b0d82-117">Overloading</span></span>  
 <span data-ttu-id="b0d82-118">[<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="b0d82-118">The [<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b0d82-119">Przeciążanie `<<` operator wpływa na działanie `<<=` operatora.</span><span class="sxs-lookup"><span data-stu-id="b0d82-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="b0d82-120">Jeśli używa Twój kod `<<=` na klasę lub strukturę, która overloads `<<`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="b0d82-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b0d82-121">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b0d82-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0d82-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0d82-122">Example</span></span>  
 <span data-ttu-id="b0d82-123">W poniższym przykładzie użyto `<<=` operator przesunięcia wzorca bitowego z `Integer` zmiennej po określonym i przypisz wynik do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b0d82-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b0d82-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0d82-124">See Also</span></span>  
 [<span data-ttu-id="b0d82-125"><< — Operator</span><span class="sxs-lookup"><span data-stu-id="b0d82-125"><< Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-operator.md)  
 [<span data-ttu-id="b0d82-126">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="b0d82-126">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="b0d82-127">Bit Shift — operatory</span><span class="sxs-lookup"><span data-stu-id="b0d82-127">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="b0d82-128">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0d82-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="b0d82-129">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="b0d82-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="b0d82-130">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="b0d82-130">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
