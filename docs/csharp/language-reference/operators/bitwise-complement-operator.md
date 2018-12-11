---
title: ~ Operator - C# odwołania
ms.custom: seodec18
ms.date: 11/05/2018
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 57e5baee423c0b5d9292d0ad4cbf909646eb3a38
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235728"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="46cf5-102">Operator ~ (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="46cf5-102">~ Operator (C# Reference)</span></span>

<span data-ttu-id="46cf5-103">Operator dopełnienia bitowego `~` jest Jednoargumentowy operator, który wytwarza bitowe uzupełnienie swojego operandu odwracając każdy bit.</span><span class="sxs-lookup"><span data-stu-id="46cf5-103">The bitwise complement operator `~` is a unary operator that produces a bitwise complement of its operand by reversing each bit.</span></span> <span data-ttu-id="46cf5-104">Obsługa wszystkich typów całkowitych `~` operatora.</span><span class="sxs-lookup"><span data-stu-id="46cf5-104">All integer types support the `~` operator.</span></span>

> [!NOTE]
> <span data-ttu-id="46cf5-105">`~` Symboli jest również używane do deklarowania finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="46cf5-105">The `~` symbol is also used to declare finalizers.</span></span> <span data-ttu-id="46cf5-106">Aby uzyskać więcej informacji, zobacz [finalizatory](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="46cf5-106">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

<span data-ttu-id="46cf5-107">W poniższym przykładzie pokazano użycie `~` operator:</span><span class="sxs-lookup"><span data-stu-id="46cf5-107">The following example demonstrates the usage of the `~` operator:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseComplementExamples.cs#Example)]

> [!NOTE]
> <span data-ttu-id="46cf5-108">W poprzednim przykładzie użyto literały binarne [wprowadzona w C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) i [udoskonalone w C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="46cf5-108">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced  in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="46cf5-109">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="46cf5-109">Operator overloadability</span></span>

<span data-ttu-id="46cf5-110">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `~` operatora.</span><span class="sxs-lookup"><span data-stu-id="46cf5-110">User-defined types can [overload](../keywords/operator.md) the `~` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="46cf5-111">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="46cf5-111">C# language specification</span></span>

<span data-ttu-id="46cf5-112">Aby uzyskać więcej informacji, zobacz [operator dopełnienia bitowego](~/_csharplang/spec/expressions.md#bitwise-complement-operator) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="46cf5-112">For more information, see the [Bitwise complement operator](~/_csharplang/spec/expressions.md#bitwise-complement-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46cf5-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46cf5-113">See also</span></span>

- [<span data-ttu-id="46cf5-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="46cf5-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="46cf5-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="46cf5-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="46cf5-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="46cf5-116">C# Operators</span></span>](index.md)
- [<span data-ttu-id="46cf5-117">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="46cf5-117">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)
- [<span data-ttu-id="46cf5-118">& — operator</span><span class="sxs-lookup"><span data-stu-id="46cf5-118">& operator</span></span>](and-operator.md)
- [<span data-ttu-id="46cf5-119">| operator</span><span class="sxs-lookup"><span data-stu-id="46cf5-119">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="46cf5-120">^ — operator</span><span class="sxs-lookup"><span data-stu-id="46cf5-120">^ operator</span></span>](xor-operator.md)
