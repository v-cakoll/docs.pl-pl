---
title: Operator ~ (odwołanie w C#)
ms.date: 11/05/2018
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 1bcb07c5639a098e3a8c566e92083ca0d48efb81
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153218"
---
# <a name="-operator-c-reference"></a>Operator ~ (odwołanie w C#)

Operator dopełnienia bitowego `~` jest Jednoargumentowy operator, który wytwarza bitowe uzupełnienie swojego operandu odwracając każdy bit. Obsługa wszystkich typów całkowitych `~` operatora.

> [!NOTE]
> `~` Symboli jest również używane do deklarowania finalizatorów. Aby uzyskać więcej informacji, zobacz [finalizatory](../../programming-guide/classes-and-structs/destructors.md).

W poniższym przykładzie pokazano użycie `~` operator:

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseComplementExamples.cs#Example)]

> [!NOTE]
> W poprzednim przykładzie użyto literały binarne [wprowadzona w C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) i [udoskonalone w C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).

## <a name="operator-overloadability"></a>Overloadability — operator

Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `~` operatora.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [operator dopełnienia bitowego](~/_csharplang/spec/expressions.md#bitwise-complement-operator) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [Finalizatory](../../programming-guide/classes-and-structs/destructors.md)
- [& — operator](and-operator.md)
- [| operator](or-operator.md)
- [^ — operator](xor-operator.md)
