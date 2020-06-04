---
title: Wyrażenie lambda nie zostanie usunięte z tej obsługi zdarzeń
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 07ace3f1b9c5e512227dc1f718ef768b631c8303
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397379"
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a>Wyrażenie lambda nie zostanie usunięte z tej obsługi zdarzeń

Wyrażenie lambda nie zostanie usunięte z tej procedury obsługi zdarzeń. Przypisz wyrażenie lambda do zmiennej i Użyj zmiennej, aby dodać i usunąć zdarzenie.

Gdy wyrażenia lambda są używane z obsługą zdarzeń, może nie być widoczne oczekiwane zachowanie. Kompilator generuje nową metodę dla każdej definicji wyrażenia lambda, nawet jeśli są identyczne. W związku z tym Poniższy kod wyświetla `False` .

```vb
Module Module1

    Sub Main()
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1
        Console.WriteLine(fun1 = fun2)
    End Sub

    Delegate Function ChangeInteger(ByVal x As Integer) As Integer

End Module
```

Gdy wyrażenia lambda są używane z obsługą zdarzeń, może to spowodować nieoczekiwane wyniki. W poniższym przykładzie wyrażenie lambda dodane przez `AddHandler` nie jest usuwane przez `RemoveHandler` instrukcję.

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Sub Main()

        ' The following line adds one listener to the event.
        AddHandler ProcessInteger, Function(m As Integer) m

        ' The following statement searches the current listeners
        ' for a match to remove. However, this lambda is not the same
        ' as the previous one, so nothing is removed.
        RemoveHandler ProcessInteger, Function(m As Integer) m

    End Sub
End Module
```

Domyślnie ten komunikat jest ostrzeżeniem. Aby uzyskać więcej informacji na temat sposobu ukrywania ostrzeżeń lub traktowania ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

**Identyfikator błędu:** BC42326

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Aby uniknąć ostrzeżenia i usunąć wyrażenie lambda, przypisz wyrażenie lambda do zmiennej i Użyj zmiennej w obu `AddHandler` `RemoveHandler` instrukcjach i, jak pokazano w poniższym przykładzie.

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Dim PrintHandler As ProcessIntegerEventHandler

    Sub Main()

        ' Assign the lambda expression to a variable.
        PrintHandler = Function(m As Integer) m

        ' Use the variable to add the listener.
        AddHandler ProcessInteger, PrintHandler

        ' Use the variable again when you want to remove the listener.
        RemoveHandler ProcessInteger, PrintHandler

    End Sub
End Module
```

## <a name="see-also"></a>Zobacz też

- [Wyrażenia lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [Swobodna konwersja delegatów](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Zdarzenia](../../programming-guide/language-features/events/index.md)
