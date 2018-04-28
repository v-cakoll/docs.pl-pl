---
title: Kolejność wykonywania działań (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d8de9deea84c7f0c11c91b55951cdfc200b017f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="a8db1-102">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8db1-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="a8db1-103">Gdy występują kilka operacji w wyrażeniu, każda część jest oceniane i rozpoznać w ustalonej kolejności o nazwie *kolejność*.</span><span class="sxs-lookup"><span data-stu-id="a8db1-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>  
  
## <a name="precedence-rules"></a><span data-ttu-id="a8db1-104">Reguły pierwszeństwa</span><span class="sxs-lookup"><span data-stu-id="a8db1-104">Precedence Rules</span></span>  
 <span data-ttu-id="a8db1-105">Jeśli wyrażenia zawierają operatory z więcej niż jedną kategorię, są one oceniane zgodnie z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="a8db1-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>  
  
-   <span data-ttu-id="a8db1-106">Operatory arytmetyczne i łączenia mają kolejność pierwszeństwa opisane w poniższej sekcji, a wszystkie mają wyższy priorytet niż porównanie logiczne i operatory bitowe.</span><span class="sxs-lookup"><span data-stu-id="a8db1-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>  
  
-   <span data-ttu-id="a8db1-107">Wszystkie operatory porównania ma taki sam priorytet i wszystkie mają wyższy priorytet niż operatory logiczne i bitowe, ale niższy priorytet niż operatory arytmetyczne i łączenia.</span><span class="sxs-lookup"><span data-stu-id="a8db1-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>  
  
-   <span data-ttu-id="a8db1-108">Operatory logiczne i bitowe mają kolejność pierwszeństwa opisane w poniższej sekcji, a wszystkie mieć niższego pierwszeństwa niż arytmetyczne, łączenie i operatory porównania.</span><span class="sxs-lookup"><span data-stu-id="a8db1-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>  
  
-   <span data-ttu-id="a8db1-109">Operatory z równy priorytet są wykonywane od lewej do prawej w kolejności, w jakiej występują w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="a8db1-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>  
  
## <a name="precedence-order"></a><span data-ttu-id="a8db1-110">Kolejność pierwszeństwa</span><span class="sxs-lookup"><span data-stu-id="a8db1-110">Precedence Order</span></span>  
 <span data-ttu-id="a8db1-111">Operatory są oceniane w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="a8db1-111">Operators are evaluated in the following order of precedence:</span></span>  
  
### <a name="await-operator"></a><span data-ttu-id="a8db1-112">Await — Operator</span><span class="sxs-lookup"><span data-stu-id="a8db1-112">Await Operator</span></span>  
 <span data-ttu-id="a8db1-113">await</span><span class="sxs-lookup"><span data-stu-id="a8db1-113">Await</span></span>  
  
### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="a8db1-114">Operacje arytmetyczne i operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="a8db1-114">Arithmetic and Concatenation Operators</span></span>  
 <span data-ttu-id="a8db1-115">Zapis wykładniczy (`^`)</span><span class="sxs-lookup"><span data-stu-id="a8db1-115">Exponentiation (`^`)</span></span>  
  
 <span data-ttu-id="a8db1-116">Jednoargumentowy tożsamości i negacji (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="a8db1-116">Unary identity and negation (`+`, `–`)</span></span>  
  
 <span data-ttu-id="a8db1-117">Mnożenia i dzielenia liczb zmiennoprzecinkowych (`*`, `/`)</span><span class="sxs-lookup"><span data-stu-id="a8db1-117">Multiplication and floating-point division (`*`, `/`)</span></span>  
  
 <span data-ttu-id="a8db1-118">Dzielenie liczby całkowitej (`\`)</span><span class="sxs-lookup"><span data-stu-id="a8db1-118">Integer division (`\`)</span></span>  
  
 <span data-ttu-id="a8db1-119">Arytmetycznego modulo (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="a8db1-119">Modulus arithmetic (`Mod`)</span></span>  
  
 <span data-ttu-id="a8db1-120">Dodawanie i odejmowanie (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="a8db1-120">Addition and subtraction (`+`, `–`)</span></span>  
  
 <span data-ttu-id="a8db1-121">Łączenie ciągów (`&`)</span><span class="sxs-lookup"><span data-stu-id="a8db1-121">String concatenation (`&`)</span></span>  
  
 <span data-ttu-id="a8db1-122">Przesunięcia bitowego arytmetyczne (`<<`, `>>`)</span><span class="sxs-lookup"><span data-stu-id="a8db1-122">Arithmetic bit shift (`<<`, `>>`)</span></span>  
  
### <a name="comparison-operators"></a><span data-ttu-id="a8db1-123">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="a8db1-123">Comparison Operators</span></span>  
 <span data-ttu-id="a8db1-124">Wszystkie operatory porównania (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`... `Is`)</span><span class="sxs-lookup"><span data-stu-id="a8db1-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>  
  
### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="a8db1-125">Operatory logiczne i bitowe</span><span class="sxs-lookup"><span data-stu-id="a8db1-125">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="a8db1-126">Negacja (`Not`)</span><span class="sxs-lookup"><span data-stu-id="a8db1-126">Negation (`Not`)</span></span>  
  
 <span data-ttu-id="a8db1-127">Razem (`And`, `AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="a8db1-127">Conjunction (`And`, `AndAlso`)</span></span>  
  
 <span data-ttu-id="a8db1-128">Wraz z wartościami granicznymi rozłączenia (`Or`, `OrElse`)</span><span class="sxs-lookup"><span data-stu-id="a8db1-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>  
  
 <span data-ttu-id="a8db1-129">Wyłączny rozłączenia (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="a8db1-129">Exclusive disjunction (`Xor`)</span></span>  
  
### <a name="comments"></a><span data-ttu-id="a8db1-130">Komentarze</span><span class="sxs-lookup"><span data-stu-id="a8db1-130">Comments</span></span>  
 <span data-ttu-id="a8db1-131">`=` Operator jest tylko operator porównania, nie operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="a8db1-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="a8db1-132">Operator łączenia ciągu (`&`) nie jest operator arytmetyczny, ale w pierwszeństwo jest zgrupowana za pomocą operatorów arytmetycznych.</span><span class="sxs-lookup"><span data-stu-id="a8db1-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>  
  
 <span data-ttu-id="a8db1-133">`Is` i `IsNot` operatory są operatory porównania odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="a8db1-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="a8db1-134">Porównuje wartości dwa obiekty; Sprawdź one tylko do określenia, czy dwie zmienne obiektu odwoływać się do tego samego wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="a8db1-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>  
  
## <a name="associativity"></a><span data-ttu-id="a8db1-135">Łączność</span><span class="sxs-lookup"><span data-stu-id="a8db1-135">Associativity</span></span>  
 <span data-ttu-id="a8db1-136">Gdy operatory równy priorytet występować razem w wyrażeniu, na przykład mnożenia i dzielenia, kompilator oblicza każdej operacji zgodnie z jego napotka od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="a8db1-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="a8db1-137">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="a8db1-137">The following example illustrates this.</span></span>  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 <span data-ttu-id="a8db1-138">Pierwsze wyrażenie daje w wyniku dzielenia 96 / 8 (co powoduje 12), a następnie dzielenia 12 / 4, co prowadzi do trzech.</span><span class="sxs-lookup"><span data-stu-id="a8db1-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="a8db1-139">Ponieważ kompilator daje w wyniku operacji `n1` od lewej do prawej, oceny jest taki sam jawnie określić kolejności `n2`.</span><span class="sxs-lookup"><span data-stu-id="a8db1-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="a8db1-140">Zarówno `n1` i `n2` dawać wynik trzech.</span><span class="sxs-lookup"><span data-stu-id="a8db1-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="a8db1-141">Z kolei `n3` ma wynik 48, ponieważ nawiasy wymusić kompilator, aby ocenić 8 / 4 pierwszy.</span><span class="sxs-lookup"><span data-stu-id="a8db1-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>  
  
 <span data-ttu-id="a8db1-142">Ze względu na to zachowanie operatory są określane jako *pozostałych asocjacyjnej* w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a8db1-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>  
  
## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="a8db1-143">Zastępowanie priorytet i łączność</span><span class="sxs-lookup"><span data-stu-id="a8db1-143">Overriding Precedence and Associativity</span></span>  
 <span data-ttu-id="a8db1-144">Aby wymusić niektórych części wyrażenia ma zostać obliczone przed pozostałymi można Użyj nawiasów.</span><span class="sxs-lookup"><span data-stu-id="a8db1-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="a8db1-145">To zastąpienie jednocześnie kolejność pierwszeństwa, jak i kojarzenie po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="a8db1-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="a8db1-146">Visual Basic zawsze wykonuje operacje, które są ujęte w nawiasy przed elementami poza.</span><span class="sxs-lookup"><span data-stu-id="a8db1-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="a8db1-147">Jednak w obrębie nawiasów przechowuje zwykłej priorytet i łączność, chyba że Użyj nawiasów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="a8db1-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="a8db1-148">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="a8db1-148">The following example illustrates this.</span></span>  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8db1-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8db1-149">See Also</span></span>  
 [<span data-ttu-id="a8db1-150">=, operator</span><span class="sxs-lookup"><span data-stu-id="a8db1-150">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [<span data-ttu-id="a8db1-151">Is, operator</span><span class="sxs-lookup"><span data-stu-id="a8db1-151">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="a8db1-152">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="a8db1-152">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="a8db1-153">Like, operator</span><span class="sxs-lookup"><span data-stu-id="a8db1-153">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="a8db1-154">TypeOf, operator</span><span class="sxs-lookup"><span data-stu-id="a8db1-154">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="a8db1-155">Await, operator</span><span class="sxs-lookup"><span data-stu-id="a8db1-155">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="a8db1-156">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="a8db1-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="a8db1-157">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="a8db1-157">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
