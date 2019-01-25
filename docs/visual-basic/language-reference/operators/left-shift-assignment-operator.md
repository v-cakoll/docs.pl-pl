---
title: '&lt;&lt;= — Operator (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 9d4f367506c847ddf2478dd1ea07e28332cc62a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677774"
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="ae0b9-102">&lt;&lt;= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae0b9-102">&lt;&lt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="ae0b9-103">Wykonuje arytmetyczne przesunięcie w lewo na wartość zmiennej lub właściwości, a następnie przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae0b9-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae0b9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae0b9-104">Syntax</span></span>  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="ae0b9-105">Części</span><span class="sxs-lookup"><span data-stu-id="ae0b9-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="ae0b9-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ae0b9-106">Required.</span></span> <span data-ttu-id="ae0b9-107">Zmiennej lub właściwości typu całkowitego (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).</span><span class="sxs-lookup"><span data-stu-id="ae0b9-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="ae0b9-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ae0b9-108">Required.</span></span> <span data-ttu-id="ae0b9-109">Wyrażenia liczbowego typu danych, która rozszerza się na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ae0b9-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae0b9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae0b9-110">Remarks</span></span>  
 <span data-ttu-id="ae0b9-111">Element w lewej części `<<=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="ae0b9-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="ae0b9-112">Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="ae0b9-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="ae0b9-113">`<<=` Operator najpierw wykonuje arytmetyczne przesunięcie w lewo na wartość zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae0b9-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="ae0b9-114">Operator następnie przypisuje wynik tej operacji do tej zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae0b9-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="ae0b9-115">Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bity przesunięte poza jednym końcu wynik nie są ponownie wprowadzone po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="ae0b9-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="ae0b9-116">W arytmetyczne przesunięcie w lewo bity przesunięte poza zakresem typu danych wyniku są odrzucane i pozycje bitów zwolnione w wyniku po prawej stronie zostaną ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="ae0b9-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ae0b9-117">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="ae0b9-117">Overloading</span></span>  
 <span data-ttu-id="ae0b9-118">[<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ae0b9-118">The [<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ae0b9-119">Przeciążanie `<<` operator ma wpływ na zachowanie `<<=` operatora.</span><span class="sxs-lookup"><span data-stu-id="ae0b9-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="ae0b9-120">Jeśli kod używa `<<=` dla klasy lub struktury, która przeciążenia `<<`, należy zrozumieć zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="ae0b9-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ae0b9-121">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ae0b9-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae0b9-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae0b9-122">Example</span></span>  
 <span data-ttu-id="ae0b9-123">W poniższym przykładzie użyto `<<=` operatora przesunięcia wzorca bitowego `Integer` zmiennej pozostawiony przez określony przedział i przypisz wynik do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ae0b9-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ae0b9-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae0b9-124">See also</span></span>
- [<span data-ttu-id="ae0b9-125"><<, operator</span><span class="sxs-lookup"><span data-stu-id="ae0b9-125"><< Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [<span data-ttu-id="ae0b9-126">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="ae0b9-126">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="ae0b9-127">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="ae0b9-127">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="ae0b9-128">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae0b9-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="ae0b9-129">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="ae0b9-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="ae0b9-130">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="ae0b9-130">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
