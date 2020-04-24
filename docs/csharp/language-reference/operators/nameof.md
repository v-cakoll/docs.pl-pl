---
title: wyrażenie nameof — odwołanie w C#
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: d71acf0cf7d5cdcfa5310455af2120fa1f82d567
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135922"
---
# <a name="nameof-expression-c-reference"></a>wyrażenie nameof (odwołanie w C#)

`nameof` Wyrażenie tworzy nazwę zmiennej, typu lub składowej jako stałą typu String:

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

Jak pokazano w powyższym przykładzie, w przypadku typu i przestrzeni nazw, wygenerowana nazwa zazwyczaj nie jest w [pełni kwalifikowana](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

W przypadku [identyfikatorów Verbatim](../tokens/verbatim.md) `@` znak nie jest częścią nazwy, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[nameof verbatim](snippets/NameOfOperator.cs#Verbatim)]

`nameof` Wyrażenie jest oceniane w czasie kompilacji i nie ma wpływu na czas wykonywania.

Możesz użyć `nameof` wyrażenia, aby zwiększyć łatwość obsługi kodu sprawdzania argumentów:

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

`nameof` Wyrażenie jest dostępne w języku C# 6 i nowszych.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia nameof](~/_csharplang/spec/expressions.md#nameof-expressions) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
