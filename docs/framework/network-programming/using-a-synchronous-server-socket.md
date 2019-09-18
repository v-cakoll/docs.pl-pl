---
title: Używanie synchronicznego gniazda serwera
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
ms.openlocfilehash: cbc02c755ceefa8f31439f121a98978b82f33fa2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047034"
---
# <a name="using-a-synchronous-server-socket"></a>Używanie synchronicznego gniazda serwera
Synchroniczne gniazda serwera zawieszają wykonywanie aplikacji do momentu odebrania żądania połączenia w gnieździe. Synchroniczne gniazda serwera nie są odpowiednie dla aplikacji, które wykorzystują intensywną eksploatację sieci, ale mogą być odpowiednie dla prostych aplikacji sieciowych.  
  
 Gdy jest ustawiony do nasłuchiwania na punkcie końcowym <xref:System.Net.Sockets.Socket.Bind%2A> przy <xref:System.Net.Sockets.Socket.Listen%2A> użyciu metod i, jest <xref:System.Net.Sockets.Socket.Accept%2A> gotowy do akceptowania przychodzących żądań połączeń przy użyciu metody. <xref:System.Net.Sockets.Socket> Aplikacja jest wstrzymana do momentu odebrania żądania połączenia w przypadku wywołania metody **Accept** .  
  
 Po odebraniu żądania połączenia **Zaakceptuj** zwraca nowe wystąpienie **gniazda** skojarzone z klientem nawiązującym połączenie. Poniższy przykład odczytuje dane z klienta programu, wyświetla go w konsoli programu i zwraca dane z powrotem do klienta. **Gniazdo** nie określa żadnego protokołu obsługi komunikatów, dlatego ciąg "\<EOF >" oznacza koniec danych komunikatu. Przyjęto założenie , że `listener` gniazdo o nazwie zostało zainicjowane i powiązane z punktem końcowym.  
  
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
