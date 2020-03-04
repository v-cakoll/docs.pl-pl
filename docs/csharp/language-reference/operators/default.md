---
title: domyślny operator — C# odwołanie
description: Użyj operatora domyślnego, aby utworzyć wartość domyślną typu
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: ba4c02caa53a9d532be4012a4543a25cd41b6023
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239316"
---
# <a name="default-operator-c-reference"></a>Default — operatorC# (odwołanie)

Operator `default` generuje [wartość domyślną](../builtin-types/default-values.md) typu. Argument operatora `default` musi być nazwą typu lub parametrem typu.

Poniższy przykład pokazuje użycie operatora `default`:

[!code-csharp-interactive[default of T](~/samples/snippets/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

Możesz również użyć słowa kluczowego `default` jako domyślnej etykiety case w [instrukcji`switch`](../keywords/switch.md).

## <a name="default-literal"></a>domyślny literał

Począwszy od C# 7,1, można użyć literału `default`, aby utworzyć wartość domyślną typu, gdy kompilator może wywnioskować typ wyrażenia. Wyrażenie `default` literału zwraca tę samą wartość co wyrażenie `default(T)`, gdzie `T` jest typem wywnioskowanym. Literału `default` można użyć w dowolnym z następujących przypadków:

- W przypisaniu lub inicjacji zmiennej.
- W deklaracji wartości domyślnej dla [opcjonalnego parametru metody](../../methods.md#optional-parameters-and-arguments).
- W wywołaniu metody, aby podać wartość argumentu.
- W [instrukcji`return`](../keywords/return.md) lub jako wyrażenie w [składowej](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)zawierającej wyrażenie.

Poniższy przykład pokazuje użycie literału `default`:

[!code-csharp-interactive[default literal](~/samples/snippets/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia wartości domyślnej](~/_csharplang/spec/expressions.md#default-value-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Aby uzyskać więcej informacji na temat literału `default`, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Wartości domyślne C# typów](../builtin-types/default-values.md)
- [Typy ogólne w .NET](../../../standard/generics/index.md)
