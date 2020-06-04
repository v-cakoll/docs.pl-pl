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
ms.openlocfilehash: 6539beb5cf8078281357445e2391fac189208087
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406357"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="f9adb-102">- — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9adb-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="f9adb-103">Zwraca różnicę między dwoma wyrażeniami liczbowymi lub wartością ujemną wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="f9adb-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9adb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9adb-104">Syntax</span></span>  
  
```vb  
expression1 – expression2
```
  
<span data-ttu-id="f9adb-105">lub</span><span class="sxs-lookup"><span data-stu-id="f9adb-105">or</span></span>

```vb  
–expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="f9adb-106">Części</span><span class="sxs-lookup"><span data-stu-id="f9adb-106">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="f9adb-107">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f9adb-107">Required.</span></span> <span data-ttu-id="f9adb-108">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="f9adb-108">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="f9adb-109">Wymagane, chyba że `–` operator oblicza wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="f9adb-109">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="f9adb-110">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="f9adb-110">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="f9adb-111">Wynik</span><span class="sxs-lookup"><span data-stu-id="f9adb-111">Result</span></span>  
 <span data-ttu-id="f9adb-112">Wynikiem jest różnica między `expression1` i `expression2` lub Negacja wartości `expression1` .</span><span class="sxs-lookup"><span data-stu-id="f9adb-112">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="f9adb-113">Typ danych wyniku jest typem liczbowym odpowiednim dla typów danych `expression1` i `expression2` .</span><span class="sxs-lookup"><span data-stu-id="f9adb-113">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="f9adb-114">Zobacz tabele "arytmetyczne liczby całkowite" w [typach danych wyników operatora](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="f9adb-114">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="f9adb-115">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="f9adb-115">Supported Types</span></span>  
 <span data-ttu-id="f9adb-116">Wszystkie typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="f9adb-116">All numeric types.</span></span> <span data-ttu-id="f9adb-117">Obejmuje to typy niepodpisane i zmiennoprzecinkowe oraz `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="f9adb-117">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9adb-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9adb-118">Remarks</span></span>  
 <span data-ttu-id="f9adb-119">W pierwszym użyciu pokazanym w pokazanej wcześniej składni `–` operator to *binarny* operator odejmowania arytmetycznego dla różnicy między dwoma wyrażeniami liczbowymi.</span><span class="sxs-lookup"><span data-stu-id="f9adb-119">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="f9adb-120">W drugim wykorzystaniu pokazanym w składni pokazanej wcześniej `–` operator jest *jednoargumentowym* operatorem negacji dla wartości ujemnej wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f9adb-120">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="f9adb-121">W tym sensie Negacja składa się z odwrócenia znaku, `expression1` aby wynik był dodatni, jeśli `expression1` jest ujemny.</span><span class="sxs-lookup"><span data-stu-id="f9adb-121">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="f9adb-122">Jeśli wyrażenie zwróci wartość [Nothing](../nothing.md), `–` operator traktuje ją jako zero.</span><span class="sxs-lookup"><span data-stu-id="f9adb-122">If either expression evaluates to [Nothing](../nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9adb-123">`–`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f9adb-123">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f9adb-124">Jeśli kod używa tego operatora dla takiej klasy lub struktury, upewnij się, że rozumiesz jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f9adb-124">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="f9adb-125">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f9adb-125">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9adb-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9adb-126">Example</span></span>  
 <span data-ttu-id="f9adb-127">Poniższy przykład używa operatora, `–` Aby obliczyć i zwrócić różnicę między dwiema liczbami, a następnie Negate liczbę.</span><span class="sxs-lookup"><span data-stu-id="f9adb-127">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="f9adb-128">Po wykonaniu tych instrukcji `binaryResult` zawiera 124,45 i `unaryResult` zawiera – 334,90.</span><span class="sxs-lookup"><span data-stu-id="f9adb-128">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9adb-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9adb-129">See also</span></span>

- [<span data-ttu-id="f9adb-130">-= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9adb-130">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="f9adb-131">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="f9adb-131">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="f9adb-132">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9adb-132">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f9adb-133">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="f9adb-133">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f9adb-134">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f9adb-134">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
