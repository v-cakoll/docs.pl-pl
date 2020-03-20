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
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="00035-102">Używanie synchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="00035-102">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="00035-103">Synchroniczne gniazdo klienta zawiesza program aplikacji po zakończeniu operacji sieciowej.</span><span class="sxs-lookup"><span data-stu-id="00035-103">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="00035-104">Gniazda synchroniczne nie są odpowiednie dla aplikacji, które intensywnie korzystają z sieci do ich działania, ale mogą umożliwić prosty dostęp do usług sieciowych dla innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="00035-104">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="00035-105">Aby wysłać dane, przekaż tablicę <xref:System.Net.Sockets.Socket> bajtów do jednej<xref:System.Net.Sockets.Socket.Send%2A> z <xref:System.Net.Sockets.Socket.SendTo%2A>metod wysyłania danych klasy ( i ).</span><span class="sxs-lookup"><span data-stu-id="00035-105">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="00035-106">Poniższy przykład koduje ciąg do buforu tablicy bajtów przy użyciu <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> właściwości, a następnie przesyła bufor do urządzenia sieciowego przy użyciu **Send** metody.</span><span class="sxs-lookup"><span data-stu-id="00035-106">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="00035-107">Send **Send** Metoda zwraca liczbę bajtów wysłanych do urządzenia sieciowego.</span><span class="sxs-lookup"><span data-stu-id="00035-107">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="00035-108">**Send** Metoda usuwa bajty z buforu i kolejkuje je z interfejsem sieciowym, które mają być wysyłane do urządzenia sieciowego.</span><span class="sxs-lookup"><span data-stu-id="00035-108">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="00035-109">Interfejs sieciowy może nie wysłać danych natychmiast, ale wyśle je ostatecznie, tak długo, jak połączenie jest zamknięte normalnie z <xref:System.Net.Sockets.Socket.Shutdown%2A> metodą.</span><span class="sxs-lookup"><span data-stu-id="00035-109">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="00035-110">Aby odbierać dane z urządzenia sieciowego, należy przekazać bufor do jednej<xref:System.Net.Sockets.Socket.Receive%2A> <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>z metod odbierania danych klasy **Socket** ( i ).</span><span class="sxs-lookup"><span data-stu-id="00035-110">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="00035-111">Gniazda synchroniczne zawieszają aplikację do momentu odebraniem bajtów z sieci lub do momentu zamknięcia gniazda.</span><span class="sxs-lookup"><span data-stu-id="00035-111">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="00035-112">Poniższy przykład odbiera dane z sieci, a następnie wyświetla je na konsoli.</span><span class="sxs-lookup"><span data-stu-id="00035-112">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="00035-113">W przykładzie przyjęto założenie, że dane pochodzące z sieci są tekstem zakodowanym w ascii.</span><span class="sxs-lookup"><span data-stu-id="00035-113">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="00035-114">Receive **Receive** Metoda zwraca liczbę bajtów odebranych z sieci.</span><span class="sxs-lookup"><span data-stu-id="00035-114">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
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
  
 <span data-ttu-id="00035-115">Gdy gniazdo nie jest już potrzebne, należy go <xref:System.Net.Sockets.Socket.Shutdown%2A> zwolnić, wywołując metodę, a następnie wywołując **Close** metody.</span><span class="sxs-lookup"><span data-stu-id="00035-115">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="00035-116">Poniższy przykład zwalnia **Socket**.</span><span class="sxs-lookup"><span data-stu-id="00035-116">The following example releases a **Socket**.</span></span> <span data-ttu-id="00035-117">Wyliczenie <xref:System.Net.Sockets.SocketShutdown> definiuje stałe, które wskazują, czy gniazdo powinno być zamknięte do wysyłania, odbierania lub dla obu.</span><span class="sxs-lookup"><span data-stu-id="00035-117">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="00035-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00035-118">See also</span></span>

- [<span data-ttu-id="00035-119">Używanie asynchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="00035-119">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="00035-120">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="00035-120">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="00035-121">Przykład synchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="00035-121">Synchronous Client Socket Example</span></span>](synchronous-client-socket-example.md)
