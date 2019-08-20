---
title: Operatory — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 4870c744383205c2b7e3832c01fb838a545f085f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588610"
---
# <a name="operators-c-programming-guide"></a><span data-ttu-id="6011e-102">Operatory (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="6011e-102">Operators (C# Programming Guide)</span></span>

<span data-ttu-id="6011e-103">W C#programie *operator* jest elementem programu, który jest stosowany do co najmniej jednego *operandu* w wyrażeniu lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6011e-103">In C#, an *operator* is a program element that is applied to one or more *operands* in an expression or statement.</span></span> <span data-ttu-id="6011e-104">Operatory przyjmujące jeden operand, takie jak operator przyrostu (`++`) lub `new`, są określane jako operatory jednoargumentowe.</span><span class="sxs-lookup"><span data-stu-id="6011e-104">Operators that take one operand, such as the increment operator (`++`) or `new`, are referred to as *unary* operators.</span></span> <span data-ttu-id="6011e-105">Operatory, które przyjmują dwa operandy, takie jak operatory`+`arytmetyczne`*`(`/`,`-`,,), są określane jako operatory *binarne* .</span><span class="sxs-lookup"><span data-stu-id="6011e-105">Operators that take two operands, such as arithmetic operators (`+`,`-`,`*`,`/`), are referred to as *binary* operators.</span></span> <span data-ttu-id="6011e-106">Jeden operator, operator warunkowy (`?:`), przyjmuje trzy operandy i jest jedynym operatorem trójskładnikowych w C#.</span><span class="sxs-lookup"><span data-stu-id="6011e-106">One operator, the conditional operator (`?:`), takes three operands and is the sole ternary operator in C#.</span></span>  
  
 <span data-ttu-id="6011e-107">Poniższa instrukcja języka C# zawiera jeden operator jednoargumentowy i jeden argument operacji.</span><span class="sxs-lookup"><span data-stu-id="6011e-107">The following C# statement contains a single unary operator and a single operand.</span></span> <span data-ttu-id="6011e-108">Operator `++`przyrostu, modyfikuje wartość operandu `y`.</span><span class="sxs-lookup"><span data-stu-id="6011e-108">The increment operator, `++`, modifies the value of the operand `y`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 <span data-ttu-id="6011e-109">Następująca instrukcja języka C# zawiera dwa operatory dwuargumentowe, z których każdy przyjmuje dwa argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="6011e-109">The following C# statement contains two binary operators, each with two operands.</span></span> <span data-ttu-id="6011e-110">Operator `=`przypisania,, ma zmienną `y` integer i wyrażenie `2 + 3` jako operandy.</span><span class="sxs-lookup"><span data-stu-id="6011e-110">The assignment operator, `=`, has the integer variable `y` and the expression `2 + 3` as operands.</span></span> <span data-ttu-id="6011e-111">Wyrażenie `2 + 3` składa się z operatora dodawania i dwóch operandów, `2` i `3`.</span><span class="sxs-lookup"><span data-stu-id="6011e-111">The expression `2 + 3` itself consists of the addition operator and two operands, `2` and `3`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
<span data-ttu-id="6011e-112">Argument operacji może być prawidłowym wyrażeniem zawierającym kod o dowolnej długości i może składać się z dowolnej liczby podwyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6011e-112">An operand can be a valid expression that is composed of any length of code, and it can comprise any number of sub expressions.</span></span> <span data-ttu-id="6011e-113">W wyrażeniu zawierającym wiele operatorów kolejność, w której są stosowane operatory jest określana według *pierwszeństwa*operatorów, *łączność*i nawiasów.</span><span class="sxs-lookup"><span data-stu-id="6011e-113">In an expression that contains multiple operators, the order in which the operators are applied is determined by *operator precedence*, *associativity*, and parentheses.</span></span>  

## <a name="operator-precedence"></a><span data-ttu-id="6011e-114">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="6011e-114">Operator precedence</span></span>
  
<span data-ttu-id="6011e-115">Każdy operator ma zdefiniowane pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="6011e-115">Each operator has a defined precedence.</span></span> <span data-ttu-id="6011e-116">W wyrażeniu zawierającym wiele operatorów, które mają różne poziomy pierwszeństwa, pierwszeństwo operatorów określa kolejność wykonywania obliczeń tych operatorów.</span><span class="sxs-lookup"><span data-stu-id="6011e-116">In an expression that contains multiple operators that have different precedence levels, the precedence of the operators determines the order in which the operators are evaluated.</span></span> <span data-ttu-id="6011e-117">Na przykład następująca instrukcja przypisuje 3 do `n1`:</span><span class="sxs-lookup"><span data-stu-id="6011e-117">For example, the following statement assigns 3 to `n1`:</span></span>

