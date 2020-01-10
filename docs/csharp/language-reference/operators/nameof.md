---
title: operator nameof — C# odwołanie
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: c1d71d52a9222379adc36479715113b181da7133
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712692"
---
# <a name="nameof-operator-c-reference"></a>nameof — operatorC# (odwołanie)

Operator `nameof` uzyskuje nazwę zmiennej, typu lub składowej jako stałą typu String:

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

Jak pokazano w powyższym przykładzie, w przypadku typu i przestrzeni nazw, wygenerowana nazwa zazwyczaj nie jest w [pełni kwalifikowana](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

Operator `nameof` jest oceniany w czasie kompilacji i nie ma wpływu w czasie wykonywania.

Możesz użyć operatora `nameof`, aby kod sprawdzania argumentów był bardziej konserwowany:

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

Operator `nameof` jest dostępny w C# 6 i nowszych.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia nameof](~/_csharplang/spec/expressions.md#nameof-expressions) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
