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
# <a name="using-a-synchronous-server-socket"></a><span data-ttu-id="db49e-103">Używanie synchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="db49e-103">Using a Synchronous Server Socket</span></span>
<span data-ttu-id="db49e-104">Synchroniczne gniazda serwera zawieszają wykonywanie aplikacji do momentu odebrania żądania połączenia w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="db49e-104">Synchronous server sockets suspend the execution of the application until a connection request is received on the socket.</span></span> <span data-ttu-id="db49e-105">Synchroniczne gniazda serwera nie są odpowiednie dla aplikacji, które wykorzystują intensywną eksploatację sieci, ale mogą być odpowiednie dla prostych aplikacji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="db49e-105">Synchronous server sockets are not suitable for applications that make heavy use of the network in their operation, but they can be suitable for simple network applications.</span></span>  
  
 <span data-ttu-id="db49e-106">Gdy <xref:System.Net.Sockets.Socket> jest ustawiony do nasłuchiwania na punkcie końcowym przy użyciu <xref:System.Net.Sockets.Socket.Bind%2A> <xref:System.Net.Sockets.Socket.Listen%2A> metod i, jest gotowy do akceptowania przychodzących żądań połączeń przy użyciu <xref:System.Net.Sockets.Socket.Accept%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="db49e-106">After a <xref:System.Net.Sockets.Socket> is set to listen on an endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> and <xref:System.Net.Sockets.Socket.Listen%2A> methods, it is ready to accept incoming connection requests using the <xref:System.Net.Sockets.Socket.Accept%2A> method.</span></span> <span data-ttu-id="db49e-107">Aplikacja jest wstrzymana do momentu odebrania żądania połączenia w przypadku wywołania metody **Accept** .</span><span class="sxs-lookup"><span data-stu-id="db49e-107">The application is suspended until a connection request is received when the **Accept** method is called.</span></span>  
  
 <span data-ttu-id="db49e-108">Po odebraniu żądania połączenia **Zaakceptuj** zwraca nowe wystąpienie **gniazda** skojarzone z klientem nawiązującym połączenie.</span><span class="sxs-lookup"><span data-stu-id="db49e-108">When a connection request is received, **Accept** returns a new **Socket** instance that is associated with the connecting client.</span></span> <span data-ttu-id="db49e-109">Poniższy przykład odczytuje dane z klienta programu, wyświetla go w konsoli programu i zwraca dane z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="db49e-109">The following example reads data from the client, displays it on the console, and echoes the data back to the client.</span></span> <span data-ttu-id="db49e-110">**Gniazdo** nie określa żadnego protokołu obsługi komunikatów, więc ciąg " \<EOF> " oznacza koniec danych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="db49e-110">The **Socket** does not specify any messaging protocol, so the string "\<EOF>" marks the end of the message data.</span></span> <span data-ttu-id="db49e-111">Przyjęto założenie, że **gniazdo** o nazwie `listener` zostało zainicjowane i powiązane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="db49e-111">It assumes that a **Socket** named `listener` has been initialized and bound to an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db49e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db49e-112">See also</span></span>

- [<span data-ttu-id="db49e-113">Używanie asynchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="db49e-113">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="db49e-114">Przykład synchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="db49e-114">Synchronous Server Socket Example</span></span>](synchronous-server-socket-example.md)
- [<span data-ttu-id="db49e-115">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="db49e-115">Listening with Sockets</span></span>](listening-with-sockets.md)
