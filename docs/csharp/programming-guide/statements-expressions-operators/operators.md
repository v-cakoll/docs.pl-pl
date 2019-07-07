---
title: Operatorzy — C# przewodnik programowania
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 551d4cd8bf26a1c1caf3cbf611d9f338ae2581be
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609501"
---
# <a name="operators-c-programming-guide"></a><span data-ttu-id="e9109-102">Operatory (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="e9109-102">Operators (C# Programming Guide)</span></span>

<span data-ttu-id="e9109-103">W języku C# *operator* jest elementem programu, który jest stosowany do co najmniej jednego *operandy* w wyrażeniu lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e9109-103">In C#, an *operator* is a program element that is applied to one or more *operands* in an expression or statement.</span></span> <span data-ttu-id="e9109-104">Operatory przyjmujące jeden argument operacji, takich jak operator inkrementacji (`++`) lub `new`, są określane jako *jednoargumentowe* operatorów.</span><span class="sxs-lookup"><span data-stu-id="e9109-104">Operators that take one operand, such as the increment operator (`++`) or `new`, are referred to as *unary* operators.</span></span> <span data-ttu-id="e9109-105">Operatory przyjmujące dwa argumenty operacji, takie jak operatory arytmetyczne (`+`,`-`,`*`,`/`), są określane jako *binarne* operatorów.</span><span class="sxs-lookup"><span data-stu-id="e9109-105">Operators that take two operands, such as arithmetic operators (`+`,`-`,`*`,`/`), are referred to as *binary* operators.</span></span> <span data-ttu-id="e9109-106">Jeden operator, operator warunkowy (`?:`), przyjmuje trzy argumenty operacji i jest jedynym operatorem trójargumentowym w języku C#.</span><span class="sxs-lookup"><span data-stu-id="e9109-106">One operator, the conditional operator (`?:`), takes three operands and is the sole ternary operator in C#.</span></span>  
  
 <span data-ttu-id="e9109-107">Poniższa instrukcja języka C# zawiera jeden operator jednoargumentowy i jeden argument operacji.</span><span class="sxs-lookup"><span data-stu-id="e9109-107">The following C# statement contains a single unary operator and a single operand.</span></span> <span data-ttu-id="e9109-108">Operator inkrementacji `++`, modyfikuje wartość argumentu operacji `y`.</span><span class="sxs-lookup"><span data-stu-id="e9109-108">The increment operator, `++`, modifies the value of the operand `y`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 <span data-ttu-id="e9109-109">Następująca instrukcja języka C# zawiera dwa operatory dwuargumentowe, z których każdy przyjmuje dwa argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="e9109-109">The following C# statement contains two binary operators, each with two operands.</span></span> <span data-ttu-id="e9109-110">Operator przypisania `=`, ma zmienną całkowitą `y` i wyrażenie `2 + 3` jako argumentów.</span><span class="sxs-lookup"><span data-stu-id="e9109-110">The assignment operator, `=`, has the integer variable `y` and the expression `2 + 3` as operands.</span></span> <span data-ttu-id="e9109-111">Wyrażenie `2 + 3` zawiera dodatkowy operator i dwa operandy `2` i `3`.</span><span class="sxs-lookup"><span data-stu-id="e9109-111">The expression `2 + 3` itself consists of the addition operator and two operands, `2` and `3`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
<span data-ttu-id="e9109-112">Argument operacji może być prawidłowym wyrażeniem zawierającym kod o dowolnej długości i może składać się z dowolnej liczby podwyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e9109-112">An operand can be a valid expression that is composed of any length of code, and it can comprise any number of sub expressions.</span></span> <span data-ttu-id="e9109-113">W wyrażeniu zawierającym wiele operatorów kolejność stosowania operatorów jest ustalana *pierwszeństwo operatorów*, *kojarzenie*i nawiasy.</span><span class="sxs-lookup"><span data-stu-id="e9109-113">In an expression that contains multiple operators, the order in which the operators are applied is determined by *operator precedence*, *associativity*, and parentheses.</span></span>  

## <a name="operator-precedence"></a><span data-ttu-id="e9109-114">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="e9109-114">Operator precedence</span></span>
  
<span data-ttu-id="e9109-115">Każdy operator ma zdefiniowane pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="e9109-115">Each operator has a defined precedence.</span></span> <span data-ttu-id="e9109-116">W wyrażeniu zawierającym wiele operatorów, które mają różne poziomy pierwszeństwa, pierwszeństwo operatorów określa kolejność wykonywania obliczeń tych operatorów.</span><span class="sxs-lookup"><span data-stu-id="e9109-116">In an expression that contains multiple operators that have different precedence levels, the precedence of the operators determines the order in which the operators are evaluated.</span></span> <span data-ttu-id="e9109-117">Na przykład następująca instrukcja przypisuje wartość 3 do `n1`:</span><span class="sxs-lookup"><span data-stu-id="e9109-117">For example, the following statement assigns 3 to `n1`:</span></span>

