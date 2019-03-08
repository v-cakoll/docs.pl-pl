---
title: Korzystanie z wariancji w Delegatach (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: 19eb3070c1b8359a4eb050e7cf2f16622f66ebe9
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679798"
---
# <a name="using-variance-in-delegates-visual-basic"></a>Korzystanie z wariancji w Delegatach (Visual Basic)

Po przypisaniu metody z delegatem, *Kowariancja* i *kontrawariancja* zapewniają elastyczność dopasowanie typu delegata z podpis metody. Kowariancja zezwala na metodę, aby zwracany typ, który jest bardziej pochodnego niż zdefiniowanymi dla delegata. Kontrawariancja umożliwia metody, która ma typy parametrów, które są mniej pochodnego niż typ delegata.

## <a name="example-1-covariance"></a>Przykład 1: Kowariancja

### <a name="description"></a>Opis

W tym przykładzie pokazano, jak można używać delegatów za pomocą metod, które mają zwracane typy, które są uzyskiwane ze zwracanego typu w podpisie delegata. Typ danych zwracanych przez `DogsHandler` typu `Dogs`, która pochodzi od klasy `Mammals` typu, który jest zdefiniowany w delegacie.

### <a name="code"></a>Kod

```vb
Class Mammals
End Class

Class Dogs
    Inherits Mammals
End Class
Class Test
    Public Delegate Function HandlerMethod() As Mammals
    Public Shared Function MammalsHandler() As Mammals
        Return Nothing
    End Function
    Public Shared Function DogsHandler() As Dogs
        Return Nothing
    End Function
    Sub Test()
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler
        ' Covariance enables this assignment.
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler
    End Sub
End Class
```

## <a name="example-2-contravariance"></a>Przykład 2: Kontrawariancja

### <a name="description"></a>Opis

W tym przykładzie pokazano, jak można używać delegatów za pomocą metody, które mają parametry typu, które typy podstawowe typu parametru podpis delegata. Za pomocą kontrawariancja możesz użyć jednego programu obsługi zdarzeń zamiast oddzielnych programów obsługi. Na przykład można utworzyć program obsługi zdarzeń, który akceptuje `EventArgs` parametr wejściowy i korzystać z niego przy użyciu `Button.MouseClick` zdarzenia, które wysyła `MouseEventArgs` typu jako parametru, a także z `TextBox.KeyDown` zdarzenia, które wysyła `KeyEventArgs` parametru.

### <a name="code"></a>Kod

```vb
' Event handler that accepts a parameter of the EventArgs type.
Private Sub MultiHandler(ByVal sender As Object,
                         ByVal e As System.EventArgs)
    Label1.Text = DateTime.Now
End Sub

Private Sub Form1_Load(ByVal sender As System.Object,
    ByVal e As System.EventArgs) Handles MyBase.Load

    ' You can use a method that has an EventArgs parameter,
    ' although the event expects the KeyEventArgs parameter.
    AddHandler Button1.KeyDown, AddressOf MultiHandler

    ' You can use the same method
    ' for the event that expects the MouseEventArgs parameter.
    AddHandler Button1.MouseClick, AddressOf MultiHandler
End Sub
```

## <a name="see-also"></a>Zobacz także

- [Wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Korzystanie z wariancji dla Func i akcji delegatów ogólnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
