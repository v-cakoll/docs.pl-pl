---
title: nameof operator - odwołanie do języka C#
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: ffbc801acf61bf72db1c88912dc2142a478fa280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846275"
---
# <a name="nameof-operator-c-reference"></a>operator nameof (odwołanie do języka C#)

Operator `nameof` uzyskuje nazwę zmiennej, typu lub elementu członkowskiego jako stałą ciągu:

[!code-csharp-interactive[nameof operator](snippets/NameOfOperator.cs#Examples)]

Jak pokazano w poprzednim przykładzie, w przypadku typu i obszaru nazw, nazwa wyprodukowana zwykle nie jest [w pełni kwalifikowana.](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)

Operator `nameof` jest oceniany w czasie kompilacji i nie ma wpływu w czasie wykonywania.

Operator służy `nameof` do tworzenia kodu sprawdzania argumentów bardziej wykonalne:

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

Operator `nameof` jest dostępny w języku C# 6 i nowszych.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [Nameof wyrażeń](~/_csharplang/spec/expressions.md#nameof-expressions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
