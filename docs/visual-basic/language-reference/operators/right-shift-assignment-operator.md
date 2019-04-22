---
title: '>>= — Operator (Visual Basic)'
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
ms.openlocfilehash: 1076ce62077391f2c88ebdd621d1dbd6fb40d647
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838966"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="3426a-102">>> = — operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3426a-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="3426a-103">Wykonuje arytmetyczne przesunięcie w prawo na wartość zmiennej lub właściwości, a następnie przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="3426a-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3426a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3426a-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="3426a-105">Części</span><span class="sxs-lookup"><span data-stu-id="3426a-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="3426a-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="3426a-106">Required.</span></span> <span data-ttu-id="3426a-107">Zmiennej lub właściwości typu całkowitego (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).</span><span class="sxs-lookup"><span data-stu-id="3426a-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="3426a-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="3426a-108">Required.</span></span> <span data-ttu-id="3426a-109">Wyrażenia liczbowego typu danych, która rozszerza się na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3426a-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3426a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3426a-110">Remarks</span></span>  
 <span data-ttu-id="3426a-111">Element w lewej części `>>=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="3426a-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="3426a-112">Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="3426a-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="3426a-113">`>>=` Operator najpierw wykonuje arytmetyczne przesunięcie w prawo na wartość zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="3426a-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="3426a-114">Operator następnie przypisuje wynik tej operacji do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="3426a-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="3426a-115">Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bity przesunięte poza jednym końcu wynik nie są ponownie wprowadzone po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="3426a-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="3426a-116">W arytmetyczne przesunięcie w prawo bity przesunięte poza Pozycja bitu po prawej stronie są odrzucane i skrajnie po lewej stronie bit jest propagowana do pozycji bitów zwolnione w wyniku po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="3426a-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="3426a-117">Oznacza to, że jeśli `variableorproperty` ma wartość ujemną, opuszczone pozycje są ustawione na jeden.</span><span class="sxs-lookup"><span data-stu-id="3426a-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="3426a-118">Jeśli `variableorproperty` jest dodatnia, lub jeśli jego typem jest typ bez znaku, pozycje opuszczonych zostaną ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="3426a-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="3426a-119">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="3426a-119">Overloading</span></span>  
 <span data-ttu-id="3426a-120">[>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="3426a-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3426a-121">Przeciążanie `>>` operator ma wpływ na zachowanie `>>=` operatora.</span><span class="sxs-lookup"><span data-stu-id="3426a-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="3426a-122">Jeśli kod używa `>>=` dla klasy lub struktury, która przeciążenia `>>`, należy zrozumieć zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="3426a-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3426a-123">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3426a-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3426a-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="3426a-124">Example</span></span>  
 <span data-ttu-id="3426a-125">W poniższym przykładzie użyto `>>=` operatora przesunięcia wzorca bitowego `Integer` zmiennej bezpośrednio przez określony przedział i przypisz wynik do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3426a-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="3426a-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3426a-126">See also</span></span>

- [<span data-ttu-id="3426a-127">>>, operator</span><span class="sxs-lookup"><span data-stu-id="3426a-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [<span data-ttu-id="3426a-128">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="3426a-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="3426a-129">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="3426a-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="3426a-130">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3426a-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="3426a-131">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="3426a-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="3426a-132">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="3426a-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
