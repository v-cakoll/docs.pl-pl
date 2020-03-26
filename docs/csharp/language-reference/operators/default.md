---
title: domyślne wyrażenia wartości — odwołanie do języka C#
description: Użyj domyślnych wyrażeń wartości, aby uzyskać wartość domyślną typu
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
- default
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 2adfd8d24066e9dad50c3c18407d3ade71b4b68e
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507181"
---
# <a name="default-value-expressions-c-reference"></a>domyślne wyrażenia wartości (odwołanie do języka C#)

Domyślne wyrażenie wartości tworzy [wartość domyślną](../builtin-types/default-values.md) typu. Istnieją dwa rodzaje domyślnych wyrażeń wartości: [domyślne](#default-operator) wywołanie operatora i [domyślny literał](#default-literal).

`default` Słowo kluczowe służy również jako domyślna etykieta sprawy w [ `switch` instrukcji](../keywords/switch.md).

## <a name="default-operator"></a>default, operator

Argumentem `default` operatora musi być nazwa typu lub parametru typu, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a>domyślny literał

Począwszy od języka C# 7.1, można użyć `default` literału do uzyskania domyślnej wartości typu, gdy kompilator można wywnioskować typ wyrażenia. Wyrażenie `default` dosłowne tworzy taką `default(T)` samą `T` wartość jak wyrażenie, gdzie jest typem wywnioskowane. `default` Literał można użyć w dowolnym z następujących przypadków:

- W przypisywaniu lub inicjalizacji zmiennej.
- W deklaracji wartości domyślnej dla [parametru metody opcjonalnej](../../methods.md#optional-parameters-and-arguments).
- W wywołaniu metody, aby podać wartość argumentu.
- W [ `return` instrukcji](../keywords/return.md) lub jako wyrażenie w wyrażeniu-zabudowany [element członkowski](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

W poniższym przykładzie `default` pokazano użycie literału:

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcję Domyślne wyrażenia wartości](~/_csharplang/spec/expressions.md#default-value-expressions) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

Aby uzyskać więcej `default` informacji na temat literału, zobacz [notatkę dotyczącą propozycji funkcji](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Domyślne wartości typów języka C#](../builtin-types/default-values.md)
- [Typy ogólne w .NET](../../../standard/generics/index.md)
