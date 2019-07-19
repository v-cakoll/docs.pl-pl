---
title: Delegowanie operatora C# — odwołanie
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1fe281776bd75d8fa869065cd24e85f04fec849d
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331774"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="9087f-102">Delegate — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="9087f-102">delegate operator (C# reference)</span></span>

<span data-ttu-id="9087f-103">`delegate` Operator tworzy anonimową metodę, która może zostać przekonwertowana na typ delegata:</span><span class="sxs-lookup"><span data-stu-id="9087f-103">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](~/samples/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

<span data-ttu-id="9087f-104">Począwszy od C# 3, [wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) zapewniają bardziej zwięzły i jednoznaczny sposób tworzenia anonimowej funkcji.</span><span class="sxs-lookup"><span data-stu-id="9087f-104">Beginning with C# 3, [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="9087f-105">Użyj [operatora = >](lambda-operator.md) , aby utworzyć wyrażenie lambda:</span><span class="sxs-lookup"><span data-stu-id="9087f-105">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>

[!code-csharp-interactive[lambda expression](~/samples/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]

<span data-ttu-id="9087f-106">Gdy używasz `delegate` operatora, możesz pominąć listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="9087f-106">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="9087f-107">W takim przypadku utworzona Metoda anonimowa może zostać przekonwertowana na typ delegata z dowolną listą parametrów, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="9087f-107">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](~/samples/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="9087f-108">Jest to jedyna funkcja metod anonimowych, które nie są obsługiwane przez wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="9087f-108">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="9087f-109">We wszystkich innych przypadkach wyrażenie lambda jest preferowanym sposobem pisania kodu śródwierszowego.</span><span class="sxs-lookup"><span data-stu-id="9087f-109">In all other cases, a lambda expression is a preferred way to write inline code.</span></span> <span data-ttu-id="9087f-110">Aby uzyskać więcej informacji na temat funkcji wyrażeń lambda, na przykład przechwytywania zmiennych zewnętrznych, zobacz [lambda Expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="9087f-110">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="9087f-111">Możesz również użyć słowa `delegate` kluczowego, aby zadeklarować [typ delegata](../builtin-types/reference-types.md#the-delegate-type).</span><span class="sxs-lookup"><span data-stu-id="9087f-111">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9087f-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9087f-112">C# language specification</span></span>

<span data-ttu-id="9087f-113">Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia funkcji anonimowej](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9087f-113">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9087f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9087f-114">See also</span></span>

- [<span data-ttu-id="9087f-115">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="9087f-115">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9087f-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="9087f-116">C# operators</span></span>](index.md)
