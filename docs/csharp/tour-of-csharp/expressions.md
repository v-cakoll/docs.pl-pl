---
title: C#Wyrażenia — Przewodnik po C# języku
description: Wyrażenia, operandy i operatory tworzą bloki C# języka
ms.date: 02/27/2020
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 209b5da01cd7539f2bd97023f40fd149910b6f1d
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159159"
---
# <a name="expressions"></a>Wyrażenia

*Wyrażenia* są zbudowane z *argumentów operacji* i *operatorów*. Operatory wyrażenia wskazują operacje do zastosowania dla operandów. Przykłady operatorów obejmują `+`, `-`, `*`, `/`i `new`. Przykładami operandów są literały, pola, zmienne lokalne i wyrażenia.

Gdy wyrażenie zawiera wiele operatorów, *pierwszeństwo* operatorów określa kolejność, w której są oceniane poszczególne operatory. Na przykład wyrażenie `x + y * z` jest oceniane jako `x + (y * z)`, ponieważ operator `*` ma wyższy priorytet niż operator `+`.

Gdy operand występuje między dwoma operatorami o takim samym priorytecie, *łączność* operatorów kontroluje kolejność wykonywania operacji:

* Z wyjątkiem operatorów przypisania i łączenia wartości null wszystkie operatory binarne są z *lewej strony skojarzenia*, co oznacza, że operacje są wykonywane od lewej do prawej. Na przykład `x + y + z` jest oceniane jako `(x + y) + z`.
* Operatory przypisania, `??` i operatory `??=`, a operator warunkowy `?:` są z *prawej strony skojarzenia*, co oznacza, że operacje są wykonywane od prawej do lewej. Na przykład `x = y = z` jest oceniane jako `x = (y = z)`.

Pierwszeństwo i asocjacyjność mogą być kontrolowane za pomocą nawiasów. Na przykład `x + y * z` najpierw mnoży `y` przez `z`, a następnie dodaje wynik do `x`, ale `(x + y) * z` najpierw dodaje `x` i `y`, a następnie mnoży wynik przez `z`.

Większość operatorów może być [*przeciążona*](../language-reference/operators/operator-overloading.md). Przeciążanie operatora umożliwia określanie definiowanych przez użytkownika implementacji operatorów dla operacji, w których jeden lub oba operandy mają typ struktury lub klasy zdefiniowanej przez użytkownika.

C#udostępnia wiele operatorów do wykonywania operacji [arytmetycznych](../language-reference/operators/arithmetic-operators.md), [logicznych](../language-reference/operators/boolean-logical-operators.md), [bitowe i przesunięcia](../language-reference/operators/bitwise-and-shift-operators.md) oraz porównywania [równości](../language-reference/operators/equality-operators.md) i [kolejności](../language-reference/operators/comparison-operators.md) .

Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz [ C# operatory](../language-reference/operators/index.md).

> [!div class="step-by-step"]
> [Poprzednie](types-and-variables.md)
> [dalej](statements.md)
