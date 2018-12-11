---
title: 'Instrukcje: Identyfikowanie typu dopuszczającego wartość null — C# Programming Guide'
ms.custom: seodec18
description: Dowiedz się, jak ustalić, czy typ jest typ dopuszczający wartość null lub jest wystąpieniem typu dopuszczającego wartość null
ms.date: 09/24/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 88c8c9d881719bd1d09a8879112b26d1c484f827
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240271"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>Instrukcje: Identyfikowanie typu dopuszczającego wartość null (C# Programming Guide)

Poniższy przykład pokazuje, jak ustalić, czy <xref:System.Type?displayProperty=nameWithType> wystąpienie reprezentuje zamknięte ogólnego typu dopuszczającego wartość null, to znaczy, <xref:System.Nullable%601?displayProperty=nameWithType> typu z określonego typu parametru `T`:

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

Jak pokazano w przykładzie, możesz użyć [typeof](../../language-reference/keywords/typeof.md) operatora do utworzenia <xref:System.Type?displayProperty=nameWithType> obiektu.  
  
Jeśli chcesz określić, czy wystąpienie jest typ dopuszczający wartość null, nie używaj <xref:System.Object.GetType%2A?displayProperty=nameWithType> metodę, aby uzyskać <xref:System.Type> wystąpienia z poprzedniego kodu. Gdy wywołujesz <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody w wystąpieniu typu dopuszczającego wartość null, wystąpienie jest [opakowany](using-nullable-types.md#boxing-and-unboxing) do <xref:System.Object>. Pakowanie instancji innych niż null typu dopuszczającego wartość null jest odpowiednikiem pakowania wartości typu podstawowego <xref:System.Object.GetType%2A> zwraca <xref:System.Type> obiekt, który reprezentuje typ podstawowy elementu typu dopuszczającego wartość null:

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

Nie używaj [jest](../../language-reference/keywords/is.md) operator, aby ustalić, czy wystąpienie jest typu dopuszczającego wartość null. Jak pokazano na poniższym przykładzie, nie rozróżnia typów wystąpień typu dopuszczającego wartość null i jej typ podstawowy przy użyciu `is` operator:

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

Kod przedstawiony w poniższym przykładzie służy do ustalania, czy wystąpienie jest typ dopuszczający wartość null:

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a>Zobacz także

- [Typy dopuszczające wartości zerowe](index.md)  
- [Przy użyciu typów dopuszczających wartości zerowe](using-nullable-types.md)  
- <xref:System.Nullable.GetUnderlyingType%2A>  
