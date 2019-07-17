---
title: operator nameof — C# odwołania
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 945a8a8ff6d96cb505fa10e85c21a93347661a23
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238691"
---
# <a name="nameof-operator-c-reference"></a>nameof operator (C# odwołania)

`nameof` Operator uzyskuje nazwę zmiennej, typu lub składowej jako stała typu string:

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

Zgodnie z poprzednim przykładzie pokazano, w przypadku typu i przestrzeni nazw, nazwę utworzone zazwyczaj nie jest [w pełni kwalifikowana](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

`nameof` Operator jest obliczane w czasie kompilacji i nie ma wpływu w czasie wykonywania.

Możesz użyć `nameof` operator się będzie łatwiejszy w utrzymaniu kod sprawdzania argumentu:

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

`nameof` Operator jest dostępna w C# 6 i nowsze.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [wyrażeń Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
