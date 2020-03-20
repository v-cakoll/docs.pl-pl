---
title: Używanie synchronicznego gniazda klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- synchronous client sockets
- Socket class, synchronous client sockets
- receiving data, sockets
- sockets, synchronous client sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
ms.openlocfilehash: fdecd18dc5975cd469e49de0eb0b55081e738cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047074"
---
# <a name="using-a-synchronous-client-socket"></a>Używanie synchronicznego gniazda klienta
Synchroniczne gniazdo klienta zawiesza program aplikacji po zakończeniu operacji sieciowej. Gniazda synchroniczne nie są odpowiednie dla aplikacji, które intensywnie korzystają z sieci do ich działania, ale mogą umożliwić prosty dostęp do usług sieciowych dla innych aplikacji.  
  
 Aby wysłać dane, przekaż tablicę <xref:System.Net.Sockets.Socket> bajtów do jednej<xref:System.Net.Sockets.Socket.Send%2A> z <xref:System.Net.Sockets.Socket.SendTo%2A>metod wysyłania danych klasy ( i ). Poniższy przykład koduje ciąg do buforu tablicy bajtów przy użyciu <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> właściwości, a następnie przesyła bufor do urządzenia sieciowego przy użyciu **Send** metody. Send **Send** Metoda zwraca liczbę bajtów wysłanych do urządzenia sieciowego.  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 **Send** Metoda usuwa bajty z buforu i kolejkuje je z interfejsem sieciowym, które mają być wysyłane do urządzenia sieciowego. Interfejs sieciowy może nie wysłać danych natychmiast, ale wyśle je ostatecznie, tak długo, jak połączenie jest zamknięte normalnie z <xref:System.Net.Sockets.Socket.Shutdown%2A> metodą.  
  
 Aby odbierać dane z urządzenia sieciowego, należy przekazać bufor do jednej<xref:System.Net.Sockets.Socket.Receive%2A> <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>z metod odbierania danych klasy **Socket** ( i ). Gniazda synchroniczne zawieszają aplikację do momentu odebraniem bajtów z sieci lub do momentu zamknięcia gniazda. Poniższy przykład odbiera dane z sieci, a następnie wyświetla je na konsoli. W przykładzie przyjęto założenie, że dane pochodzące z sieci są tekstem zakodowanym w ascii. Receive **Receive** Metoda zwraca liczbę bajtów odebranych z sieci.  
  
```vb  
Dim bytes(1024) As Byte  
Dim bytesRec = s.Receive(bytes)  
Console.WriteLine("Echoed text = {0}", _  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec))  
```  
  
```csharp  
byte[] bytes = new byte[1024];  
int bytesRec = s.Receive(bytes);  
Console.WriteLine("Echoed text = {0}",  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec));  
```  
  
 Gdy gniazdo nie jest już potrzebne, należy go <xref:System.Net.Sockets.Socket.Shutdown%2A> zwolnić, wywołując metodę, a następnie wywołując **Close** metody. Poniższy przykład zwalnia **Socket**. Wyliczenie <xref:System.Net.Sockets.SocketShutdown> definiuje stałe, które wskazują, czy gniazdo powinno być zamknięte do wysyłania, odbierania lub dla obu.  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a>Zobacz też

- [Używanie asynchronicznego gniazda klienta](using-an-asynchronous-client-socket.md)
- [Nasłuchiwanie przy użyciu gniazd](listening-with-sockets.md)
- [Przykład synchronicznego gniazda klienta](synchronous-client-socket-example.md)
