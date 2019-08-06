---
title: domyślny operator — C# odwołanie
ms.custom: seodec18
description: Użyj domyślnego operatora, aby utworzyć wartość domyślną typu
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 5623cb9dc3790b5bb99635c41cb3f122f4c71d8e
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68804239"
---
# <a name="default-operator-c-reference"></a>Default — operatorC# (odwołanie)

Operator generuje [wartość domyślną typu.](../keywords/default-values-table.md) `default` Argument `default` operatora musi być nazwą typu lub parametrem typu.

W poniższym przykładzie pokazano sposób użycia `default` operatora:

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

Możesz również użyć `default` słowa kluczowego jako domyślnej etykiety case [ `switch` w instrukcji](../keywords/switch.md).

## <a name="default-literal"></a>domyślny literał

Począwszy od C# 7,1, można użyć `default` literału, aby utworzyć wartość domyślną typu, gdy kompilator może wywnioskować typ wyrażenia. Wyrażenie literału zwraca tę samą wartość `default(T)` , co wyrażenie, `T` gdzie jest typem wywnioskowanym. `default` `default` Literału można użyć w dowolnym z następujących przypadków:

- W przypisaniu lub inicjacji zmiennej.
- W deklaracji wartości domyślnej dla opcjonalnego parametru metody.
- W wywołaniu metody, aby podać wartość argumentu.
- W instrukcji `return` lub jako wyrażenie w składowej zawierającej wyrażenie.

W poniższym przykładzie pokazano użycie `default` literału:

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia wartości domyślnej](~/_csharplang/spec/expressions.md#default-value-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Aby uzyskać więcej informacji na `default` temat literału, zapoznaj się z uwagami dotyczącymi [funkcji](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Tabela wartości domyślnych](../keywords/default-values-table.md)
