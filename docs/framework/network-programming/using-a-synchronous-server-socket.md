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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047034"
---
# <a name="using-a-synchronous-server-socket"></a>Używanie synchronicznego gniazda serwera
Synchroniczne gniazda serwera zawieszają wykonywanie aplikacji do momentu odebrania żądania połączenia na gnieździe. Synchroniczne gniazda serwerów nie są odpowiednie dla aplikacji, które intensywnie korzystają z sieci podczas ich działania, ale mogą być odpowiednie do prostych aplikacji sieciowych.  
  
 Po <xref:System.Net.Sockets.Socket> a jest ustawiona do nasłuchiwania w punkcie końcowym przy użyciu <xref:System.Net.Sockets.Socket.Bind%2A> i <xref:System.Net.Sockets.Socket.Listen%2A> metody, jest gotowy do akceptowania żądań połączeń przychodzących przy użyciu <xref:System.Net.Sockets.Socket.Accept%2A> metody. Aplikacja jest zawieszona do momentu odebraniem żądania połączenia, gdy wywoływana jest metoda **Accept.**  
  
 Po odebraniu żądania **połączenia, Zaakceptuj** zwraca nowe **wystąpienie Socket,** które jest skojarzone z klientem łączącym. Poniższy przykład odczytuje dane z klienta, wyświetla go na konsoli i echa danych z powrotem do klienta. **Socket** nie określa żadnego protokołu obsługi\<wiadomości, więc ciąg "EOF>" oznacza koniec danych wiadomości. Przyjęto założenie, **Socket** że `listener` Socket nazwie został zainicjowany i powiązany z punktem końcowym.  
  
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

- [Używanie asynchronicznego gniazda serwera](using-an-asynchronous-server-socket.md)
- [Przykład synchronicznego gniazda serwera](synchronous-server-socket-example.md)
- [Nasłuchiwanie przy użyciu gniazd](listening-with-sockets.md)
