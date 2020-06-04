---
title: Operatory warunkowe null
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: bffbba859968e0a050397cd9e685c142f801798a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401475"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. lub? () operatory warunkowe o wartości null (Visual Basic)

Testuje wartość operandu po lewej stronie dla wartości null ( `Nothing` ) przed wykonaniem operacji dostępu do elementu członkowskiego ( `?.` ) lub indeksu ( `?()` ); zwraca wartość, `Nothing` Jeśli argument operacji po lewej stronie ma wartość `Nothing` . Należy zauważyć, że w wyrażeniach, które zwykle zwracają typy wartości, operator warunkowy o wartości null zwraca wartość <xref:System.Nullable%601> .

Te operatory ułatwiają pisanie mniejszego kodu do obsługi kontroli wartości null, szczególnie w przypadku malejących struktur danych. Przykład:

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

Operatory warunkowe o wartości null są krótkimi obwodami.  Jeśli jedna operacja w łańcuchu warunkowego dostępu do elementu członkowskiego i operacji indeksu zostanie zwrócona `Nothing` , pozostała część wykonania łańcucha zostanie zatrzymana.  W poniższym przykładzie `C(E)` nie jest oceniana, `A` Jeśli `B` ,, lub `C` jest wynikiem `Nothing` .

```vb
A?.B?.C?(E)
```

Innym zastosowaniem dostępu do składowych o wartości null jest wywoływanie delegatów w sposób bezpieczny dla wątków z znacznie mniejszym kodem.  W poniższym przykładzie zdefiniowano dwa typy, `NewsBroadcaster` a i `NewsReceiver` . Elementy wiadomości są wysyłane do odbiorcy przez `NewsBroadcaster.SendNews` delegata.

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

Jeśli na liście wywołań nie ma elementów `SendNews` , `SendNews` Delegat zgłosi <xref:System.NullReferenceException> . Przed operatorami warunkowymi null, kod podobny do poniższego upewnienia się, że lista wywołań delegata nie była `Nothing` :

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

Nowy sposób jest bezpieczny wątkowo, ponieważ kompilator generuje kod do oszacowania `SendNews` tylko jeden raz, utrzymując wynik w zmiennej tymczasowej. Należy jawnie wywołać `Invoke` metodę, ponieważ nie istnieje składnia niewarunkowego delegata o wartości null `SendNews?(String)` .

## <a name="see-also"></a>Zobacz też

- [Operatory (Visual Basic)](index.md)
- [Przewodnik programowania w Visual Basic](../../programming-guide/index.md)
- [Dokumentacja języka Visual Basic](../index.md)
