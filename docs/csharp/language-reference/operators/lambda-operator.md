---
title: = > — odwołanie C# do operatora
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 3b3a5c2e96e92271da66cbd8f1039a9ec97544fa
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971229"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2b7dd-102">= > — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="2b7dd-102">=> operator (C# reference)</span></span>

<span data-ttu-id="2b7dd-103">`=>` Token jest obsługiwany w dwóch formach: jako operator lambda oraz jako separator nazwy elementu członkowskiego i implementacji elementu członkowskiego w definicji treści wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2b7dd-103">The `=>` token is supported in two forms: as the lambda operator and as a separator of a member name and the member implementation in an expression body definition.</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="2b7dd-104">Operator lambda</span><span class="sxs-lookup"><span data-stu-id="2b7dd-104">Lambda operator</span></span>

<span data-ttu-id="2b7dd-105">W [wyrażeniach lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)operator `=>` lambda oddziela zmienne wejściowe po lewej stronie od treści lambda po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="2b7dd-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input variables on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="2b7dd-106">W poniższym przykładzie użyto funkcji [LINQ](../../programming-guide/concepts/linq/index.md) z składnią metody, aby pokazać użycie wyrażeń lambda:</span><span class="sxs-lookup"><span data-stu-id="2b7dd-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="2b7dd-107">Zmienne wejściowe wyrażeń lambda są silnie wpisywane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2b7dd-107">Input variables of lambda expressions are strongly typed at compile time.</span></span> <span data-ttu-id="2b7dd-108">Gdy kompilator może wywnioskować typy zmiennych wejściowych, jak w poprzednim przykładzie, można pominąć deklaracje typu.</span><span class="sxs-lookup"><span data-stu-id="2b7dd-108">When the compiler can infer the types of input variables, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="2b7dd-109">Jeśli musisz określić typ zmiennych wejściowych, należy to zrobić dla każdej zmiennej, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2b7dd-109">If you need to specify the type of input variables, you must do that for each variable, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="2b7dd-110">Poniższy przykład pokazuje, jak zdefiniować wyrażenie lambda bez zmiennych wejściowych:</span><span class="sxs-lookup"><span data-stu-id="2b7dd-110">The following example shows how to define a lambda expression without input variables:</span></span>

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="2b7dd-111">Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2b7dd-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="2b7dd-112">Definicja treści wyrażenia</span><span class="sxs-lookup"><span data-stu-id="2b7dd-112">Expression body definition</span></span>

<span data-ttu-id="2b7dd-113">Definicja treści wyrażenia ma następującą składnię ogólną:</span><span class="sxs-lookup"><span data-stu-id="2b7dd-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="2b7dd-114">gdzie `expression` jest prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="2b7dd-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="2b7dd-115">Zwracany typ elementu `expression` musi być niejawnie konwertowany na typ zwracany elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="2b7dd-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="2b7dd-116">Jeśli typem zwracanym elementu członkowskiego `void` jest lub, jeśli element członkowski jest konstruktorem, finalizatorem lub akcesorem `set` właściwości, `expression` musi być [*wyrażeniem instrukcji*](~/_csharplang/spec/statements.md#expression-statements); może to być dowolny typ.</span><span class="sxs-lookup"><span data-stu-id="2b7dd-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements); it can be of any type then.</span></span>

<span data-ttu-id="2b7dd-117">W poniższym przykładzie przedstawiono definicję treści wyrażenia dla `Person.ToString` metody:</span><span class="sxs-lookup"><span data-stu-id="2b7dd-117">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="2b7dd-118">Jest to skrócona wersja następującej definicji metody:</span><span class="sxs-lookup"><span data-stu-id="2b7dd-118">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="2b7dd-119">Definicje treści wyrażenia dla metod i właściwości tylko do odczytu są obsługiwane począwszy od C# 6.</span><span class="sxs-lookup"><span data-stu-id="2b7dd-119">Expression body definitions for methods and read-only properties are supported starting with C# 6.</span></span> <span data-ttu-id="2b7dd-120">Definicje treści wyrażenia dla konstruktorów, finalizatorów, metod dostępu do właściwości i indeksatorów są obsługiwane począwszy C# od 7,0.</span><span class="sxs-lookup"><span data-stu-id="2b7dd-120">Expression body definitions for constructors, finalizers, property accessors, and indexers are supported starting with C# 7.0.</span></span>

<span data-ttu-id="2b7dd-121">Aby uzyskać więcej informacji, zobacz [elementy członkowskie z wyrażeniami](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="2b7dd-121">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="2b7dd-122">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="2b7dd-122">Operator overloadability</span></span>

<span data-ttu-id="2b7dd-123">Operator `=>` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="2b7dd-123">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2b7dd-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2b7dd-124">C# language specification</span></span>

<span data-ttu-id="2b7dd-125">Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia funkcji anonimowej](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="2b7dd-125">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b7dd-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b7dd-126">See also</span></span>

- [<span data-ttu-id="2b7dd-127">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="2b7dd-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2b7dd-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="2b7dd-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="2b7dd-129">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="2b7dd-129">Lambda expressions</span></span>](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="2b7dd-130">Elementy członkowskie z wyrażeniem w treści</span><span class="sxs-lookup"><span data-stu-id="2b7dd-130">Expression-bodied members</span></span>](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)
