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
# <a name="how-to-identify-a-nullable-value-type-c-programming-guide"></a>Instrukcje: Identyfikowanie typu wartości null (C# Przewodnik programowania)

Poniższy przykład pokazuje, jak ustalić, czy wystąpienie <xref:System.Type?displayProperty=nameWithType> reprezentuje zamknięty typ wartości null, czyli typ <xref:System.Nullable%601?displayProperty=nameWithType> z określonym parametrem typu `T`:

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

Jak pokazano w przykładzie, używasz operatora [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) do tworzenia obiektu <xref:System.Type?displayProperty=nameWithType>.

Aby określić, czy wystąpienie ma typ wartości null, nie należy używać metody <xref:System.Object.GetType%2A?displayProperty=nameWithType>, aby uzyskać wystąpienie <xref:System.Type> do przetestowania przy użyciu poprzedniego kodu. Po wywołaniu metody <xref:System.Object.GetType%2A?displayProperty=nameWithType> w wystąpieniu typu wartości null wystąpienie jest [opakowane](using-nullable-types.md#boxing-and-unboxing) do <xref:System.Object>. Jako opakowanie niezerowego typu wartości null jest równoważne z opakowaniem wartości typu podstawowego, <xref:System.Object.GetType%2A> zwraca obiekt <xref:System.Type>, który reprezentuje typ podstawowy typu wartości null:

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

Nie używaj operatora [is](../../language-reference/keywords/is.md) , aby określić, czy wystąpienie ma typ wartości null. Jak pokazano na poniższym przykładzie, nie można rozróżnić typów wystąpień typu wartości null i jego typ podstawowy przy użyciu operatora `is`:

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

Możesz użyć kodu przedstawionego w poniższym przykładzie, aby określić, czy wystąpienie ma typ wartości null:

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]

## <a name="see-also"></a>Zobacz także

- [Typy wartości null](index.md)
- [Używanie typów wartości null](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
