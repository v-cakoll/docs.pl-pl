---
title: C#Wyrażenia — Przewodnik po przykładzie C# języka
description: bloki konstrukcyjne są wyrażenia, argumenty operacji i operatory C# języka
ms.date: 04/25/2019
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: ffe800304a9125e11e20d96a84919936f1fee2c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753649"
---
# <a name="expressions"></a>Wyrażenia

*Wyrażenia* są konstruowane na podstawie *operandów* i *operatorów*. Operatory wyrażenia wskazują operacje do zastosowania dla operandów. Przykłady operatorów to `+`, `-`, `*`, `/`i `new`. Przykładami operandów są literały, pola, zmienne lokalne i wyrażenia.

Gdy wyrażenie zawiera wiele operatorów *pierwszeństwo* operatorów określa kolejność, w jakiej są oceniane poszczególne operatory. Na przykład, wyrażenie `x + y * z` jest oceniane jako `x + (y * z)`, ponieważ operator `*` ma wyższy priorytet niż operator `+`.

Gdy operand występuje między dwoma operatorami o tym samym priorytecie *asocjacyjność* operatorów określa kolejność, w której są wykonywane operacje:

* Z wyjątkiem operatorów przypisania wszystkie operatory dwuargumentowe są *lewostronne*, co oznacza, że operacje są wykonywane od lewej do prawej. Na przykład `x + y + z` jest oceniane jako `(x + y) + z`.
* Operatory przypisania i operator warunkowy (`?:`) są *prawostronne*, co oznacza, że operacje są wykonywane od prawej do lewej. Na przykład `x = y = z` jest oceniane jako `x = (y = z)`.

Pierwszeństwo i asocjacyjność mogą być kontrolowane za pomocą nawiasów. Na przykład `x + y * z` najpierw mnoży `y` przez `z` , a następnie dodaje wynik do `x`, ale `(x + y) * z` najpierw dodaje `x` i `y` i następnie wynik mnoży przez `z`.

Większość operatorów może być [ *przeciążone*](../language-reference/keywords/operator.md). Przeciążanie operatora umożliwia określanie definiowanych przez użytkownika implementacji operatorów dla operacji, w których jeden lub oba operandy mają typ struktury lub klasy zdefiniowanej przez użytkownika.

C#udostępnia wiele operatorów przeprowadzić [arytmetyczne](../language-reference/operators/arithmetic-operators.md), [logiczne](../language-reference/operators/boolean-logical-operators.md), [bitowe- and -shift](../language-reference/operators/bitwise-and-shift-operators.md) operacji i [równości](../language-reference/operators/equality-operators.md) i [kolejności](../language-reference/operators/comparison-operators.md) porównania.

Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](../language-reference/operators/index.md).

> [!div class="step-by-step"]
> [Poprzednie](types-and-variables.md)
> [dalej](statements.md)
