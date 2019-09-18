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
# <a name="using-a-synchronous-server-socket"></a><span data-ttu-id="d6af4-102">Używanie synchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="d6af4-102">Using a Synchronous Server Socket</span></span>
<span data-ttu-id="d6af4-103">Synchroniczne gniazda serwera zawieszają wykonywanie aplikacji do momentu odebrania żądania połączenia w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="d6af4-103">Synchronous server sockets suspend the execution of the application until a connection request is received on the socket.</span></span> <span data-ttu-id="d6af4-104">Synchroniczne gniazda serwera nie są odpowiednie dla aplikacji, które wykorzystują intensywną eksploatację sieci, ale mogą być odpowiednie dla prostych aplikacji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="d6af4-104">Synchronous server sockets are not suitable for applications that make heavy use of the network in their operation, but they can be suitable for simple network applications.</span></span>  
  
 <span data-ttu-id="d6af4-105">Gdy jest ustawiony do nasłuchiwania na punkcie końcowym <xref:System.Net.Sockets.Socket.Bind%2A> przy <xref:System.Net.Sockets.Socket.Listen%2A> użyciu metod i, jest <xref:System.Net.Sockets.Socket.Accept%2A> gotowy do akceptowania przychodzących żądań połączeń przy użyciu metody. <xref:System.Net.Sockets.Socket></span><span class="sxs-lookup"><span data-stu-id="d6af4-105">After a <xref:System.Net.Sockets.Socket> is set to listen on an endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> and <xref:System.Net.Sockets.Socket.Listen%2A> methods, it is ready to accept incoming connection requests using the <xref:System.Net.Sockets.Socket.Accept%2A> method.</span></span> <span data-ttu-id="d6af4-106">Aplikacja jest wstrzymana do momentu odebrania żądania połączenia w przypadku wywołania metody **Accept** .</span><span class="sxs-lookup"><span data-stu-id="d6af4-106">The application is suspended until a connection request is received when the **Accept** method is called.</span></span>  
  
 <span data-ttu-id="d6af4-107">Po odebraniu żądania połączenia **Zaakceptuj** zwraca nowe wystąpienie **gniazda** skojarzone z klientem nawiązującym połączenie.</span><span class="sxs-lookup"><span data-stu-id="d6af4-107">When a connection request is received, **Accept** returns a new **Socket** instance that is associated with the connecting client.</span></span> <span data-ttu-id="d6af4-108">Poniższy przykład odczytuje dane z klienta programu, wyświetla go w konsoli programu i zwraca dane z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="d6af4-108">The following example reads data from the client, displays it on the console, and echoes the data back to the client.</span></span> <span data-ttu-id="d6af4-109">**Gniazdo** nie określa żadnego protokołu obsługi komunikatów, dlatego ciąg "\<EOF >" oznacza koniec danych komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d6af4-109">The **Socket** does not specify any messaging protocol, so the string "\<EOF>" marks the end of the message data.</span></span> <span data-ttu-id="d6af4-110">Przyjęto założenie , że `listener` gniazdo o nazwie zostało zainicjowane i powiązane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="d6af4-110">It assumes that a **Socket** named `listener` has been initialized and bound to an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6af4-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6af4-111">See also</span></span>

- [<span data-ttu-id="d6af4-112">Używanie asynchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="d6af4-112">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="d6af4-113">Przykład synchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="d6af4-113">Synchronous Server Socket Example</span></span>](synchronous-server-socket-example.md)
- [<span data-ttu-id="d6af4-114">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="d6af4-114">Listening with Sockets</span></span>](listening-with-sockets.md)