```csharp
n1 = 11 - 2 * 4;
```

<span data-ttu-id="e9109-118">Mnożenie jest wykonywane jako pierwsze, ponieważ mnożenie ma pierwszeństwo przed odejmowaniem.</span><span class="sxs-lookup"><span data-stu-id="e9109-118">The multiplication is executed first because multiplication takes precedence over subtraction.</span></span>

<span data-ttu-id="e9109-119">Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](../../language-reference/operators/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9109-119">For the complete list of C# operators ordered by precedence level, see [C# operators](../../language-reference/operators/index.md).</span></span>
  
## <a name="associativity"></a><span data-ttu-id="e9109-120">Łączność</span><span class="sxs-lookup"><span data-stu-id="e9109-120">Associativity</span></span>

 <span data-ttu-id="e9109-121">Gdy co najmniej dwa operatory w wyrażeniu mają takie samo pierwszeństwo, są obliczane na podstawie łączności.</span><span class="sxs-lookup"><span data-stu-id="e9109-121">When two or more operators that have the same precedence are present in an expression, they are evaluated based on associativity.</span></span> <span data-ttu-id="e9109-122">Operatory mające łączność do lewej strony są obliczane w kolejności od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="e9109-122">Left-associative operators are evaluated in order from left to right.</span></span> <span data-ttu-id="e9109-123">Na przykład `x * y / z` jest oceniane jako `(x * y) / z`.</span><span class="sxs-lookup"><span data-stu-id="e9109-123">For example, `x * y / z` is evaluated as `(x * y) / z`.</span></span> <span data-ttu-id="e9109-124">Operatory mające łączność do prawej strony są obliczane w kolejności od prawej do lewej.</span><span class="sxs-lookup"><span data-stu-id="e9109-124">Right-associative operators are evaluated in order from right to left.</span></span> <span data-ttu-id="e9109-125">Na przykład operator przypisania ma łączność do prawej strony.</span><span class="sxs-lookup"><span data-stu-id="e9109-125">For example, the assignment operator is right associative.</span></span> <span data-ttu-id="e9109-126">Gdyby tak nie było, poniższy kod powodowałby wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="e9109-126">If it were not, the following code would result in an error.</span></span>  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 <span data-ttu-id="e9109-127">Innym przykładem operator trójargumentowy ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) jest łączność do prawej strony.</span><span class="sxs-lookup"><span data-stu-id="e9109-127">As another example the ternary operator ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) is right associative.</span></span> <span data-ttu-id="e9109-128">Większość operatory dwuargumentowe mają łączność do lewej.</span><span class="sxs-lookup"><span data-stu-id="e9109-128">Most binary operators are left associative.</span></span>  
  
 <span data-ttu-id="e9109-129">Niezależnie od tego, czy operatory w wyrażeniu mają łączność do lewej strony, czy do prawej, argumenty operacji każdego wyrażenia są obliczane najpierw od lewej strony do prawej.</span><span class="sxs-lookup"><span data-stu-id="e9109-129">Whether the operators in an expression are left associative or right associative, the operands of each expression are evaluated first, from left to right.</span></span> <span data-ttu-id="e9109-130">W poniższych przykładach pokazano kolejność obliczania operatorów i argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="e9109-130">The following examples illustrate the order of evaluation of operators and operands.</span></span>  
  
