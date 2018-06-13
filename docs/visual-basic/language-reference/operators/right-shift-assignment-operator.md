---
title: '&gt;&gt;= — Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: d0c0ea819741f80e30e55a960b1187699898a3bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604110"
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="1c67c-102">&gt;&gt;= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c67c-102">&gt;&gt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="1c67c-103">Wykonuje arytmetyczne przesunięcie w prawo na wartość zmiennej lub właściwości i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="1c67c-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c67c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c67c-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="1c67c-105">Części</span><span class="sxs-lookup"><span data-stu-id="1c67c-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="1c67c-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1c67c-106">Required.</span></span> <span data-ttu-id="1c67c-107">Zmienna lub właściwość typu całkowitego (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).</span><span class="sxs-lookup"><span data-stu-id="1c67c-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="1c67c-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1c67c-108">Required.</span></span> <span data-ttu-id="1c67c-109">Wyrażenia liczbowego typu danych rozszerzająca do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="1c67c-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c67c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c67c-110">Remarks</span></span>  
 <span data-ttu-id="1c67c-111">Element po lewej stronie `>>=` operator może być zmienną skalarną proste, właściwością lub element tablicy.</span><span class="sxs-lookup"><span data-stu-id="1c67c-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="1c67c-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="1c67c-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="1c67c-113">`>>=` Operator najpierw wykonuje arytmetyczne przesunięcie w prawo na wartość zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="1c67c-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="1c67c-114">Następnie operator przypisuje wynik tej operacji do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="1c67c-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="1c67c-115">Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bitów przesunąć poza jednym zakończeniu wynik nie są ponownie na drugim końcu.</span><span class="sxs-lookup"><span data-stu-id="1c67c-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="1c67c-116">W arytmetyczne przesunięcie w prawo bitów przesunięty poza Pozycja bitu po prawej stronie zostaną odrzucone i lewej bit jest propagowana do pozycji z bitowego vacated po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="1c67c-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="1c67c-117">Oznacza to, że jeśli `variableorproperty` ma wartość ujemną vacated pozycje są ustawione na jedną.</span><span class="sxs-lookup"><span data-stu-id="1c67c-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="1c67c-118">Jeśli `variableorproperty` jest dodatnia, lub jeśli jego typem jest typ bez znaku, vacated pozycji zostaną ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="1c67c-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="1c67c-119">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="1c67c-119">Overloading</span></span>  
 <span data-ttu-id="1c67c-120">[>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="1c67c-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1c67c-121">Przeciążanie `>>` operator wpływa na działanie `>>=` operatora.</span><span class="sxs-lookup"><span data-stu-id="1c67c-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="1c67c-122">Jeśli używa Twój kod `>>=` na klasę lub strukturę, która overloads `>>`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="1c67c-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1c67c-123">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1c67c-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c67c-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c67c-124">Example</span></span>  
 <span data-ttu-id="1c67c-125">W poniższym przykładzie użyto `>>=` operator przesunięcia wzorca bitowego z `Integer` zmiennej bezpośrednio przez określony i przypisz wynik do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1c67c-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1c67c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c67c-126">See Also</span></span>  
 [<span data-ttu-id="1c67c-127">>>, operator</span><span class="sxs-lookup"><span data-stu-id="1c67c-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)  
 [<span data-ttu-id="1c67c-128">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="1c67c-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="1c67c-129">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="1c67c-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="1c67c-130">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c67c-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="1c67c-131">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="1c67c-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="1c67c-132">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="1c67c-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
