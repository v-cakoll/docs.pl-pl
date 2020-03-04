---
title: = > — odwołanie C# do operatora
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 5df1ae60ddc298f75d70db7769ec1bf1d21b8ef2
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239290"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="05b05-102">= > — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="05b05-102">=> operator (C# reference)</span></span>

<span data-ttu-id="05b05-103">Token `=>` jest obsługiwany w dwóch formach: jako [operator lambda](#lambda-operator) oraz jako separator nazwy elementu członkowskiego i implementacji elementu członkowskiego w [definicji treści wyrażenia](#expression-body-definition).</span><span class="sxs-lookup"><span data-stu-id="05b05-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="05b05-104">Operator lambda</span><span class="sxs-lookup"><span data-stu-id="05b05-104">Lambda operator</span></span>

<span data-ttu-id="05b05-105">W [wyrażeniach lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)operator lambda `=>` oddziela parametry wejściowe po lewej stronie od treści lambda po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="05b05-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="05b05-106">W poniższym przykładzie użyto funkcji [LINQ](../../programming-guide/concepts/linq/index.md) z składnią metody, aby pokazać użycie wyrażeń lambda:</span><span class="sxs-lookup"><span data-stu-id="05b05-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="05b05-107">Parametry wejściowe wyrażenia lambda są silnie wpisywane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="05b05-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="05b05-108">Gdy kompilator może wywnioskować typy parametrów wejściowych, jak w poprzednim przykładzie, można pominąć deklaracje typu.</span><span class="sxs-lookup"><span data-stu-id="05b05-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="05b05-109">Jeśli musisz określić typ parametrów wejściowych, należy to zrobić dla każdego parametru, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="05b05-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="05b05-110">Poniższy przykład pokazuje, jak zdefiniować wyrażenie lambda bez parametrów wejściowych:</span><span class="sxs-lookup"><span data-stu-id="05b05-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="05b05-111">Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="05b05-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="05b05-112">Definicja treści wyrażenia</span><span class="sxs-lookup"><span data-stu-id="05b05-112">Expression body definition</span></span>

<span data-ttu-id="05b05-113">Definicja treści wyrażenia ma następującą składnię ogólną:</span><span class="sxs-lookup"><span data-stu-id="05b05-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="05b05-114">gdzie `expression` jest prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="05b05-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="05b05-115">Zwracany typ `expression` musi być niejawnie konwertowany na typ zwracany elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="05b05-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="05b05-116">Jeśli typem zwracanym elementu członkowskiego jest `void` lub jeśli element członkowski jest konstruktorem, finalizatorem lub właściwością dostępu `set`, `expression` musi być [*wyrażeniem instrukcji*](~/_csharplang/spec/statements.md#expression-statements), które może być dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="05b05-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements), which can be of any type.</span></span>

<span data-ttu-id="05b05-117">W poniższym przykładzie przedstawiono definicję treści wyrażenia dla metody `Person.ToString`:</span><span class="sxs-lookup"><span data-stu-id="05b05-117">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="05b05-118">Jest to skrócona wersja następującej definicji metody:</span><span class="sxs-lookup"><span data-stu-id="05b05-118">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="05b05-119">Definicje treści wyrażenia dla metod, operatorów i właściwości tylko do odczytu są obsługiwane począwszy od C# 6.</span><span class="sxs-lookup"><span data-stu-id="05b05-119">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="05b05-120">Definicje treści wyrażenia dla konstruktorów, finalizatorów i metod dostępu właściwości i indeksatora są obsługiwane począwszy od C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="05b05-120">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="05b05-121">Aby uzyskać więcej informacji, zobacz [elementy członkowskie z wyrażeniami](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="05b05-121">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="05b05-122">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="05b05-122">Operator overloadability</span></span>

<span data-ttu-id="05b05-123">Operator `=>` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="05b05-123">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="05b05-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="05b05-124">C# language specification</span></span>

<span data-ttu-id="05b05-125">Aby uzyskać więcej informacji na temat operatora lambda, zobacz sekcję [wyrażenia funkcji anonimowej](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="05b05-125">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="05b05-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05b05-126">See also</span></span>

- [<span data-ttu-id="05b05-127">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="05b05-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="05b05-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="05b05-128">C# operators</span></span>](index.md)
