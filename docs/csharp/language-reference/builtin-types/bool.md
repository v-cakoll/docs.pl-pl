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
# <a name="bool-c-reference"></a>bool (odwołanie do języka C#)

Słowo `bool` kluczowe type jest aliasem <xref:System.Boolean?displayProperty=nameWithType> typu struktury .NET, który reprezentuje wartość `true` `false`logiczną, która może być albo .

Aby wykonać operacje logiczne `bool` z wartościami typu, należy użyć logicznych operatorów [logicznych.](../operators/boolean-logical-operators.md) Typ `bool` jest typu wynik [operatorów porównania](../operators/comparison-operators.md) i [równości.](../operators/equality-operators.md) `bool` Wyrażenie może być kontrolowanie wyrażenia warunkowego w [if](../keywords/if-else.md), [zrobić](../keywords/do.md), [podczas](../keywords/while.md)gdy , i [dla](../keywords/for.md) instrukcji i [w operatorze warunkowym `?:` ](../operators/conditional-operator.md).

Domyślną wartością `bool` tego `false`typu jest .

## <a name="literals"></a>Literały

Można użyć `true` literałów i `false` zainicjować `bool` zmienną lub `bool` przekazać wartość:

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Logika logiczna o trzech wartościach

Użyj typu `bool?` nullable, jeśli trzeba obsługiwać logiki trzech wartości, na przykład podczas pracy z bazami danych, które obsługują typ logiczny o trzech wartościach. W `bool?` przypadku argumentów wstępnie zdefiniowane `&` `|` i operatory obsługują logikę trójwartościową. Aby uzyskać więcej informacji, zobacz [nullable logicznych operatorów logicznych](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) sekcji [logicznych operatorów logicznych.](../operators/boolean-logical-operators.md)

Aby uzyskać więcej informacji na temat typów wartości nullable, zobacz [Typy wartości nullable](nullable-value-types.md).

## <a name="conversions"></a>Konwersje

C# zawiera tylko dwie konwersje, które obejmują `bool` typ. Są to niejawna konwersja `bool?` do odpowiedniego typu `bool?` nullable i jawne konwersji z typu. Jednak .NET udostępnia dodatkowe metody, które można użyć `bool` do konwersji do lub z typu. Aby uzyskać więcej informacji, zobacz [konwersja do i z wartości logicznych](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) sekcji strony referencyjnej <xref:System.Boolean?displayProperty=nameWithType> interfejsu API.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [typ bool](~/_csharplang/spec/types.md#the-bool-type) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Typy wartości](value-types.md)
- [true i false, operatory](../operators/true-false-operators.md)
