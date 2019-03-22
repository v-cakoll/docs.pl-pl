---
title: Operatory warunkowe null (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: b83435b8448b53eca63aac0519e9eed2f7dfa9f3
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348768"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. i? Operatory warunkowe null () (Visual Basic)

Sprawdza wartość operandu po lewej stronie w przypadku wartości null (`Nothing`) przed wykonaniem dostęp do elementu członkowskiego (`?.`) lub indeksu (`?()`) operacja; zwraca `Nothing` Jeśli po lewej stronie operand ma wartość `Nothing`. Należy pamiętać, że w wyrażeniach, które normalnie zwracane typy wartości, operatorów warunkowych działających z wartością null zwraca <xref:System.Nullable%601>.

Te operatory pomóc w pisaniu mniejszej ilości kodu do obsługi sprawdzanie wartości null, szczególnie w przypadku, gdy malejąco do struktur danych. Na przykład:

```vb
' Nothing if customers is Nothing  
Dim length As Integer? = customers?.Length  

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()   
```

Dla porównania alternatywnych kod dla pierwszego dnia te wyrażenia bez operatorów warunkowych działających z wartością null jest:

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Operatory warunkowe `null` skracają łańcuch wykonywania operacji.  Jeśli jedna operacja w łańcuchu operacji dostępu i indeks warunkowa składowa zwraca `Nothing`, pozostała część zatrzymuje wykonywanie łańcucha.  W poniższym przykładzie `C(E)` nie jest oceniany, jeśli `A`, `B`, lub `C` daje w wyniku `Nothing`.

```vb
A?.B?.C?(E);
```

Innym zastosowaniem uzyskać dostęp do elementu członkowskiego warunkowe null jest wywoływać delegatów w sposób wątkowo ze znacznie mniejszej ilości kodu.  W poniższym przykładzie zdefiniowano dwa typy `NewsBroadcaster` i `NewsReceiver`. Elementy wiadomości są wysyłane do odbiorcy przez `NewsBroadcaster.SendNews` delegować.

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

Jeśli nie ma elementów w `SendNews` listy wywołań `SendNews` delegować zgłasza <xref:System.NullReferenceException>. Przed operatory warunkowe null, kod tak, jak zapewnić następujące listy wywołanie delegata nie była `Nothing`:

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

Nowy sposób jest bezpieczny wątkowo, ponieważ kompilator generuje kod, aby sprawdzić stan `SendNews` tylko jeden raz, a następnie zapisuje wynik w zmiennej tymczasowej. Metodę `Invoke`trzeba wywołać jawnie, ponieważ nie istnieje składnia `SendNews?(String)` do wywołania delegata przy użyciu operatora warunkowego „null”.  

## <a name="see-also"></a>Zobacz także

- [Operatory (Visual Basic)](index.md)
- [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)
- [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)
