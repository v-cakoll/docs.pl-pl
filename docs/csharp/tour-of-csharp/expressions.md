---
title: Wyrażenia języka C# — przewodnik po języku Języka C#
description: Wyrażenia, operandy i operatory są elementami konstrukcyjnymi języka C#
ms.date: 02/27/2020
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 209b5da01cd7539f2bd97023f40fd149910b6f1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159159"
---
# <a name="expressions"></a>Wyrażenia

*Wyrażenia* są zbudowane z *operandów* i *operatorów.* Operatory wyrażenia wskazują, które operacje mają być stosowane do argumentów. Przykłady operatorów obejmują `+` `-`, `*` `/`, `new`, i . Przykłady argumentów obejmują literały, pola, zmienne lokalne i wyrażenia.

Gdy wyrażenie zawiera wiele operatorów, *pierwszeństwo* operatorów kontroluje kolejność, w jakiej poszczególne operatory są oceniane. Na przykład wyrażenie `x + y * z` jest oceniane `x + (y * z)` jako, ponieważ `*` operator ma `+` wyższy priorytet niż operator.

W przypadku wystąpienia operandu między dwoma operatorami o tym samym priorytecie, *asocjalność* operatorów kontroluje kolejność wykonywania operacji:

* Z wyjątkiem operatorów przypisania i null-łączenia, wszystkie operatory binarne są *lewo-zestowacyjne*, co oznacza, że operacje są wykonywane od lewej do prawej. Na przykład `x + y + z` jest oceniana jako `(x + y) + z`.
* Operatory przypisania, null-łączenie `??` i `??=` operatorów i operator `?:` warunkowy są *zestosowne,* co oznacza, że operacje są wykonywane od prawej do lewej. Na przykład `x = y = z` jest oceniana jako `x = (y = z)`.

Pierwszeństwo i kojarzenie można kontrolować za pomocą nawiasów. Na przykład `x + y * z` najpierw `y` mnoży, `z` a `x`następnie `(x + y) * z` dodaje `x` wynik `y` do , ale `z`najpierw dodaje, a następnie mnoży wynik przez .

Większość operatorów może być [*przeciążona.*](../language-reference/operators/operator-overloading.md) Przeciążenie operatora pozwala na implementacje operatora zdefiniowane przez użytkownika, które mają być określone dla operacji, w których jeden lub oba operandy są klasy zdefiniowanej przez użytkownika lub typu struktury.

C# udostępnia szereg operatorów do wykonywania operacji [arytmetycznych,](../language-reference/operators/arithmetic-operators.md) [logicznych,](../language-reference/operators/boolean-logical-operators.md) [bitowych i zmianowych](../language-reference/operators/bitwise-and-shift-operators.md) oraz porównań [równości](../language-reference/operators/equality-operators.md) i [kolejności.](../language-reference/operators/comparison-operators.md)

Aby uzyskać pełną listę operatorów języka C# uporządkowanych według poziomu pierwszeństwa, zobacz [Operatory języka C#.](../language-reference/operators/index.md)

> [!div class="step-by-step"]
> [Poprzedni](types-and-variables.md)
> [następny](statements.md)
