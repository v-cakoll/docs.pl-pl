---
title: C#Wyrażenia — Przewodnik po C# języku
description: Wyrażenia, operandy i operatory tworzą bloki C# języka
ms.date: 04/25/2019
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 4866d12118518827c1f7032ac09933927f0f3c52
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395675"
---
# <a name="expressions"></a>Wyrażenia

*Wyrażenia* są zbudowane z *argumentów operacji* i *operatorów*. Operatory wyrażenia wskazują, które operacje mają być stosowane do operandów. Przykłady operatorów obejmują `+`, `-`, `*`, `/` i `new`. Przykłady operandów obejmują literały, pola, zmienne lokalne i wyrażenia.

Gdy wyrażenie zawiera wiele operatorów, *pierwszeństwo* operatorów określa kolejność, w której są oceniane poszczególne operatory. Na przykład wyrażenie `x + y * z` jest oceniane jako `x + (y * z)`, ponieważ operator `*` ma wyższy priorytet niż operator `+`.

Gdy operand występuje między dwoma operatorami o takim samym priorytecie, *łączność* operatorów kontroluje kolejność wykonywania operacji:

* Z wyjątkiem operatorów przypisania i łączenia wartości null wszystkie operatory binarne są z *lewej strony skojarzenia*, co oznacza, że operacje są wykonywane od lewej do prawej. Na przykład `x + y + z` jest oceniane jako `(x + y) + z`.
* Operatory przypisania, łączenie wartości null `??` i operatory `??=` i operator warunkowy `?:` są z prawej strony *skojarzenia*, co oznacza, że operacje są wykonywane od prawej do lewej. Na przykład `x = y = z` jest oceniane jako `x = (y = z)`.

Pierwszeństwo i łączność można kontrolować za pomocą nawiasów. Na przykład `x + y * z` najpierw mnoży `y` przez `z`, a następnie dodaje wynik do `x`, ale `(x + y) * z` dodaje `x` i `y`, a następnie mnoży wynik przez `z`.

Większość operatorów może być [*przeciążona*](../language-reference/operators/operator-overloading.md). Przeciążanie operatora umożliwia określenie implementacji operatora zdefiniowanego przez użytkownika dla operacji, w których jeden lub oba operandy są klasy lub typu struktury zdefiniowanej przez użytkownika.

C#udostępnia wiele operatorów do wykonywania operacji [arytmetycznych](../language-reference/operators/arithmetic-operators.md), [logicznych](../language-reference/operators/boolean-logical-operators.md), [bitowe i przesunięcia](../language-reference/operators/bitwise-and-shift-operators.md) oraz porównywania [równości](../language-reference/operators/equality-operators.md) i [kolejności](../language-reference/operators/comparison-operators.md) .

Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz [ C# operatory](../language-reference/operators/index.md).

> [!div class="step-by-step"]
> [Poprzedni](types-and-variables.md)
> [Następny](statements.md)
