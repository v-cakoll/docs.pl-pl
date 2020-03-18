---
title: operator domyślny — odwołanie do języka C#
description: Użyj domyślnego operatora do wytworzenia wartości domyślnej typu
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 0d37fe952e71e74f014872231a2e58663dea9d18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399484"
---
# <a name="default-operator-c-reference"></a>operator domyślny (odwołanie do języka C#)

Operator `default` tworzy [wartość domyślną](../builtin-types/default-values.md) typu. Argument `default` do operatora musi być nazwa typu lub parametrtypu.

W poniższym przykładzie przedstawiono `default` użycie operatora:

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

Słowo `default` kluczowe jest również używane jako domyślna etykieta sprawy w [ `switch` instrukcji](../keywords/switch.md).

## <a name="default-literal"></a>literał domyślny

Począwszy od Języka C# 7.1, można użyć `default` literału do produkcji wartości domyślnej typu, gdy kompilator można wywnioskować typ wyrażenia. Wyrażenie `default` literału tworzy tę `default(T)` samą `T` wartość co wyrażenie, w którym jest typem wywnioskowanym. Literału `default` można użyć w dowolnym z następujących przypadków:

- W przypisaniu lub inicjowaniu zmiennej.
- W deklaracji wartości domyślnej dla [parametru metody opcjonalnej](../../methods.md#optional-parameters-and-arguments).
- W wywołaniu metody, aby podać wartość argumentu.
- W [ `return` instrukcji](../keywords/return.md) lub jako wyrażenie w [element członkowski zabudowany wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

W poniższym przykładzie przedstawiono `default` użycie literału:

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcję Domyślne wyrażenia wartości](~/_csharplang/spec/expressions.md#default-value-expressions) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

Aby uzyskać więcej `default` informacji na temat literału, zobacz [notatkę propozycji funkcji](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Domyślne wartości typów Języka C#](../builtin-types/default-values.md)
- [Typy ogólne w .NET](../../../standard/generics/index.md)
