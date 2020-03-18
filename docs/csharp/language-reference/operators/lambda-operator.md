---
title: = operator> - odwołanie do języka C#
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 15c02e11610866f359e3e3a7e2751ded918154b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846259"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1840c-102">= operator> (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="1840c-102">=> operator (C# reference)</span></span>

<span data-ttu-id="1840c-103">Token `=>` jest obsługiwany w dwóch formach: jako [operator lambda](#lambda-operator) i jako separator nazwy elementu członkowskiego i implementacji elementu członkowskiego w [definicji treści wyrażenia](#expression-body-definition).</span><span class="sxs-lookup"><span data-stu-id="1840c-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="1840c-104">Operator Lambda</span><span class="sxs-lookup"><span data-stu-id="1840c-104">Lambda operator</span></span>

<span data-ttu-id="1840c-105">W [wyrażeniach lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)operator `=>` lambda oddziela parametry wejściowe po lewej stronie od obiektu lambda po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="1840c-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="1840c-106">W poniższym przykładzie użyto funkcji [LINQ](../../programming-guide/concepts/linq/index.md) ze składnią metody w celu zademonstrowania użycia wyrażeń lambda:</span><span class="sxs-lookup"><span data-stu-id="1840c-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](snippets/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="1840c-107">Parametry wejściowe wyrażenia lambda są silnie typowane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1840c-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="1840c-108">Gdy kompilator można wywnioskować typy parametrów wejściowych, jak w poprzednim przykładzie, można pominąć deklaracje typu.</span><span class="sxs-lookup"><span data-stu-id="1840c-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="1840c-109">Jeśli trzeba określić typ parametrów wejściowych, należy to zrobić dla każdego parametru, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1840c-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](snippets/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="1840c-110">W poniższym przykładzie pokazano, jak zdefiniować wyrażenie lambda bez parametrów wejściowych:</span><span class="sxs-lookup"><span data-stu-id="1840c-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](snippets/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="1840c-111">Aby uzyskać więcej informacji, zobacz [Wyrażenia Lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1840c-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="1840c-112">Definicja treści wyrażeń</span><span class="sxs-lookup"><span data-stu-id="1840c-112">Expression body definition</span></span>

<span data-ttu-id="1840c-113">Definicja treści wyrażenia ma następującą ogólną składnię:</span><span class="sxs-lookup"><span data-stu-id="1840c-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="1840c-114">gdzie `expression` jest prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1840c-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="1840c-115">Typ zwracany `expression` musi być niejawnie konwertowalny do typu zwracanego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1840c-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="1840c-116">Jeśli typ zwracany elementu `void` członkowskiego jest lub jeśli element członkowski `set` jest konstruktorem, finalizatorem lub akcesorem właściwości, `expression` musi być [*wyrażeniem instrukcji*](~/_csharplang/spec/statements.md#expression-statements), które może być dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="1840c-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements), which can be of any type.</span></span>

<span data-ttu-id="1840c-117">W poniższym przykładzie przedstawiono definicję treści wyrażeń `Person.ToString` dla metody:</span><span class="sxs-lookup"><span data-stu-id="1840c-117">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="1840c-118">Jest to skrócona wersja następującej definicji metody:</span><span class="sxs-lookup"><span data-stu-id="1840c-118">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="1840c-119">Definicje treści wyrażeń dla metod, operatorów i właściwości tylko do odczytu są obsługiwane począwszy od języka C# 6.</span><span class="sxs-lookup"><span data-stu-id="1840c-119">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="1840c-120">Definicje treści wyrażeń dla konstruktorów, finalizatorów oraz akcesorów właściwości i indeksatora są obsługiwane począwszy od języka C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="1840c-120">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="1840c-121">Aby uzyskać więcej informacji, zobacz [Elementy członkowskie zabudowane wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="1840c-121">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="1840c-122">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="1840c-122">Operator overloadability</span></span>

<span data-ttu-id="1840c-123">Operator `=>` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="1840c-123">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1840c-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1840c-124">C# language specification</span></span>

<span data-ttu-id="1840c-125">Aby uzyskać więcej informacji na temat operatora lambda, zobacz [anonimowe wyrażenia funkcji](~/_csharplang/spec/expressions.md#anonymous-function-expressions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="1840c-125">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1840c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1840c-126">See also</span></span>

- [<span data-ttu-id="1840c-127">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1840c-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1840c-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="1840c-128">C# operators</span></span>](index.md)
