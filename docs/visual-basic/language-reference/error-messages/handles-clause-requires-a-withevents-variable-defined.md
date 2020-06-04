---
title: Klauzula Handles wymaga zmiennej WithEvents zdefiniowanej w zawierającym ją typie lub jednym z jej typów podstawowych
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 94c4229d4036382e344cffb09295e218642c55d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402904"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>Klauzula Handles wymaga zmiennej WithEvents zdefiniowanej w zawierającym ją typie lub jednym z jej typów podstawowych

W klauzuli nie podano `WithEvents` zmiennej `Handles` . `Handles`Słowo kluczowe na końcu deklaracji procedury powoduje obsługę zdarzeń wywoływanych przez zmienną obiektu zadeklarowaną za pomocą `WithEvents` słowa kluczowego.

**Identyfikator błędu:** BC30506

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Podaj wymaganą `WithEvents` zmienną.

## <a name="example"></a>Przykład

W poniższym przykładzie Visual Basic generuje błąd kompilatora, `BC30506` ponieważ słowo kluczowe [WithEvents](../modifiers/withevents.md) nie jest używane w definicji <xref:System.Timers.Timer?displayProperty=nameWithType> wystąpienia.

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

Poniższy przykład kompiluje się pomyślnie, ponieważ `_timer1` zmienna jest zdefiniowana za pomocą `WithEvents` słowa kluczowego:

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

## <a name="see-also"></a>Zobacz też

- [Handles](../statements/handles-clause.md)
