---
title: Używanie synchronicznego gniazda serwera
description: Ten przykład przedstawia synchroniczne gniazdo serwera w .NET Framework, które wstrzymuje aplikację do momentu odebrania żądania połączenia w gnieździe.
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
ms.openlocfilehash: 9e7d32595f554b32ecc72bbb1f1a469ad5935467
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502057"
---
# <a name="using-a-synchronous-server-socket"></a>Używanie synchronicznego gniazda serwera
Synchroniczne gniazda serwera zawieszają wykonywanie aplikacji do momentu odebrania żądania połączenia w gnieździe. Synchroniczne gniazda serwera nie są odpowiednie dla aplikacji, które wykorzystują intensywną eksploatację sieci, ale mogą być odpowiednie dla prostych aplikacji sieciowych.  
  
 Gdy <xref:System.Net.Sockets.Socket> jest ustawiony do nasłuchiwania na punkcie końcowym przy użyciu <xref:System.Net.Sockets.Socket.Bind%2A> <xref:System.Net.Sockets.Socket.Listen%2A> metod i, jest gotowy do akceptowania przychodzących żądań połączeń przy użyciu <xref:System.Net.Sockets.Socket.Accept%2A> metody. Aplikacja jest wstrzymana do momentu odebrania żądania połączenia w przypadku wywołania metody **Accept** .  
  
 Po odebraniu żądania połączenia **Zaakceptuj** zwraca nowe wystąpienie **gniazda** skojarzone z klientem nawiązującym połączenie. Poniższy przykład odczytuje dane z klienta programu, wyświetla go w konsoli programu i zwraca dane z powrotem do klienta. **Gniazdo** nie określa żadnego protokołu obsługi komunikatów, więc ciąg " \<EOF> " oznacza koniec danych wiadomości. Przyjęto założenie, że **gniazdo** o nazwie `listener` zostało zainicjowane i powiązane z punktem końcowym.  
  
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

- [Używanie asynchronicznego gniazda serwera](using-an-asynchronous-server-socket.md)
- [Przykład synchronicznego gniazda serwera](synchronous-server-socket-example.md)
- [Nasłuchiwanie przy użyciu gniazd](listening-with-sockets.md)
