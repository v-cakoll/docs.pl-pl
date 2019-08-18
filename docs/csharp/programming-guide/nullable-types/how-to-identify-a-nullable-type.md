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
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>Instrukcje: Identyfikowanie typu dopuszczającego wartość null (C# Przewodnik programowania)

Poniższy przykład pokazuje <xref:System.Type?displayProperty=nameWithType> <xref:System.Nullable%601?displayProperty=nameWithType> , jak ustalić, czy wystąpienie reprezentuje zamknięty rodzajowy typ dopuszczający wartość null, czyli typ z określonym parametrem `T`typu:

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

Jak pokazano w przykładzie, należy użyć operatora [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) do utworzenia <xref:System.Type?displayProperty=nameWithType> obiektu.  
  
Aby określić, czy wystąpienie jest typu dopuszczającego wartość null, nie należy używać <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody do <xref:System.Type> przetestowania wystąpienia z poprzedzającym kodem. Po wywołaniu <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody w wystąpieniu typu dopuszczającego wartość null wystąpienie jest opakowane na [](using-nullable-types.md#boxing-and-unboxing) <xref:System.Object>. Jako opakowanie niezerowego typu dopuszczającego wartość null jest równoznaczne z opakowaniem wartości typu podstawowego, <xref:System.Object.GetType%2A> <xref:System.Type> zwraca obiekt, który reprezentuje typ bazowy typu dopuszczającego wartość null:

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

Nie używaj operatora [is](../../language-reference/keywords/is.md) , aby określić, czy wystąpienie jest typu dopuszczającego wartość null. Jak pokazano na poniższym przykładzie, nie można rozróżnić typów wystąpień typu dopuszczającego wartość null i jego typ podstawowy przy `is` użyciu operatora:

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

Możesz użyć kodu przedstawionego w poniższym przykładzie, aby określić, czy wystąpienie jest typu dopuszczającego wartość null:

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a>Zobacz także

- [Typy dopuszczające wartości null](index.md)
- [Używanie typów dopuszczających wartości null](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
