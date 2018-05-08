---
title: Przy użyciu gniazda synchroniczne serwera
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4f04255edf9533612dd6b0733331fb18587ff3f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-synchronous-server-socket"></a>Przy użyciu gniazda synchroniczne serwera
Gniazda serwera synchroniczne zawiesić wykonanie aplikacji do momentu otrzymania żądania połączenia w gnieździe. Gniazda serwera synchroniczne nie są odpowiednie dla aplikacji, które są w ich operacji w znacznym stopniu wykorzystywane sieci, ale może być odpowiednie dla aplikacji sieciowych proste.  
  
 Po <xref:System.Net.Sockets.Socket> ustawiono nasłuchiwania punktu końcowego za pomocą <xref:System.Net.Sockets.Socket.Bind%2A> i <xref:System.Net.Sockets.Socket.Listen%2A> metod, jest gotowy do akceptowania żądań połączenia przychodzących za pomocą <xref:System.Net.Sockets.Socket.Accept%2A> metody. Aplikacja jest wstrzymana, dopóki nie zostanie odebrane żądanie połączenia podczas **Akceptuj** metoda jest wywoływana.  
  
 Po odebraniu żądania połączenia **Akceptuj** zwraca nową **gniazda** wystąpienia, który jest skojarzony z klienta nawiązującego połączenie. Poniższy przykład odczytuje dane z klienta, wyświetla go w konsoli i zwraca dane do klienta. **Gniazda** nie określa protokołów obsługi wiadomości, więc ciąg "\<EOF >" oznacza koniec danymi wiadomości. Przy założeniu, że **gniazda** o nazwie `listener` zainicjowany i powiązane z punktem końcowym.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Używanie asynchronicznego gniazda serwera](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Przykład synchronicznego gniazda serwera](../../../docs/framework/network-programming/synchronous-server-socket-example.md)  
 [Nasłuchiwanie przy użyciu gniazd](../../../docs/framework/network-programming/listening-with-sockets.md)
