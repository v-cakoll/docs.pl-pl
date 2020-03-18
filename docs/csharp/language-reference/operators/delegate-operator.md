---
title: operator delegata — odwołanie do języka C#
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1dd27fe5fdfdc1bc8a63e1298da00d252e800a72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847342"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="dae55-102">operator delegata (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="dae55-102">delegate operator (C# reference)</span></span>

<span data-ttu-id="dae55-103">Operator `delegate` tworzy metodę anonimową, która może być konwertowana na typ delegata:</span><span class="sxs-lookup"><span data-stu-id="dae55-103">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](snippets/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> <span data-ttu-id="dae55-104">Począwszy od c# 3 wyrażenia lambda zapewniają bardziej zwięzły i wyrazisty sposób tworzenia funkcji anonimowych.</span><span class="sxs-lookup"><span data-stu-id="dae55-104">Beginning with C# 3, lambda expressions provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="dae55-105">Użyj [=> operatora](lambda-operator.md) do skonstruowania wyrażenia lambda:</span><span class="sxs-lookup"><span data-stu-id="dae55-105">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>
>
> [!code-csharp-interactive[lambda expression](snippets/DelegateOperator.cs#Lambda)]
>
> <span data-ttu-id="dae55-106">Aby uzyskać więcej informacji na temat funkcji wyrażeń lambda, na przykład przechwytywania zmiennych zewnętrznych, zobacz [Wyrażenia Lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="dae55-106">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="dae55-107">Korzystając z `delegate` operatora, można pominąć listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="dae55-107">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="dae55-108">Jeśli to zrobisz, utworzona metoda anonimowa może zostać przekonwertowana na typ delegata z dowolną listą parametrów, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="dae55-108">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](snippets/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="dae55-109">Jest to jedyna funkcja metod anonimowych, która nie jest obsługiwana przez wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="dae55-109">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="dae55-110">We wszystkich innych przypadkach wyrażenie lambda jest preferowanym sposobem pisania kodu w wierszu.</span><span class="sxs-lookup"><span data-stu-id="dae55-110">In all other cases, a lambda expression is a preferred way to write inline code.</span></span>

<span data-ttu-id="dae55-111">Słowo `delegate` kluczowe służy również do deklarowania [typu pełnomocnika](../builtin-types/reference-types.md#the-delegate-type).</span><span class="sxs-lookup"><span data-stu-id="dae55-111">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dae55-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dae55-112">C# language specification</span></span>

<span data-ttu-id="dae55-113">Aby uzyskać więcej informacji, zobacz [anonimowe wyrażenia funkcji](~/_csharplang/spec/expressions.md#anonymous-function-expressions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="dae55-113">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dae55-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dae55-114">See also</span></span>

- [<span data-ttu-id="dae55-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dae55-115">C# reference</span></span>](../index.md)
- [<span data-ttu-id="dae55-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="dae55-116">C# operators</span></span>](index.md)
- [<span data-ttu-id="dae55-117">= operator></span><span class="sxs-lookup"><span data-stu-id="dae55-117">=> operator</span></span>](lambda-operator.md)
