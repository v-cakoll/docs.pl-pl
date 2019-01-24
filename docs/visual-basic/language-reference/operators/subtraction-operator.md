---
title: '- — Operator (Visual Basic)'
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
ms.openlocfilehash: 8526f632b7e54c03bd16c3af70375179cd7cf277
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724476"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="1a236-102">- — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a236-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="1a236-103">Zwraca różnicę dwóch wyrażeń liczbowych lub wartość ujemną wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="1a236-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a236-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a236-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="1a236-105">Części</span><span class="sxs-lookup"><span data-stu-id="1a236-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="1a236-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1a236-106">Required.</span></span> <span data-ttu-id="1a236-107">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="1a236-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="1a236-108">Wymagane, chyba że `–` operator obliczania wartości ujemnej.</span><span class="sxs-lookup"><span data-stu-id="1a236-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="1a236-109">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="1a236-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="1a236-110">Wynik</span><span class="sxs-lookup"><span data-stu-id="1a236-110">Result</span></span>  
 <span data-ttu-id="1a236-111">Wynik jest różnica między `expression1` i `expression2`, lub zanegowaną wartość `expression1`.</span><span class="sxs-lookup"><span data-stu-id="1a236-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="1a236-112">Typ danych wynik jest typu liczbowego, odpowiednie dla typów danych `expression1` i `expression2`.</span><span class="sxs-lookup"><span data-stu-id="1a236-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="1a236-113">Zobacz tabele "Integer arytmetyczny" w [typów danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="1a236-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="1a236-114">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="1a236-114">Supported Types</span></span>  
 <span data-ttu-id="1a236-115">Wszystkich typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="1a236-115">All numeric types.</span></span> <span data-ttu-id="1a236-116">Obejmuje to typy bez znaku i błędy liczb zmiennopozycyjnych i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1a236-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a236-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a236-117">Remarks</span></span>  
 <span data-ttu-id="1a236-118">W pierwsze użycie, które są wyświetlane w składni przedstawionej wcześniej `–` operator jest *binarne* operator odejmowania arytmetycznych, różnicy między dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="1a236-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="1a236-119">Użycie drugiej, wyświetlana w składni przedstawionej wcześniej `–` operator jest *jednoargumentowe* operator negacji ujemną wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1a236-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="1a236-120">W tym sensie negację składa się z cofania znak `expression1` tak, aby wynik jest dodatni Jeśli `expression1` jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="1a236-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="1a236-121">Jeśli wyrażenie zwraca [nic](../../../visual-basic/language-reference/nothing.md), `–` operator traktuje ją jako zero.</span><span class="sxs-lookup"><span data-stu-id="1a236-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a236-122">`–` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="1a236-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1a236-123">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="1a236-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="1a236-124">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1a236-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a236-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a236-125">Example</span></span>  
 <span data-ttu-id="1a236-126">W poniższym przykładzie użyto `–` operator, aby obliczyć i zwracać różnicę między dwoma liczbami, a następnie do zanegowania liczbą.</span><span class="sxs-lookup"><span data-stu-id="1a236-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 <span data-ttu-id="1a236-127">Po wykonaniu tych instrukcji `binaryResult` zawiera 124.45 i `unaryResult` zawiera –334.90.</span><span class="sxs-lookup"><span data-stu-id="1a236-127">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a236-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a236-128">See also</span></span>
- [<span data-ttu-id="1a236-129">-= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a236-129">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="1a236-130">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="1a236-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="1a236-131">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1a236-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="1a236-132">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="1a236-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="1a236-133">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1a236-133">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
