---
title: 'Porady: Identyfikowanie typu dopuszczającego wartość null (C# Programming Guide)'
description: Dowiedz się, jak ustalić, czy typ jest typ dopuszczający wartość null lub jest wystąpieniem typu dopuszczającego wartość null
ms.date: 08/06/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: bb7ab2b8c13c2b8b4b6cd60e7959a391cd7e75c1
ms.sourcegitcommit: bd4fa78f5a46133efdead1bc692a9aa2811d7868
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42754959"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="a5dee-103">Porady: Identyfikowanie typu dopuszczającego wartość null (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="a5dee-103">How to: Identify a nullable type (C# Programming Guide)</span></span>

<span data-ttu-id="a5dee-104">Poniższy przykład pokazuje, jak ustalić, czy <xref:System.Type?displayProperty=nameWithType> wystąpienie reprezentuje typ dopuszczający wartość null:</span><span class="sxs-lookup"><span data-stu-id="a5dee-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a nullable type:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="a5dee-105">Jak pokazano w przykładzie, możesz użyć [typeof](../../language-reference/keywords/typeof.md) operatora do utworzenia <xref:System.Type?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a5dee-105">As the example shows, you use the [typeof](../../language-reference/keywords/typeof.md) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
<span data-ttu-id="a5dee-106">Jeśli chcesz określić, czy wystąpienie jest typ dopuszczający wartość null, nie używaj <xref:System.Object.GetType%2A?displayProperty=nameWithType> metodę, aby uzyskać <xref:System.Type> wystąpienia z poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="a5dee-106">If you want to determine whether an instance is of a nullable type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="a5dee-107">Gdy wywołujesz <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody w wystąpieniu typu dopuszczającego wartość null, wystąpienie jest [opakowany](using-nullable-types.md#boxing-and-unboxing) do <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a5dee-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="a5dee-108">Pakowanie instancji innych niż null typu dopuszczającego wartość null jest odpowiednikiem pakowania wartości typu podstawowego <xref:System.Object.GetType%2A> zwraca <xref:System.Type> obiekt, który reprezentuje typ podstawowy elementu typu dopuszczającego wartość null:</span><span class="sxs-lookup"><span data-stu-id="a5dee-108">As boxing of a non-null instance of a nullable type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="a5dee-109">Nie używaj [jest](../../language-reference/keywords/is.md) operator, aby ustalić, czy wystąpienie jest typu dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="a5dee-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable type.</span></span> <span data-ttu-id="a5dee-110">Jak pokazano na poniższym przykładzie, nie rozróżnia typów wystąpień typu dopuszczającego wartość null i jej typ podstawowy przy użyciu `is` operator:</span><span class="sxs-lookup"><span data-stu-id="a5dee-110">As the following example shows, you cannot distinguish types of instances of a nullable type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="a5dee-111">Kod przedstawiony w poniższym przykładzie służy do ustalania, czy wystąpienie jest typ dopuszczający wartość null:</span><span class="sxs-lookup"><span data-stu-id="a5dee-111">You can use the code presented in the following example to determine whether an instance is of a nullable type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a><span data-ttu-id="a5dee-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5dee-112">See also</span></span>

[<span data-ttu-id="a5dee-113">Typy dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="a5dee-113">Nullable types</span></span>](index.md)  
[<span data-ttu-id="a5dee-114">Przy użyciu typów dopuszczających wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="a5dee-114">Using nullable types</span></span>](using-nullable-types.md)  
<xref:System.Nullable.GetUnderlyingType%2A>  
