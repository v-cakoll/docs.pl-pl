---
title: 'Instrukcje: Identyfikowanie typu wartości null — C# Przewodnik programowania'
ms.custom: seodec18
description: Dowiedz się, jak ustalić, czy typ jest typem wartości null lub czy wystąpienie ma typ wartości null
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 15b1ffedf57648955ee5a004514841a5d140292b
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392606"
---
# <a name="how-to-identify-a-nullable-value-type-c-programming-guide"></a><span data-ttu-id="aa108-103">Instrukcje: Identyfikowanie typu wartości null (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="aa108-103">How to: identify a nullable value type (C# Programming Guide)</span></span>

<span data-ttu-id="aa108-104">Poniższy przykład pokazuje, jak ustalić, czy wystąpienie <xref:System.Type?displayProperty=nameWithType> reprezentuje zamknięty typ wartości null, czyli typ <xref:System.Nullable%601?displayProperty=nameWithType> z określonym parametrem typu `T`:</span><span class="sxs-lookup"><span data-stu-id="aa108-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a closed generic nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="aa108-105">Jak pokazano w przykładzie, używasz operatora [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) do tworzenia obiektu <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aa108-105">As the example shows, you use the [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="aa108-106">Aby określić, czy wystąpienie ma typ wartości null, nie należy używać metody <xref:System.Object.GetType%2A?displayProperty=nameWithType>, aby uzyskać wystąpienie <xref:System.Type> do przetestowania przy użyciu poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="aa108-106">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="aa108-107">Po wywołaniu metody <xref:System.Object.GetType%2A?displayProperty=nameWithType> w wystąpieniu typu wartości null wystąpienie jest [opakowane](using-nullable-types.md#boxing-and-unboxing) do <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="aa108-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="aa108-108">Jako opakowanie niezerowego typu wartości null jest równoważne z opakowaniem wartości typu podstawowego, <xref:System.Object.GetType%2A> zwraca obiekt <xref:System.Type>, który reprezentuje typ podstawowy typu wartości null:</span><span class="sxs-lookup"><span data-stu-id="aa108-108">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="aa108-109">Nie używaj operatora [is](../../language-reference/keywords/is.md) , aby określić, czy wystąpienie ma typ wartości null.</span><span class="sxs-lookup"><span data-stu-id="aa108-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="aa108-110">Jak pokazano na poniższym przykładzie, nie można rozróżnić typów wystąpień typu wartości null i jego typ podstawowy przy użyciu operatora `is`:</span><span class="sxs-lookup"><span data-stu-id="aa108-110">As the following example shows, you cannot distinguish types of instances of a nullable value type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="aa108-111">Możesz użyć kodu przedstawionego w poniższym przykładzie, aby określić, czy wystąpienie ma typ wartości null:</span><span class="sxs-lookup"><span data-stu-id="aa108-111">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]

## <a name="see-also"></a><span data-ttu-id="aa108-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa108-112">See also</span></span>

- [<span data-ttu-id="aa108-113">Typy wartości null</span><span class="sxs-lookup"><span data-stu-id="aa108-113">Nullable value types</span></span>](index.md)
- [<span data-ttu-id="aa108-114">Używanie typów wartości null</span><span class="sxs-lookup"><span data-stu-id="aa108-114">Using nullable value types</span></span>](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
