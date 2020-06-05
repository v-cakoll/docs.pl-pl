---
title: <<=, operator
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
ms.openlocfilehash: ff7cbb02a9a10dbe11450491e93fd85fd77b44ba
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370664"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b61ec-102">\<\<= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b61ec-102">\<\<= Operator (Visual Basic)</span></span>
<span data-ttu-id="b61ec-103">Wykonuje arytmetyczne przesunięcie w lewo wartości zmiennej lub właściwości i przypisuje wynik z powrotem do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="b61ec-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b61ec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b61ec-104">Syntax</span></span>  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="b61ec-105">Części</span><span class="sxs-lookup"><span data-stu-id="b61ec-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="b61ec-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b61ec-106">Required.</span></span> <span data-ttu-id="b61ec-107">Zmienna lub właściwość typu całkowitego ( `SByte` , `Byte` ,,, `Short` , `UShort` `Integer` `UInteger` , `Long` lub `ULong` ).</span><span class="sxs-lookup"><span data-stu-id="b61ec-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="b61ec-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b61ec-108">Required.</span></span> <span data-ttu-id="b61ec-109">Wyrażenie liczbowe typu danych, które jest poszerzane do `Integer` .</span><span class="sxs-lookup"><span data-stu-id="b61ec-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b61ec-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b61ec-110">Remarks</span></span>  
 <span data-ttu-id="b61ec-111">Element po lewej stronie `<<=` operatora może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="b61ec-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="b61ec-112">Zmienna lub właściwość nie może być [tylko do odczytu](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="b61ec-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="b61ec-113">`<<=`Operator najpierw wykonuje arytmetyczne przesunięcie w lewo wartości zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="b61ec-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="b61ec-114">Następnie operator przypisuje wynik tej operacji z powrotem do tej zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="b61ec-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="b61ec-115">Przesunięcia arytmetyczne nie są cykliczne, co oznacza, że bity przesunięte poza jeden koniec wyniku nie są ponownie wprowadzane na drugim końcu.</span><span class="sxs-lookup"><span data-stu-id="b61ec-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="b61ec-116">W przypadku przesunięcia w lewo po lewej stronie bity przesunięte poza zakres typu danych wynik są odrzucane, a pozycje bitowe opuszczone po prawej stronie są ustawione na wartość zero.</span><span class="sxs-lookup"><span data-stu-id="b61ec-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b61ec-117">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="b61ec-117">Overloading</span></span>  
 <span data-ttu-id="b61ec-118">[Operator<< ](left-shift-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="b61ec-118">The [<< Operator](left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b61ec-119">Przeciążanie `<<` operatora ma wpływ na zachowanie `<<=` operatora.</span><span class="sxs-lookup"><span data-stu-id="b61ec-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="b61ec-120">Jeśli kod korzysta z `<<=` klasy lub struktury, która przeciążania `<<` , należy poznać jej ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="b61ec-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b61ec-121">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b61ec-121">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b61ec-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="b61ec-122">Example</span></span>  
 <span data-ttu-id="b61ec-123">Poniższy przykład używa operatora, `<<=` Aby przesunąć wzorzec bitowy `Integer` zmiennej o podanej wartości i przypisać wynik do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b61ec-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="b61ec-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b61ec-124">See also</span></span>

- [<span data-ttu-id="b61ec-125">Operator<< </span><span class="sxs-lookup"><span data-stu-id="b61ec-125"><< Operator</span></span>](left-shift-operator.md)
- [<span data-ttu-id="b61ec-126">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="b61ec-126">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="b61ec-127">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="b61ec-127">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="b61ec-128">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b61ec-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="b61ec-129">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="b61ec-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="b61ec-130">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="b61ec-130">Statements</span></span>](../../programming-guide/language-features/statements.md)
