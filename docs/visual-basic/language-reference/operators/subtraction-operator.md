---
title: '- Operator'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 9687c366c5b23693c05ab5c6b34f50c04131dfda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348225"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="640fc-102">- — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="640fc-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="640fc-103">Zwraca różnicę między dwoma wyrażeniami liczbowymi lub wartością ujemną wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="640fc-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="640fc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="640fc-104">Syntax</span></span>  
  
```vb  
expression1 – expression2
```
  
<span data-ttu-id="640fc-105">lub</span><span class="sxs-lookup"><span data-stu-id="640fc-105">or</span></span>

```vb  
–expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="640fc-106">Części</span><span class="sxs-lookup"><span data-stu-id="640fc-106">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="640fc-107">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="640fc-107">Required.</span></span> <span data-ttu-id="640fc-108">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="640fc-108">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="640fc-109">Wymagany, chyba że operator `–` oblicza wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="640fc-109">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="640fc-110">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="640fc-110">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="640fc-111">Wynik</span><span class="sxs-lookup"><span data-stu-id="640fc-111">Result</span></span>  
 <span data-ttu-id="640fc-112">Wynikiem jest różnica między `expression1` i `expression2`lub Negacja wartości `expression1`.</span><span class="sxs-lookup"><span data-stu-id="640fc-112">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="640fc-113">Typ danych wyniku jest typem liczbowym odpowiednim dla typów danych `expression1` i `expression2`.</span><span class="sxs-lookup"><span data-stu-id="640fc-113">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="640fc-114">Zobacz tabele "arytmetyczne liczby całkowite" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="640fc-114">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="640fc-115">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="640fc-115">Supported Types</span></span>  
 <span data-ttu-id="640fc-116">Wszystkie typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="640fc-116">All numeric types.</span></span> <span data-ttu-id="640fc-117">Obejmuje to typy niepodpisane i zmiennoprzecinkowe oraz `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="640fc-117">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="640fc-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="640fc-118">Remarks</span></span>  
 <span data-ttu-id="640fc-119">W pierwszym użyciu pokazanym w pokazanej wcześniej składni operator `–` to *binarny* operator odejmowania arytmetycznego dla różnicy między dwoma wyrażeniami liczbowymi.</span><span class="sxs-lookup"><span data-stu-id="640fc-119">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="640fc-120">W drugim wykorzystaniu pokazanym wcześniej składni operator `–` jest operatorem *jednoargumentowym* operatora negacji dla wartości ujemnej wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="640fc-120">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="640fc-121">W tym sensie Negacja składa się z odwrócenia znaku `expression1`, aby wynik był dodatni, jeśli `expression1` jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="640fc-121">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="640fc-122">Jeśli wyrażenie zwróci wartość [Nothing](../../../visual-basic/language-reference/nothing.md), operator `–` traktuje ją jako zero.</span><span class="sxs-lookup"><span data-stu-id="640fc-122">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="640fc-123">Operator `–` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="640fc-123">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="640fc-124">Jeśli kod używa tego operatora dla takiej klasy lub struktury, upewnij się, że rozumiesz jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="640fc-124">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="640fc-125">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="640fc-125">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="640fc-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="640fc-126">Example</span></span>  
 <span data-ttu-id="640fc-127">Poniższy przykład używa operatora `–`, aby obliczyć i zwrócić różnicę między dwiema liczbami, a następnie Negate liczbę.</span><span class="sxs-lookup"><span data-stu-id="640fc-127">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="640fc-128">Po wykonaniu tych instrukcji `binaryResult` zawiera 124,45 i `unaryResult` Contains – 334,90.</span><span class="sxs-lookup"><span data-stu-id="640fc-128">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="640fc-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="640fc-129">See also</span></span>

- [<span data-ttu-id="640fc-130">-= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="640fc-130">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="640fc-131">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="640fc-131">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="640fc-132">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="640fc-132">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="640fc-133">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="640fc-133">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="640fc-134">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="640fc-134">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
