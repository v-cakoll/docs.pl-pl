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
ms.openlocfilehash: 720ece2f7f47961e0ab6ebf03c8afeb5fa3a6271
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093269"
---
# <a name="bool-c-reference"></a>bool (C# odwołanie)

Słowo kluczowe typu `bool` jest aliasem dla typu struktury <xref:System.Boolean?displayProperty=nameWithType> .NET, który reprezentuje wartość logiczną, która może być `true` lub `false`.

Aby wykonać operacje logiczne przy użyciu wartości typu `bool`, użyj logicznych operatorów [logicznych](../operators/boolean-logical-operators.md) . Typ `bool` jest typem wyniku [porównania](../operators/comparison-operators.md) i operatory [równości](../operators/equality-operators.md) . Wyrażenie `bool` może być kontrolnym wyrażeniem warunkowym w instrukcjach [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)i [for](../keywords/for.md) oraz w [operatorze warunkowym `?:`](../operators/conditional-operator.md).

Wartość domyślna typu `bool` jest `false`.

## <a name="literals"></a>Literały

Można użyć literałów `true` i `false`, aby zainicjować zmienną `bool` lub przekazać `bool` wartość:

[!code-csharp-interactive[bool literals](~/samples/csharp/language-reference/builtin-types/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Logika logiczna z trzema wartościami

Typ `bool?` dopuszczający wartość null, jeśli potrzebna jest obsługa logiki trójwarstwowej, na przykład podczas pracy z bazami danych, które obsługują typ Boolean o wartości 3. W przypadku operandów `bool?` wstępnie zdefiniowane `&` i operatory `|` obsługują logikę z trzema wartościami. Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne wartości null](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) w artykule [Operatory logiczne Boolean](../operators/boolean-logical-operators.md) .

Aby uzyskać więcej informacji na temat typów wartości null, zobacz [dopuszczanie typów wartości null](nullable-value-types.md).

## <a name="conversions"></a>Konwersje

C#zawiera tylko dwie konwersje, które obejmują typ `bool`. Są one niejawną konwersją do odpowiedniego typu `bool?` nullable i jawnej konwersji z typu `bool?`. Jednak platforma .NET udostępnia dodatkowe metody, których można użyć do przekonwertowania na typ `bool` lub z niego. Aby uzyskać więcej informacji, zobacz sekcję [konwertowanie do i z wartości logicznych](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) na stronie informacje o interfejsie API <xref:System.Boolean?displayProperty=nameWithType>.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Typ bool](~/_csharplang/spec/types.md#the-bool-type) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Typy wartości](value-types.md)
- [Operatory true i false](../operators/true-false-operators.md)
