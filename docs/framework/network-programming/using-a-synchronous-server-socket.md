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
ms.openlocfilehash: 43e1d54d4e74b49fdf1a8997d1cc89492c9412bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796933"
---
# <a name="using-a-synchronous-server-socket"></a><span data-ttu-id="01d73-102">Używanie synchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="01d73-102">Using a Synchronous Server Socket</span></span>
<span data-ttu-id="01d73-103">Server synchronicznego gniazda zawiesić wykonanie aplikacji, dopóki nie zostanie odebrane żądanie połączenia gniazda.</span><span class="sxs-lookup"><span data-stu-id="01d73-103">Synchronous server sockets suspend the execution of the application until a connection request is received on the socket.</span></span> <span data-ttu-id="01d73-104">Server synchronicznego gniazda nie są odpowiednie dla aplikacji, które intensywnie korzystają z sieci w ich działania, ale może być odpowiednie dla aplikacji sieciowych proste.</span><span class="sxs-lookup"><span data-stu-id="01d73-104">Synchronous server sockets are not suitable for applications that make heavy use of the network in their operation, but they can be suitable for simple network applications.</span></span>  
  
 <span data-ttu-id="01d73-105">Po <xref:System.Net.Sockets.Socket> jest ustawiony do nasłuchiwania punktu końcowego za pomocą <xref:System.Net.Sockets.Socket.Bind%2A> i <xref:System.Net.Sockets.Socket.Listen%2A> metod, jest gotowy do akceptowania połączeń przychodzących żądań przy użyciu <xref:System.Net.Sockets.Socket.Accept%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="01d73-105">After a <xref:System.Net.Sockets.Socket> is set to listen on an endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> and <xref:System.Net.Sockets.Socket.Listen%2A> methods, it is ready to accept incoming connection requests using the <xref:System.Net.Sockets.Socket.Accept%2A> method.</span></span> <span data-ttu-id="01d73-106">Aplikacja jest wstrzymana, dopóki nie zostanie odebrane żądanie połączenia podczas **Akceptuj** metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="01d73-106">The application is suspended until a connection request is received when the **Accept** method is called.</span></span>  
  
 <span data-ttu-id="01d73-107">Po odebraniu żądania połączenia **Akceptuj** zwraca nowy **gniazda** wystąpienia, który jest skojarzony z klienta nawiązującego połączenie.</span><span class="sxs-lookup"><span data-stu-id="01d73-107">When a connection request is received, **Accept** returns a new **Socket** instance that is associated with the connecting client.</span></span> <span data-ttu-id="01d73-108">Poniższy przykład odczytuje dane z klienta, wyświetla go w konsoli i zwraca dane do klienta.</span><span class="sxs-lookup"><span data-stu-id="01d73-108">The following example reads data from the client, displays it on the console, and echoes the data back to the client.</span></span> <span data-ttu-id="01d73-109">**Gniazda** nie określa protokołów obsługi komunikatów, więc ciąg "\<EOF >" oznacza koniec danych komunikatu.</span><span class="sxs-lookup"><span data-stu-id="01d73-109">The **Socket** does not specify any messaging protocol, so the string "\<EOF>" marks the end of the message data.</span></span> <span data-ttu-id="01d73-110">Założono, że **gniazda** o nazwie `listener` zainicjowany i powiązane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="01d73-110">It assumes that a **Socket** named `listener` has been initialized and bound to an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01d73-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01d73-111">See also</span></span>

- [<span data-ttu-id="01d73-112">Używanie asynchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="01d73-112">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="01d73-113">Przykład synchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="01d73-113">Synchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-server-socket-example.md)
- [<span data-ttu-id="01d73-114">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="01d73-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
