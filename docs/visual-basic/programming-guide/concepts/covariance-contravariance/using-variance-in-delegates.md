---
title: Korzystanie z wariancji w delegatach (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: ebba7e862e1b4677d9438aa301ef2b713fba3712
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169067"
---
# <a name="using-variance-in-delegates-visual-basic"></a>Korzystanie z wariancji w delegatach (Visual Basic)

Podczas przypisywania metody do delegata, *Kowariancja* i *kontrawariancja* zapewniają elastyczność dla dopasowania typu delegata z sygnaturą metody. Kowariancja zezwala metodzie na typ zwracany, który jest bardziej pochodny niż zdefiniowany w delegatze. Kontrawariancja zezwala na metodę, która ma typy parametrów, które są mniej pochodne niż te w typie delegata.

## <a name="example-1-covariance"></a>Przykład 1: Kowariancja

### <a name="description"></a>Opis

Ten przykład pokazuje, jak obiekty delegowane mogą być używane z metodami, które mają typy zwracane, które pochodzą z typu zwracanego w sygnaturze delegata. Typ danych zwracanych przez `DogsHandler` element jest typu `Dogs` `Mammals` , który pochodzi od typu, który jest zdefiniowany w delegacie.

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

W tym przykładzie pokazano, jak obiekty delegowane mogą być używane z metodami, które mają parametry, których typy są typami podstawowymi typu parametru podpisu delegata. Za pomocą kontrawariancja można użyć jednego programu obsługi zdarzeń zamiast oddzielnych programów obsługi. W poniższym przykładzie użyto dwóch delegatów:

- Delegat definiujący podpis zdarzenia [Button. KeyDown.](xref:System.Windows.Forms.Control.KeyDown) <xref:System.Windows.Forms.KeyEventHandler> Podpis jest:

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- Delegat definiujący sygnaturę zdarzenia [Button. MouseClick.](xref:System.Windows.Forms.Control.MouseDown) <xref:System.Windows.Forms.MouseEventHandler> Podpis jest:

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

W przykładzie zdefiniowano procedurę obsługi zdarzeń z <xref:System.EventArgs> parametrem i używa jej do obsługi `Button.KeyDown` zarówno zdarzenia `Button.MouseClick` , jak i. Można to zrobić, ponieważ <xref:System.EventArgs> jest typem podstawowym obu <xref:System.Windows.Forms.KeyEventArgs> i <xref:System.Windows.Forms.MouseEventArgs>.

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

- [Wariancja w delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Korzystanie z wariancji dla delegatów "Func" i "Action Generic" (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
