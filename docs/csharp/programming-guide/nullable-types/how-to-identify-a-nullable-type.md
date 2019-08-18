---
title: 'Instrukcje: Identyfikowanie typu dopuszczającego wartość null — C# Przewodnik programowania'
ms.custom: seodec18
description: Dowiedz się, jak ustalić, czy typ jest typem dopuszczającym wartość null, albo wystąpieniem typu dopuszczającego wartość null
ms.date: 09/24/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 43a35874b8c9f52c4b98a93e1217994980e1b223
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567378"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="5782a-103">Instrukcje: Identyfikowanie typu dopuszczającego wartość null (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="5782a-103">How to: Identify a nullable type (C# Programming Guide)</span></span>

<span data-ttu-id="5782a-104">Poniższy przykład pokazuje <xref:System.Type?displayProperty=nameWithType> <xref:System.Nullable%601?displayProperty=nameWithType> , jak ustalić, czy wystąpienie reprezentuje zamknięty rodzajowy typ dopuszczający wartość null, czyli typ z określonym parametrem `T`typu:</span><span class="sxs-lookup"><span data-stu-id="5782a-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a closed generic nullable type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="5782a-105">Jak pokazano w przykładzie, należy użyć operatora [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) do utworzenia <xref:System.Type?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5782a-105">As the example shows, you use the [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
<span data-ttu-id="5782a-106">Aby określić, czy wystąpienie jest typu dopuszczającego wartość null, nie należy używać <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody do <xref:System.Type> przetestowania wystąpienia z poprzedzającym kodem.</span><span class="sxs-lookup"><span data-stu-id="5782a-106">If you want to determine whether an instance is of a nullable type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="5782a-107">Po wywołaniu <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody w wystąpieniu typu dopuszczającego wartość null wystąpienie jest opakowane na [](using-nullable-types.md#boxing-and-unboxing) <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5782a-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="5782a-108">Jako opakowanie niezerowego typu dopuszczającego wartość null jest równoznaczne z opakowaniem wartości typu podstawowego, <xref:System.Object.GetType%2A> <xref:System.Type> zwraca obiekt, który reprezentuje typ bazowy typu dopuszczającego wartość null:</span><span class="sxs-lookup"><span data-stu-id="5782a-108">As boxing of a non-null instance of a nullable type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="5782a-109">Nie używaj operatora [is](../../language-reference/keywords/is.md) , aby określić, czy wystąpienie jest typu dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="5782a-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable type.</span></span> <span data-ttu-id="5782a-110">Jak pokazano na poniższym przykładzie, nie można rozróżnić typów wystąpień typu dopuszczającego wartość null i jego typ podstawowy przy `is` użyciu operatora:</span><span class="sxs-lookup"><span data-stu-id="5782a-110">As the following example shows, you cannot distinguish types of instances of a nullable type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="5782a-111">Możesz użyć kodu przedstawionego w poniższym przykładzie, aby określić, czy wystąpienie jest typu dopuszczającego wartość null:</span><span class="sxs-lookup"><span data-stu-id="5782a-111">You can use the code presented in the following example to determine whether an instance is of a nullable type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a><span data-ttu-id="5782a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5782a-112">See also</span></span>

- [<span data-ttu-id="5782a-113">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="5782a-113">Nullable types</span></span>](index.md)
- [<span data-ttu-id="5782a-114">Używanie typów dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="5782a-114">Using nullable types</span></span>](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
