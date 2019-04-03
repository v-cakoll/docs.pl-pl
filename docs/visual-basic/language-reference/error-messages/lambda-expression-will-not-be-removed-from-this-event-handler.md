---
title: Wyrażenie lambda nie zostanie usunięte z tej obsługi zdarzeń
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 20e83306925e91e579aca52f2e7c209c8c686dee
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817618"
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a>Wyrażenie lambda nie zostanie usunięte z tej obsługi zdarzeń
Wyrażenie lambda nie zostanie usunięte z tej obsługi zdarzeń. Przypisz wyrażenia lambda do zmiennej i użycia zmiennej w celu dodawania i usuwania zdarzenia.  
  
 Gdy wyrażenia lambda są używane z programami obsługi zdarzeń, może być niewidoczna zachowania, których oczekujesz. Kompilator generuje nową metodę dla każdej definicji wyrażenia lambda, nawet jeśli te wartości są identyczne. W związku z tym, poniższy kod wyświetla `False`.  
  
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
  
 Jeśli wyrażenia lambda są używane z programami obsługi zdarzeń, może to spowodować nieoczekiwane wyniki. W poniższym przykładzie, wyrażenie lambda dodane przez `AddHandler` nie został usunięty przez `RemoveHandler` instrukcji.  
  
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
  
 Domyślnie ta wiadomość jest ostrzeżenie. Aby uzyskać więcej informacji na temat Ukryj ostrzeżenia lub Traktuj ostrzeżenia jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42326  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Aby uniknąć ostrzeżenia i Usuń Wyrażenie lambda, przypisz wyrażenia lambda do zmiennej i użycia zmiennej w obu `AddHandler` i `RemoveHandler` instrukcje, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
