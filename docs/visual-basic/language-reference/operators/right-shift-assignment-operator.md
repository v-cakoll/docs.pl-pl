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
ms.openlocfilehash: 08d4e251a96ca387a709319e752351db6825d9e8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701354"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="ed96d-102">> > = — operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed96d-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="ed96d-103">Wykonuje arytmetyczne przesunięcie w prawo wartości zmiennej lub właściwości i przypisuje wynik z powrotem do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed96d-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed96d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed96d-104">Syntax</span></span>  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="ed96d-105">Części</span><span class="sxs-lookup"><span data-stu-id="ed96d-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="ed96d-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="ed96d-106">Required.</span></span> <span data-ttu-id="ed96d-107">Zmienna lub właściwość typu całkowitego (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` lub `ULong`).</span><span class="sxs-lookup"><span data-stu-id="ed96d-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="ed96d-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="ed96d-108">Required.</span></span> <span data-ttu-id="ed96d-109">Wyrażenie liczbowe typu danych, które poszerza do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ed96d-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed96d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed96d-110">Remarks</span></span>  
 <span data-ttu-id="ed96d-111">Element po lewej stronie operatora `>>=` może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="ed96d-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="ed96d-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="ed96d-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="ed96d-113">Operator `>>=` najpierw wykonuje arytmetyczne przesunięcie w prawo na wartości zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed96d-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="ed96d-114">Następnie operator przypisuje wynik tej operacji z powrotem do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed96d-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="ed96d-115">Przesunięcia arytmetyczne nie są cykliczne, co oznacza, że bity przesunięte poza jeden koniec wyniku nie są ponownie wprowadzane na drugim końcu.</span><span class="sxs-lookup"><span data-stu-id="ed96d-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="ed96d-116">W wyniku przesunięcia w prawo arytmetyczne bity przesunięte poza skrajną prawą pozycję bitu są odrzucane, a bit z lewej strony jest propagowany do pozycji bitowych opuszczone w lewo.</span><span class="sxs-lookup"><span data-stu-id="ed96d-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="ed96d-117">Oznacza to, że jeśli `variableorproperty` ma wartość ujemną, pozycje opuszczone są ustawione na jeden.</span><span class="sxs-lookup"><span data-stu-id="ed96d-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="ed96d-118">Jeśli `variableorproperty` jest dodatnia lub jeśli typ danych jest typem bez znaku, pozycje opuszczone są ustawione na wartość zero.</span><span class="sxs-lookup"><span data-stu-id="ed96d-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ed96d-119">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="ed96d-119">Overloading</span></span>  
 <span data-ttu-id="ed96d-120">[Operator > >](../../../visual-basic/language-reference/operators/right-shift-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ed96d-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ed96d-121">Przeciążanie operatora `>>` wpływa na zachowanie operatora `>>=`.</span><span class="sxs-lookup"><span data-stu-id="ed96d-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="ed96d-122">Jeśli kod używa `>>=` na klasie lub strukturze, która przeciąża `>>`, należy zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="ed96d-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ed96d-123">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ed96d-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed96d-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed96d-124">Example</span></span>  
 <span data-ttu-id="ed96d-125">Poniższy przykład używa operatora `>>=`, aby przesunąć wzorzec bitowy zmiennej `Integer` bezpośrednio o określoną wartość i przypisać wynik do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ed96d-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="ed96d-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed96d-126">See also</span></span>

- [<span data-ttu-id="ed96d-127">>>, operator</span><span class="sxs-lookup"><span data-stu-id="ed96d-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [<span data-ttu-id="ed96d-128">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="ed96d-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="ed96d-129">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="ed96d-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="ed96d-130">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed96d-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="ed96d-131">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="ed96d-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="ed96d-132">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="ed96d-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
