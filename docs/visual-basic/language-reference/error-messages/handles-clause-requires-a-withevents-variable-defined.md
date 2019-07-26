---
title: Klauzula Handles wymaga zmiennej WithEvents zdefiniowanej w zawierającym ją typie lub jednym z jej typów podstawowych
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 04c94d3d32660d1a186a9bb377c49a53e1451be6
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512732"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>Klauzula Handles wymaga zmiennej WithEvents zdefiniowanej w zawierającym ją typie lub jednym z jej typów podstawowych
W klauzuli nie podano `WithEvents`zmiennej `Handles` . Słowo kluczowe na końcu deklaracji procedury powoduje obsługę zdarzeń wywoływanych przez zmienną obiektu zadeklarowaną `WithEvents` za pomocą słowa kluczowego. `Handles`
  
 **Identyfikator błędu:** BC30506

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd
  
- Podaj wymaganą `WithEvents` zmienną.
  
## <a name="example"></a>Przykład

W poniższym przykładzie Visual Basic generuje błąd `BC30506` kompilatora, ponieważ słowo kluczowe [WithEvents](../modifiers/withevents.md) nie jest używane w definicji <xref:System.Timers.Timer?displayProperty=nameWithType> wystąpienia.

```vb
Imports System.Timers

Module Module1
    Private _timer1 As New Timer() With {.Interval = 1000, .Enabled = True}
    
    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub
End Module
```

Poniższy przykład kompiluje się pomyślnie, ponieważ `_timer1` zmienna jest zdefiniowana `WithEvents` za pomocą słowa kluczowego:

```vb
Imports System.Timers

Module Module1
    Private WithEvents _timer1 As New Timer() With {.Interval = 1000}

    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub

End Module
```

## <a name="see-also"></a>Zobacz także

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
