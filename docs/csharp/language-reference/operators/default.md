---
title: domyślny operator — C# odwołanie
ms.custom: seodec18
description: Użyj operatora domyślnego, aby utworzyć wartość domyślną typu
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 6503e82a42f116a7ba8461ae060592377579f255
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039051"
---
# <a name="default-operator-c-reference"></a>Default — operatorC# (odwołanie)

Operator `default` generuje [wartość domyślną](../keywords/default-values-table.md) typu. Argument operatora `default` musi być nazwą typu lub parametrem typu.

Poniższy przykład pokazuje użycie operatora `default`:

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

Możesz również użyć słowa kluczowego `default` jako domyślnej etykiety case w [instrukcji`switch`](../keywords/switch.md).

## <a name="default-literal"></a>domyślny literał

Począwszy od C# 7,1, można użyć literału`default`, aby utworzyć wartość domyślną typu, gdy kompilator może wywnioskować typ wyrażenia. Wyrażenie `default` literału zwraca tę samą wartość co wyrażenie `default(T)`, gdzie `T` jest typem wywnioskowanym. Literału `default` można użyć w dowolnym z następujących przypadków:

- W przypisaniu lub inicjacji zmiennej.
- W deklaracji wartości domyślnej dla [opcjonalnego parametru metody](../../methods.md#optional-parameters-and-arguments).
- W wywołaniu metody, aby podać wartość argumentu.
- W [instrukcji`return`](../keywords/return.md) lub jako wyrażenie w [składowej](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)zawierającej wyrażenie.

Poniższy przykład pokazuje użycie literału `default`:

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia wartości domyślnej](~/_csharplang/spec/expressions.md#default-value-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Aby uzyskać więcej informacji na temat literału `default`, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Tabela wartości domyślnych](../keywords/default-values-table.md)
- [Typy ogólne w .NET](../../../standard/generics/index.md)
