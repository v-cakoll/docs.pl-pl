---
title: Funkcja zagnieżdżona nie posiada podpisu zgodnego z delegatem „<delegatename>”.
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: d65c8eab661675c955ff6562098248c04036d6e7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580651"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>Funkcja zagnieżdżona nie ma sygnatury zgodnej z delegatem "\<delegatename >"

Wyrażenie lambda zostało przypisane do delegata, który ma niezgodny podpis. Na przykład w poniższym kodzie delegat `Del` ma dwa parametry Integer.

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

Błąd jest wywoływany, jeśli wyrażenie lambda z jednym argumentem jest zadeklarowane jako typ `Del`:

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

**Identyfikator błędu:** BC36532

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Dostosuj definicję delegata lub przypisane wyrażenie lambda, aby podpisy były zgodne.

## <a name="see-also"></a>Zobacz także

- [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