```csharp
n1 = 11 - 2 * 4;
```

<span data-ttu-id="6011e-118">Mnożenie jest wykonywane jako pierwsze, ponieważ mnożenie ma pierwszeństwo przed odejmowaniem.</span><span class="sxs-lookup"><span data-stu-id="6011e-118">The multiplication is executed first because multiplication takes precedence over subtraction.</span></span>

<span data-ttu-id="6011e-119">Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz [ C# operatory](../../language-reference/operators/index.md).</span><span class="sxs-lookup"><span data-stu-id="6011e-119">For the complete list of C# operators ordered by precedence level, see [C# operators](../../language-reference/operators/index.md).</span></span>
  
## <a name="associativity"></a><span data-ttu-id="6011e-120">Łączność</span><span class="sxs-lookup"><span data-stu-id="6011e-120">Associativity</span></span>

 <span data-ttu-id="6011e-121">Gdy co najmniej dwa operatory w wyrażeniu mają takie samo pierwszeństwo, są obliczane na podstawie łączności.</span><span class="sxs-lookup"><span data-stu-id="6011e-121">When two or more operators that have the same precedence are present in an expression, they are evaluated based on associativity.</span></span> <span data-ttu-id="6011e-122">Operatory mające łączność do lewej strony są obliczane w kolejności od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="6011e-122">Left-associative operators are evaluated in order from left to right.</span></span> <span data-ttu-id="6011e-123">Na przykład, `x * y / z` jest oceniane jako `(x * y) / z`.</span><span class="sxs-lookup"><span data-stu-id="6011e-123">For example, `x * y / z` is evaluated as `(x * y) / z`.</span></span> <span data-ttu-id="6011e-124">Operatory mające łączność do prawej strony są obliczane w kolejności od prawej do lewej.</span><span class="sxs-lookup"><span data-stu-id="6011e-124">Right-associative operators are evaluated in order from right to left.</span></span> <span data-ttu-id="6011e-125">Na przykład operator przypisania ma łączność do prawej strony.</span><span class="sxs-lookup"><span data-stu-id="6011e-125">For example, the assignment operator is right associative.</span></span> <span data-ttu-id="6011e-126">Gdyby tak nie było, poniższy kod powodowałby wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="6011e-126">If it were not, the following code would result in an error.</span></span>  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 <span data-ttu-id="6011e-127">Innym przykładem jest skojarzenie operatora Trzyelementowy ([?:](../../language-reference/operators/conditional-operator.md)) z prawej strony.</span><span class="sxs-lookup"><span data-stu-id="6011e-127">As another example the ternary operator ([?:](../../language-reference/operators/conditional-operator.md)) is right associative.</span></span> <span data-ttu-id="6011e-128">Większość operatorów binarnych jest polewana.</span><span class="sxs-lookup"><span data-stu-id="6011e-128">Most binary operators are left associative.</span></span>  
  
 <span data-ttu-id="6011e-129">Niezależnie od tego, czy operatory w wyrażeniu mają łączność do lewej strony, czy do prawej, argumenty operacji każdego wyrażenia są obliczane najpierw od lewej strony do prawej.</span><span class="sxs-lookup"><span data-stu-id="6011e-129">Whether the operators in an expression are left associative or right associative, the operands of each expression are evaluated first, from left to right.</span></span> <span data-ttu-id="6011e-130">W poniższych przykładach pokazano kolejność obliczania operatorów i argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="6011e-130">The following examples illustrate the order of evaluation of operators and operands.</span></span>  
  
|<span data-ttu-id="6011e-131">Instrukcja</span><span class="sxs-lookup"><span data-stu-id="6011e-131">Statement</span></span>|<span data-ttu-id="6011e-132">Kolejność obliczeń</span><span class="sxs-lookup"><span data-stu-id="6011e-132">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = b`|<span data-ttu-id="6011e-133">a, b, =</span><span class="sxs-lookup"><span data-stu-id="6011e-133">a, b, =</span></span>|  
|`a = b + c`|<span data-ttu-id="6011e-134">a, b, c, +, =</span><span class="sxs-lookup"><span data-stu-id="6011e-134">a, b, c, +, =</span></span>|  
|`a = b + c * d`|<span data-ttu-id="6011e-135">a, b, c, d, \*, +, =</span><span class="sxs-lookup"><span data-stu-id="6011e-135">a, b, c, d, \*, +, =</span></span>|  
|`a = b * c + d`|<span data-ttu-id="6011e-136">a, b, c, \*, d, +, =</span><span class="sxs-lookup"><span data-stu-id="6011e-136">a, b, c, \*, d, +, =</span></span>|  
|`a = b - c + d`|<span data-ttu-id="6011e-137">a, b, c, -, d, +, =</span><span class="sxs-lookup"><span data-stu-id="6011e-137">a, b, c, -, d, +, =</span></span>|  
|`a += b -= c`|<span data-ttu-id="6011e-138">a, b, c, -=, +=</span><span class="sxs-lookup"><span data-stu-id="6011e-138">a, b, c, -=, +=</span></span>|  
  
## <a name="adding-parentheses"></a><span data-ttu-id="6011e-139">Dodawanie nawiasów</span><span class="sxs-lookup"><span data-stu-id="6011e-139">Adding parentheses</span></span>

 <span data-ttu-id="6011e-140">Używając nawiasów, można zmienić kolejność określoną przez pierwszeństwo operatorów oraz łączność.</span><span class="sxs-lookup"><span data-stu-id="6011e-140">You can change the order imposed by operator precedence and associativity by using parentheses.</span></span> <span data-ttu-id="6011e-141">Na przykład `2 + 3 * 2` zwykle jest to 8, ponieważ operatory mnożenia mają pierwszeństwo przed operatorami dodatków.</span><span class="sxs-lookup"><span data-stu-id="6011e-141">For example, `2 + 3 * 2` ordinarily evaluates to 8, because multiplicative operators take precedence over additive operators.</span></span> <span data-ttu-id="6011e-142">Jeśli jednak wyrażenie zostanie zapisane jako `(2 + 3) * 2`, dodanie jest oceniane przed mnożeniem, a wynikiem będzie 10.</span><span class="sxs-lookup"><span data-stu-id="6011e-142">However, if you write the expression as `(2 + 3) * 2`, the addition is evaluated before the multiplication, and the result is 10.</span></span> <span data-ttu-id="6011e-143">W poniższych przykładach pokazano kolejność obliczania w wyrażeniach z nawiasami.</span><span class="sxs-lookup"><span data-stu-id="6011e-143">The following examples illustrate the order of evaluation in parenthesized expressions.</span></span> <span data-ttu-id="6011e-144">Tak jak w poprzednich przykładach argumenty operacji są obliczane przed zastosowaniem operatora.</span><span class="sxs-lookup"><span data-stu-id="6011e-144">As in previous examples, the operands are evaluated before the operator is applied.</span></span>  
  
|<span data-ttu-id="6011e-145">Instrukcja</span><span class="sxs-lookup"><span data-stu-id="6011e-145">Statement</span></span>|<span data-ttu-id="6011e-146">Kolejność obliczeń</span><span class="sxs-lookup"><span data-stu-id="6011e-146">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = (b + c) * d`|<span data-ttu-id="6011e-147">a, b, c, +, d, \*, =</span><span class="sxs-lookup"><span data-stu-id="6011e-147">a, b, c, +, d, \*, =</span></span>|  
|`a = b - (c + d)`|<span data-ttu-id="6011e-148">a, b, c, d, +, -, =</span><span class="sxs-lookup"><span data-stu-id="6011e-148">a, b, c, d, +, -, =</span></span>|  
|`a = (b + c) * (d - e)`|<span data-ttu-id="6011e-149">a, b, c, +, d, e, -, \*, =</span><span class="sxs-lookup"><span data-stu-id="6011e-149">a, b, c, +, d, e, -, \*, =</span></span>|  
  
## <a name="operator-overloading"></a><span data-ttu-id="6011e-150">Przeładowanie operatora</span><span class="sxs-lookup"><span data-stu-id="6011e-150">Operator overloading</span></span>

<span data-ttu-id="6011e-151">Można zdefiniować zachowanie niektórych operatorów dla niestandardowych klas i struktur.</span><span class="sxs-lookup"><span data-stu-id="6011e-151">You can define the behavior of certain operators for custom classes and structs.</span></span> <span data-ttu-id="6011e-152">Ten proces jest określany mianem *przeciążenia operatora*.</span><span class="sxs-lookup"><span data-stu-id="6011e-152">This process is referred to as *operator overloading*.</span></span> <span data-ttu-id="6011e-153">Aby uzyskać więcej informacji, zobacz przeciążanie [operatora](../../language-reference/operators/operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="6011e-153">For more information, see [Operator overloading](../../language-reference/operators/operator-overloading.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6011e-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6011e-154">See also</span></span>

- [<span data-ttu-id="6011e-155">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6011e-155">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6011e-156">Instrukcje, wyrażenia i operatory</span><span class="sxs-lookup"><span data-stu-id="6011e-156">Statements, Expressions, and Operators</span></span>](index.md)
- [<span data-ttu-id="6011e-157">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="6011e-157">C# Operators</span></span>](../../language-reference/operators/index.md)