|<span data-ttu-id="e9109-131">Instrukcja</span><span class="sxs-lookup"><span data-stu-id="e9109-131">Statement</span></span>|<span data-ttu-id="e9109-132">Kolejność obliczeń</span><span class="sxs-lookup"><span data-stu-id="e9109-132">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = b`|<span data-ttu-id="e9109-133">a, b, =</span><span class="sxs-lookup"><span data-stu-id="e9109-133">a, b, =</span></span>|  
|`a = b + c`|<span data-ttu-id="e9109-134">a, b, c, +, =</span><span class="sxs-lookup"><span data-stu-id="e9109-134">a, b, c, +, =</span></span>|  
|`a = b + c * d`|<span data-ttu-id="e9109-135">a, b, c, d, \*, +, =</span><span class="sxs-lookup"><span data-stu-id="e9109-135">a, b, c, d, \*, +, =</span></span>|  
|`a = b * c + d`|<span data-ttu-id="e9109-136">a, b, c, \*, d, +, =</span><span class="sxs-lookup"><span data-stu-id="e9109-136">a, b, c, \*, d, +, =</span></span>|  
|`a = b - c + d`|<span data-ttu-id="e9109-137">a, b, c, -, d, +, =</span><span class="sxs-lookup"><span data-stu-id="e9109-137">a, b, c, -, d, +, =</span></span>|  
|`a += b -= c`|<span data-ttu-id="e9109-138">a, b, c, -=, +=</span><span class="sxs-lookup"><span data-stu-id="e9109-138">a, b, c, -=, +=</span></span>|  
  
## <a name="adding-parentheses"></a><span data-ttu-id="e9109-139">Dodawanie nawiasów</span><span class="sxs-lookup"><span data-stu-id="e9109-139">Adding parentheses</span></span>

 <span data-ttu-id="e9109-140">Używając nawiasów, można zmienić kolejność określoną przez pierwszeństwo operatorów oraz łączność.</span><span class="sxs-lookup"><span data-stu-id="e9109-140">You can change the order imposed by operator precedence and associativity by using parentheses.</span></span> <span data-ttu-id="e9109-141">Na przykład `2 + 3 * 2` zazwyczaj daje w wyniku 8, ponieważ operatory mnożne pierwszeństwo przed operatorami addytywnymi.</span><span class="sxs-lookup"><span data-stu-id="e9109-141">For example, `2 + 3 * 2` ordinarily evaluates to 8, because multiplicative operators take precedence over additive operators.</span></span> <span data-ttu-id="e9109-142">Jednak jeśli piszesz wyrażenia jako `(2 + 3) * 2`, dodawanie zostanie wykonane przed mnożeniem, a wynik to 10.</span><span class="sxs-lookup"><span data-stu-id="e9109-142">However, if you write the expression as `(2 + 3) * 2`, the addition is evaluated before the multiplication, and the result is 10.</span></span> <span data-ttu-id="e9109-143">W poniższych przykładach pokazano kolejność obliczania w wyrażeniach z nawiasami.</span><span class="sxs-lookup"><span data-stu-id="e9109-143">The following examples illustrate the order of evaluation in parenthesized expressions.</span></span> <span data-ttu-id="e9109-144">Tak jak w poprzednich przykładach argumenty operacji są obliczane przed zastosowaniem operatora.</span><span class="sxs-lookup"><span data-stu-id="e9109-144">As in previous examples, the operands are evaluated before the operator is applied.</span></span>  
  
|<span data-ttu-id="e9109-145">Instrukcja</span><span class="sxs-lookup"><span data-stu-id="e9109-145">Statement</span></span>|<span data-ttu-id="e9109-146">Kolejność obliczeń</span><span class="sxs-lookup"><span data-stu-id="e9109-146">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = (b + c) * d`|<span data-ttu-id="e9109-147">a, b, c, +, d, \*, =</span><span class="sxs-lookup"><span data-stu-id="e9109-147">a, b, c, +, d, \*, =</span></span>|  
|`a = b - (c + d)`|<span data-ttu-id="e9109-148">a, b, c, d, +, -, =</span><span class="sxs-lookup"><span data-stu-id="e9109-148">a, b, c, d, +, -, =</span></span>|  
|`a = (b + c) * (d - e)`|<span data-ttu-id="e9109-149">a, b, c, +, d, e, -, \*, =</span><span class="sxs-lookup"><span data-stu-id="e9109-149">a, b, c, +, d, e, -, \*, =</span></span>|  
  
## <a name="operator-overloading"></a><span data-ttu-id="e9109-150">Przeładowanie operatora</span><span class="sxs-lookup"><span data-stu-id="e9109-150">Operator overloading</span></span>

<span data-ttu-id="e9109-151">Można zdefiniować zachowanie operatorów dla niestandardowych klas i struktur.</span><span class="sxs-lookup"><span data-stu-id="e9109-151">You can define the behavior of certain operators for custom classes and structs.</span></span> <span data-ttu-id="e9109-152">Ten proces jest nazywany *przeciążenia operatora*.</span><span class="sxs-lookup"><span data-stu-id="e9109-152">This process is referred to as *operator overloading*.</span></span> <span data-ttu-id="e9109-153">Aby uzyskać więcej informacji, zobacz [przeciążania operatora](../../language-reference/operators/operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="e9109-153">For more information, see [Operator overloading](../../language-reference/operators/operator-overloading.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e9109-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9109-154">See also</span></span>

- [<span data-ttu-id="e9109-155">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e9109-155">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e9109-156">Instrukcje, wyrażenia i operatory</span><span class="sxs-lookup"><span data-stu-id="e9109-156">Statements, Expressions, and Operators</span></span>](index.md)
- [<span data-ttu-id="e9109-157">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="e9109-157">C# Operators</span></span>](../../language-reference/operators/index.md)
