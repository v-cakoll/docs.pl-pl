---
title: Wyrażenie jest wartością i dlatego nie może być elementem docelowym przypisania
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 9e4dbaf2f2800454c673cd58ddec4cf0f6e5c6b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409511"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Wyrażenie jest wartością i dlatego nie może być elementem docelowym przypisania

Instrukcja próbuje przypisać wartość do wyrażenia. Można przypisać wartość tylko do zapisywalnej zmiennej, właściwości lub elementu tablicy w czasie wykonywania. Poniższy przykład ilustruje, jak ten błąd może wystąpić.

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

Podobne przykłady mogą dotyczyć właściwości i elementów tablicy.

**Dostęp pośredni.** Bezpośredni dostęp za pomocą typu wartości może również generować ten błąd. Rozważmy następujący przykład kodu, który podejmuje próbę ustawienia wartości <xref:System.Drawing.Point> przez uzyskanie dostępu do niej pośrednio za pomocą <xref:System.Windows.Forms.Control.Location%2A> .

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

Ostatnia instrukcja w powyższym przykładzie kończy się niepowodzeniem, ponieważ powoduje utworzenie tylko tymczasowej alokacji dla <xref:System.Drawing.Point> struktury zwróconej przez <xref:System.Windows.Forms.Control.Location%2A> Właściwość. Struktura jest typem wartości, a tymczasowa struktura nie jest zachowywana po uruchomieniu instrukcji. Problem został rozwiązany przez zadeklarowanie i użycie zmiennej dla <xref:System.Windows.Forms.Control.Location%2A> , co powoduje utworzenie bardziej trwałego przydziału dla <xref:System.Drawing.Point> struktury. Poniższy przykład pokazuje kod, który może zastąpić ostatnią instrukcję z poprzedniego przykładu.

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

**Identyfikator błędu:** BC30068

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Jeśli instrukcja przypisuje wartość do wyrażenia, zastąp wyrażenie pojedynczym zapisywalną zmienną, właściwością lub elementem tablicy.

- Jeśli instrukcja wykonuje pośredni dostęp za pomocą typu wartości (zazwyczaj struktury), Utwórz zmienną do przechowywania typu wartości.

- Przypisz odpowiednią strukturę (lub inny typ wartości) do zmiennej.

- Użyj zmiennej, aby uzyskać dostęp do właściwości w celu przypisania jej wartości.

## <a name="see-also"></a>Zobacz też

- [Operatory i wyrażenia](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Instrukcje](../../programming-guide/language-features/statements.md)
- [Rozwiązywanie problemów z procedurami](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
