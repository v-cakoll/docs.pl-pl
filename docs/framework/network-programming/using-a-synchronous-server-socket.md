---
title: Za pomocą synchronicznego gniazda serwera
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- synchronous server sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- Socket class, synchronous server sockets
- protocols, sockets
- sockets, synchronous server sockets
- Internet, sockets
ms.assetid: d1ce882e-653e-41f5-9289-844ec855b804
ms.openlocfilehash: 2a4fd2f903f96a14d4a256ea68240e942ccd59eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614279"
---
# <a name="using-a-synchronous-server-socket"></a>Za pomocą synchronicznego gniazda serwera
Server synchronicznego gniazda zawiesić wykonanie aplikacji, dopóki nie zostanie odebrane żądanie połączenia gniazda. Server synchronicznego gniazda nie są odpowiednie dla aplikacji, które intensywnie korzystają z sieci w ich działania, ale może być odpowiednie dla aplikacji sieciowych proste.  
  
 Po <xref:System.Net.Sockets.Socket> jest ustawiony do nasłuchiwania punktu końcowego za pomocą <xref:System.Net.Sockets.Socket.Bind%2A> i <xref:System.Net.Sockets.Socket.Listen%2A> metod, jest gotowy do akceptowania połączeń przychodzących żądań przy użyciu <xref:System.Net.Sockets.Socket.Accept%2A> metody. Aplikacja jest wstrzymana, dopóki nie zostanie odebrane żądanie połączenia podczas **Akceptuj** metoda jest wywoływana.  
  
 Po odebraniu żądania połączenia **Akceptuj** zwraca nowy **gniazda** wystąpienia, który jest skojarzony z klienta nawiązującego połączenie. Poniższy przykład odczytuje dane z klienta, wyświetla go w konsoli i zwraca dane do klienta. **Gniazda** nie określa protokołów obsługi komunikatów, więc ciąg "\<EOF >" oznacza koniec danych komunikatu. Założono, że **gniazda** o nazwie `listener` zainicjowany i powiązane z punktem końcowym.  
  
```vb  
Console.WriteLine("Waiting for a connection...")  
Dim handler As Socket = listener.Accept()  
Dim data As String = Nothing  
  
While True  
    bytes = New Byte(1024) {}  
    Dim bytesRec As Integer = handler.Receive(bytes)  
    data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
    If data.IndexOf("<EOF>") > - 1 Then  
        Exit While  
    End If  
End While  
  
Console.WriteLine("Text received : {0}", data)  
  
Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
handler.Send(msg)  
handler.Shutdown(SocketShutdown.Both)  
handler.Close()  
```  
  
```csharp  
Console.WriteLine("Waiting for a connection...");  
Socket handler = listener.Accept();  
String data = null;  
  
while (true) {  
    bytes = new byte[1024];  
    int bytesRec = handler.Receive(bytes);  
    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
    if (data.IndexOf("<EOF>") > -1) {  
        break;  
    }  
}  
  
Console.WriteLine( "Text received : {0}", data);  
  
byte[] msg = Encoding.ASCII.GetBytes(data);  
handler.Send(msg);  
handler.Shutdown(SocketShutdown.Both);  
handler.Close();  
```  
  
## <a name="see-also"></a>Zobacz także
- [Używanie asynchronicznego gniazda serwera](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)
- [Przykład synchronicznego gniazda serwera](../../../docs/framework/network-programming/synchronous-server-socket-example.md)
- [Nasłuchiwanie przy użyciu gniazd](../../../docs/framework/network-programming/listening-with-sockets.md)
