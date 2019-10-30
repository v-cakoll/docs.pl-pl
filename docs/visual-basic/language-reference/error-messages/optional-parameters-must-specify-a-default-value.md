---
title: Parametry opcjonalne muszą określać wartość domyślną
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: eb782b2fa1fb73c7407b57a0942e5eebb30474ff
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040931"
---
# <a name="optional-parameters-must-specify-a-default-value"></a>Parametry opcjonalne muszą określać wartość domyślną

Parametry opcjonalne muszą podawać wartości domyślne, których można użyć, jeśli żaden parametr nie jest dostarczany przez procedurę wywołującą.

**Identyfikator błędu:** BC30812

## <a name="example"></a>Przykład

Poniższy przykład generuje BC30812:

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Określ wartości domyślne dla parametrów opcjonalnych:

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a>Zobacz także

- [Optional](../modifiers/optional.md)
