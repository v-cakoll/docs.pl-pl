---
title: Klauzula Handles wymaga zmiennej WithEvents zdefiniowanej w zawierającym ją typie lub jednym z jej typów podstawowych
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 191415408f607d0ff768e50c41fa9b3c4405a688
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582824"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>Klauzula Handles wymaga zmiennej WithEvents zdefiniowanej w zawierającym ją typie lub jednym z jej typów podstawowych

W klauzuli `Handles` nie podano zmiennej `WithEvents`. Słowo kluczowe `Handles` na końcu deklaracji procedury powoduje obsługę zdarzeń wywoływanych przez zmienną obiektu zadeklarowaną za pomocą słowa kluczowego `WithEvents`.

**Identyfikator błędu:** BC30506

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Podaj niezbędną zmienną `WithEvents`.

## <a name="example"></a>Przykład

W poniższym przykładzie Visual Basic generuje błąd kompilatora `BC30506`, ponieważ słowo kluczowe [WithEvents](../modifiers/withevents.md) nie jest używane w definicji wystąpienia <xref:System.Timers.Timer?displayProperty=nameWithType>.

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

Poniższy przykład kompiluje się pomyślnie, ponieważ zmienna `_timer1` jest zdefiniowana za pomocą słowa kluczowego `WithEvents`:

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

- [Realizuj](../../../visual-basic/language-reference/statements/handles-clause.md)
