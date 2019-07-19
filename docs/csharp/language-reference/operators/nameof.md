---
title: operator nameof — C# odwołanie
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 965b3e96a20906187df4c8693f050c550a747091
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331440"
---
# <a name="nameof-operator-c-reference"></a>nameof — operatorC# (odwołanie)

`nameof` Operator uzyskuje nazwę zmiennej, typu lub składowej jako stałą typu String:

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

Jak pokazano w powyższym przykładzie, w przypadku typu i przestrzeni nazw, wygenerowana nazwa zazwyczaj nie jest w [pełni kwalifikowana](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

`nameof` Operator jest oceniany w czasie kompilacji i nie ma wpływu na czas wykonywania.

Możesz użyć `nameof` operatora, aby kod sprawdzania argumentów był bardziej konserwowany:

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

Operator jest dostępny w C# 6 i nowszych. `nameof`

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia nameof](~/_csharplang/spec/expressions.md#nameof-expressions) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
