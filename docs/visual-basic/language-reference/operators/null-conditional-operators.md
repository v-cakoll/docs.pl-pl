---
title: Operatory warunkowe o wartości null
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: 003f579a7128bbe2462b7fbe7057de03e61bfbe6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348288"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. lub? () operatory warunkowe o wartości null (Visual Basic)

Testuje wartość operandu po lewej stronie dla wartości null (`Nothing`) przed wykonaniem operacji dostępu do elementu członkowskiego (`?.`) lub indeksu (`?()`). zwraca `Nothing`, jeśli argument operacji po lewej stronie szacuje się na `Nothing`. Należy zauważyć, że w wyrażeniach, które zwykle zwracają typy wartości, operator warunkowy NULL zwraca <xref:System.Nullable%601>.

Te operatory ułatwiają pisanie mniejszego kodu do obsługi kontroli wartości null, szczególnie w przypadku malejących struktur danych. Na przykład:

```vb
' Nothing if customers is Nothing
Dim length As Integer? = customers?.Length

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()
```

W celu porównania kod alternatywny dla pierwszego z tych wyrażeń bez operatora warunkowego null jest następujący:

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Czasami trzeba wykonać akcję na obiekcie, który może mieć wartość null, na podstawie wartości logicznej składowej tego obiektu (podobnie jak właściwość logiczna `IsAllowedFreeShipping` w poniższym przykładzie):

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
  ApplyFreeShippingToOrders(customer)
End If
```

Możesz skrócić swój kod i unikać ręcznego sprawdzania wartości null przy użyciu operatora warunkowego null w następujący sposób:

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

Operatory warunkowe `null` skracają łańcuch wykonywania operacji.  Jeśli jedna operacja w łańcuchu warunkowych operacji dostępu i indeksowania zwraca `Nothing`, pozostała część wykonania łańcucha zostanie zatrzymana.  W poniższym przykładzie `C(E)` nie jest oceniane, jeśli `A`, `B`lub `C` szacuje się na `Nothing`.

```vb
A?.B?.C?(E)
```

Innym zastosowaniem dostępu do składowych o wartości null jest wywoływanie delegatów w sposób bezpieczny dla wątków z znacznie mniejszym kodem.  W poniższym przykładzie zdefiniowano dwa typy, `NewsBroadcaster` i `NewsReceiver`. Elementy wiadomości są wysyłane do odbiorcy przez delegata `NewsBroadcaster.SendNews`.

```vb
Public Module NewsBroadcaster
   Dim SendNews As Action(Of String)

   Public Sub Main()
      Dim rec As New NewsReceiver()
      Dim rec2 As New NewsReceiver()
      SendNews?.Invoke("Just in: A newsworthy item...")
   End Sub

   Public Sub Register(client As Action(Of String))
      SendNews = SendNews.Combine({SendNews, client})
   End Sub
End Module

Public Class NewsReceiver
   Public Sub New()
      NewsBroadcaster.Register(AddressOf Me.DisplayNews)
   End Sub

   Public Sub DisplayNews(newsItem As String)
      Console.WriteLine(newsItem)
   End Sub
End Class
```

Jeśli na liście wywołań `SendNews` nie ma elementów, delegat `SendNews` zgłosi <xref:System.NullReferenceException>. Przed operatorami warunkowymi null, kod podobny do poniższego upewnił się, że lista wywołań delegata nie została `Nothing`:

```vb
SendNews = SendNews.Combine({SendNews, client})
If SendNews IsNot Nothing Then
   SendNews("Just in...")
End If
```

Nowy sposób jest znacznie prostszy:

```vb
SendNews = SendNews.Combine({SendNews, client})
SendNews?.Invoke("Just in...")
```

Nowy sposób jest bezpieczny wątkowo, ponieważ kompilator generuje kod służący do oszacowania `SendNews` tylko jeden raz, utrzymując wynik w zmiennej tymczasowej. Należy jawnie wywołać metodę `Invoke`, ponieważ nie istnieje składnia wywołania delegata warunkowego o wartości null `SendNews?(String)`.

## <a name="see-also"></a>Zobacz także

- [Operatory (Visual Basic)](index.md)
- [Przewodnik programowania Visual Basic](../../../visual-basic/programming-guide/index.md)
- [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)
