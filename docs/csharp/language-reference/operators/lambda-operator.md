---
title: =&gt; Operator - C# odwołania
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: fa2e149f5b19e80e3171d08519be3ae249d2a112
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540809"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="356d6-102">=&gt; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="356d6-102">=&gt; operator (C# Reference)</span></span>

<span data-ttu-id="356d6-103">`=>` Tokenu jest obsługiwana w dwóch formach: jako operatora lambda i separator nazwę elementu członkowskiego i implementacji elementu członkowskiego w definicji treści wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="356d6-103">The `=>` token is supported in two forms: as the lambda operator and as a separator of a member name and the member implementation in an expression body definition.</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="356d6-104">Lambda operator</span><span class="sxs-lookup"><span data-stu-id="356d6-104">Lambda operator</span></span>

<span data-ttu-id="356d6-105">W [wyrażeń lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md), operatora lambda `=>` zmienne wejściowe po lewej stronie są oddzielone od treści lambda po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="356d6-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input variables on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="356d6-106">W poniższym przykładzie użyto [LINQ](../../programming-guide/concepts/linq/index.md) funkcję za pomocą składni metody, aby zademonstrować użycie wyrażenia lambda:</span><span class="sxs-lookup"><span data-stu-id="356d6-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#InferredTypes)]

<span data-ttu-id="356d6-107">Zmienne wejściowe wyrażeń lambda są silnie typizowane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="356d6-107">Input variables of lambda expressions are strongly typed at compile time.</span></span> <span data-ttu-id="356d6-108">Gdy kompilator może wywnioskować rodzaje zmiennych wejściowych, podobnie jak w poprzednim przykładzie, możesz pominąć deklaracje typu.</span><span class="sxs-lookup"><span data-stu-id="356d6-108">When the compiler can infer the types of input variables, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="356d6-109">Jeśli musisz określić typ zmiennych wejściowych, należy użyć dla każdej zmiennej, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="356d6-109">If you need to specify the type of input variables, you must do that for each variable, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#ExplicitTypes)]

<span data-ttu-id="356d6-110">Poniższy przykład pokazuje jak zdefiniować wyrażenia lambda bez zmienne wejściowe:</span><span class="sxs-lookup"><span data-stu-id="356d6-110">The following example shows how to define a lambda expression without input variables:</span></span>

[!code-csharp-interactive[without input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#WithoutInput)]

<span data-ttu-id="356d6-111">Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="356d6-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="356d6-112">Definicja treści wyrażenia</span><span class="sxs-lookup"><span data-stu-id="356d6-112">Expression body definition</span></span>

<span data-ttu-id="356d6-113">Definicja treści wyrażenia ma następującą składnię ogólne:</span><span class="sxs-lookup"><span data-stu-id="356d6-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="356d6-114">gdzie *wyrażenie* jest prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="356d6-114">where *expression* is a valid expression.</span></span> <span data-ttu-id="356d6-115">Należy pamiętać, że *wyrażenie* może być *wyrażenie instrukcji* tylko jeśli element członkowski zwracany typ jest `void`, lub, jeśli element jest konstruktorem, finalizator lub właściwość `set` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="356d6-115">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor, a finalizer, or a property `set` accessor.</span></span>

<span data-ttu-id="356d6-116">W poniższym przykładzie pokazano definicję treści wyrażenia dla `Person.ToString` metody:</span><span class="sxs-lookup"><span data-stu-id="356d6-116">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="356d6-117">Jest wersją skróconą następującą definicję metody:</span><span class="sxs-lookup"><span data-stu-id="356d6-117">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="356d6-118">Definicje treści wyrażenia dla metod i właściwości tylko do odczytu są obsługiwane, począwszy od C# 6.</span><span class="sxs-lookup"><span data-stu-id="356d6-118">Expression body definitions for methods and read-only properties are supported starting with C# 6.</span></span> <span data-ttu-id="356d6-119">Definicje treści wyrażenia dla konstruktorów, finalizatorów, metod dostępu do właściwości i indeksatorów są obsługiwane, począwszy od C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="356d6-119">Expression body definitions for constructors, finalizers, property accessors, and indexers are supported starting with C# 7.0.</span></span>

<span data-ttu-id="356d6-120">Aby uzyskać więcej informacji, zobacz [elementy członkowskie z wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="356d6-120">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="356d6-121">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="356d6-121">Operator overloadability</span></span>

<span data-ttu-id="356d6-122">Operator `=>` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="356d6-122">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="356d6-123">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="356d6-123">C# language specification</span></span>

<span data-ttu-id="356d6-124">Aby uzyskać więcej informacji, zobacz [wyrażenia funkcji anonimowych](~/_csharplang/spec/expressions.md#anonymous-function-expressions) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="356d6-124">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="356d6-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="356d6-125">See also</span></span>

- [<span data-ttu-id="356d6-126">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="356d6-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="356d6-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="356d6-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="356d6-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="356d6-128">C# Operators</span></span>](index.md)
- [<span data-ttu-id="356d6-129">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="356d6-129">Lambda expressions</span></span>](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="356d6-130">Elementy członkowskie z wyrażeniem w treści</span><span class="sxs-lookup"><span data-stu-id="356d6-130">Expression-bodied members</span></span>](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)