---
title: nazwa wyrażenia — odwołanie do języka C#
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 5a68161be7bb03122d2a63ccef4365c5853862b2
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507142"
---
# <a name="nameof-expression-c-reference"></a>nazwa wyrażenia (odwołanie do języka C#)

Wyrażenie `nameof` tworzy nazwę zmiennej, typu lub elementu członkowskiego jako stałą ciągu:

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

Jak pokazano w poprzednim przykładzie, w przypadku typu i obszaru nazw powstała nazwa zwykle nie jest [w pełni kwalifikowana.](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)

Wyrażenie `nameof` jest oceniane w czasie kompilacji i nie ma wpływu w czasie wykonywania.

Można użyć `nameof` wyrażenia, aby kod sprawdzania argumentów był bardziej sprawny:

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

Wyrażenie `nameof` jest dostępne w języku C# 6 i nowszych.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) [w specyfikacji języka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
