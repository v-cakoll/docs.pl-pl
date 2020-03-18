---
title: typ bool - odwołanie do języka C#
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 2ba2e54a6b0f24402fc3728dfe19b548a2368830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846448"
---
# <a name="bool-c-reference"></a><span data-ttu-id="900ce-102">bool (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="900ce-102">bool (C# reference)</span></span>

<span data-ttu-id="900ce-103">Słowo `bool` kluczowe type jest aliasem <xref:System.Boolean?displayProperty=nameWithType> typu struktury .NET, który reprezentuje wartość `true` `false`logiczną, która może być albo .</span><span class="sxs-lookup"><span data-stu-id="900ce-103">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="900ce-104">Aby wykonać operacje logiczne `bool` z wartościami typu, należy użyć logicznych operatorów [logicznych.](../operators/boolean-logical-operators.md)</span><span class="sxs-lookup"><span data-stu-id="900ce-104">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="900ce-105">Typ `bool` jest typu wynik [operatorów porównania](../operators/comparison-operators.md) i [równości.](../operators/equality-operators.md)</span><span class="sxs-lookup"><span data-stu-id="900ce-105">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="900ce-106">`bool` Wyrażenie może być kontrolowanie wyrażenia warunkowego w [if](../keywords/if-else.md), [zrobić](../keywords/do.md), [podczas](../keywords/while.md)gdy , i [dla](../keywords/for.md) instrukcji i [w operatorze warunkowym `?:` ](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="900ce-106">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="900ce-107">Domyślną wartością `bool` tego `false`typu jest .</span><span class="sxs-lookup"><span data-stu-id="900ce-107">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="900ce-108">Literały</span><span class="sxs-lookup"><span data-stu-id="900ce-108">Literals</span></span>

<span data-ttu-id="900ce-109">Można użyć `true` literałów i `false` zainicjować `bool` zmienną lub `bool` przekazać wartość:</span><span class="sxs-lookup"><span data-stu-id="900ce-109">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="900ce-110">Logika logiczna o trzech wartościach</span><span class="sxs-lookup"><span data-stu-id="900ce-110">Three-valued Boolean logic</span></span>

<span data-ttu-id="900ce-111">Użyj typu `bool?` nullable, jeśli trzeba obsługiwać logiki trzech wartości, na przykład podczas pracy z bazami danych, które obsługują typ logiczny o trzech wartościach.</span><span class="sxs-lookup"><span data-stu-id="900ce-111">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="900ce-112">W `bool?` przypadku argumentów wstępnie zdefiniowane `&` `|` i operatory obsługują logikę trójwartościową.</span><span class="sxs-lookup"><span data-stu-id="900ce-112">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="900ce-113">Aby uzyskać więcej informacji, zobacz [nullable logicznych operatorów logicznych](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) sekcji [logicznych operatorów logicznych.](../operators/boolean-logical-operators.md)</span><span class="sxs-lookup"><span data-stu-id="900ce-113">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="900ce-114">Aby uzyskać więcej informacji na temat typów wartości nullable, zobacz [Typy wartości nullable](nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="900ce-114">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="900ce-115">Konwersje</span><span class="sxs-lookup"><span data-stu-id="900ce-115">Conversions</span></span>

<span data-ttu-id="900ce-116">C# zawiera tylko dwie konwersje, które obejmują `bool` typ.</span><span class="sxs-lookup"><span data-stu-id="900ce-116">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="900ce-117">Są to niejawna konwersja `bool?` do odpowiedniego typu `bool?` nullable i jawne konwersji z typu.</span><span class="sxs-lookup"><span data-stu-id="900ce-117">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="900ce-118">Jednak .NET udostępnia dodatkowe metody, które można użyć `bool` do konwersji do lub z typu.</span><span class="sxs-lookup"><span data-stu-id="900ce-118">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="900ce-119">Aby uzyskać więcej informacji, zobacz [konwersja do i z wartości logicznych](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) sekcji strony referencyjnej <xref:System.Boolean?displayProperty=nameWithType> interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="900ce-119">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="900ce-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="900ce-120">C# language specification</span></span>

<span data-ttu-id="900ce-121">Aby uzyskać więcej informacji, zobacz sekcję [typ bool](~/_csharplang/spec/types.md#the-bool-type) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="900ce-121">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="900ce-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="900ce-122">See also</span></span>

- [<span data-ttu-id="900ce-123">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="900ce-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="900ce-124">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="900ce-124">Value types</span></span>](value-types.md)
- [<span data-ttu-id="900ce-125">true i false, operatory</span><span class="sxs-lookup"><span data-stu-id="900ce-125">true and false operators</span></span>](../operators/true-false-operators.md)
