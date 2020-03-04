---
title: Typ bool- C# odwołanie
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 0e01c183ef07c23203619e0cbbf550c6268bdd46
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239836"
---
# <a name="bool-c-reference"></a><span data-ttu-id="4dcc2-102">bool (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="4dcc2-102">bool (C# reference)</span></span>

<span data-ttu-id="4dcc2-103">Słowo kluczowe typu `bool` jest aliasem dla typu struktury <xref:System.Boolean?displayProperty=nameWithType> .NET, który reprezentuje wartość logiczną, która może być `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="4dcc2-103">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="4dcc2-104">Aby wykonać operacje logiczne przy użyciu wartości typu `bool`, użyj logicznych operatorów [logicznych](../operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="4dcc2-104">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="4dcc2-105">Typ `bool` jest typem wyniku [porównania](../operators/comparison-operators.md) i operatory [równości](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="4dcc2-105">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="4dcc2-106">Wyrażenie `bool` może być kontrolnym wyrażeniem warunkowym w instrukcjach [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)i [for](../keywords/for.md) oraz w [operatorze warunkowym `?:`](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4dcc2-106">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="4dcc2-107">Wartość domyślna typu `bool` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="4dcc2-107">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="4dcc2-108">Literały</span><span class="sxs-lookup"><span data-stu-id="4dcc2-108">Literals</span></span>

<span data-ttu-id="4dcc2-109">Można użyć literałów `true` i `false`, aby zainicjować zmienną `bool` lub przekazać `bool` wartość:</span><span class="sxs-lookup"><span data-stu-id="4dcc2-109">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](~/samples/snippets/csharp/language-reference/builtin-types/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="4dcc2-110">Logika logiczna z trzema wartościami</span><span class="sxs-lookup"><span data-stu-id="4dcc2-110">Three-valued Boolean logic</span></span>

<span data-ttu-id="4dcc2-111">Typ `bool?` dopuszczający wartość null, jeśli potrzebna jest obsługa logiki trójwarstwowej, na przykład podczas pracy z bazami danych, które obsługują typ Boolean o wartości 3.</span><span class="sxs-lookup"><span data-stu-id="4dcc2-111">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="4dcc2-112">W przypadku operandów `bool?` wstępnie zdefiniowane `&` i operatory `|` obsługują logikę z trzema wartościami.</span><span class="sxs-lookup"><span data-stu-id="4dcc2-112">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="4dcc2-113">Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne wartości null](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) w artykule [Operatory logiczne Boolean](../operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="4dcc2-113">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="4dcc2-114">Aby uzyskać więcej informacji na temat typów wartości null, zobacz [dopuszczanie typów wartości null](nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="4dcc2-114">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="4dcc2-115">Konwersje</span><span class="sxs-lookup"><span data-stu-id="4dcc2-115">Conversions</span></span>

<span data-ttu-id="4dcc2-116">C#zawiera tylko dwie konwersje, które obejmują typ `bool`.</span><span class="sxs-lookup"><span data-stu-id="4dcc2-116">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="4dcc2-117">Są one niejawną konwersją do odpowiedniego typu `bool?` nullable i jawnej konwersji z typu `bool?`.</span><span class="sxs-lookup"><span data-stu-id="4dcc2-117">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="4dcc2-118">Jednak platforma .NET udostępnia dodatkowe metody, których można użyć do przekonwertowania na typ `bool` lub z niego.</span><span class="sxs-lookup"><span data-stu-id="4dcc2-118">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="4dcc2-119">Aby uzyskać więcej informacji, zobacz sekcję [konwertowanie do i z wartości logicznych](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) na stronie informacje o interfejsie API <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4dcc2-119">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4dcc2-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4dcc2-120">C# language specification</span></span>

<span data-ttu-id="4dcc2-121">Aby uzyskać więcej informacji, zobacz sekcję [Typ bool](~/_csharplang/spec/types.md#the-bool-type) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="4dcc2-121">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4dcc2-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4dcc2-122">See also</span></span>

- [<span data-ttu-id="4dcc2-123">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="4dcc2-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4dcc2-124">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="4dcc2-124">Value types</span></span>](value-types.md)
- [<span data-ttu-id="4dcc2-125">Operatory true i false</span><span class="sxs-lookup"><span data-stu-id="4dcc2-125">true and false operators</span></span>](../operators/true-false-operators.md)
