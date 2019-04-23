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
ms.openlocfilehash: 339f9c9d8b25f6deef4cc77f60c26b7b5d017ce0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105784"
---
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="3b7d4-102">Używanie synchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="3b7d4-102">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="3b7d4-103">Synchronicznego gniazda klienta zawiesza program aplikacji podczas wykonywania operacji sieciowej.</span><span class="sxs-lookup"><span data-stu-id="3b7d4-103">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="3b7d4-104">Synchronicznego gniazda nie są odpowiednie dla aplikacji, które intensywnie korzystają z sieci do ich działania, ale mogą one umożliwiać prosty dostęp do usług sieciowych dla innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b7d4-104">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="3b7d4-105">Aby wysyłać dane, należy przekazać tablicy typu byte do jednej z <xref:System.Net.Sockets.Socket> metod wysyłania danych klasy (<xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.SendTo%2A>).</span><span class="sxs-lookup"><span data-stu-id="3b7d4-105">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="3b7d4-106">Poniższy przykład koduje ciąg w użyciu bufor tablicy bajtów <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> właściwości i następnie przesyła bufor do urządzenia sieciowego za pomocą **wysyłania** metody.</span><span class="sxs-lookup"><span data-stu-id="3b7d4-106">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="3b7d4-107">**Wysyłania** metoda zwraca liczbę bajtów wysłanych z urządzeniem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="3b7d4-107">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="3b7d4-108">**Wysyłania** metoda usuwa bajtów z bufora i kolejki je z interfejsem sieciowym do wysłania do urządzenia sieciowego.</span><span class="sxs-lookup"><span data-stu-id="3b7d4-108">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="3b7d4-109">Interfejs sieciowy nie może wysłać dane od razu, ale wysyła on po pewnym czasie tak długo, jak połączenie jest zamknięte zwykle z <xref:System.Net.Sockets.Socket.Shutdown%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3b7d4-109">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="3b7d4-110">Odbieranie danych z urządzenia sieciowego, należy przekazać do jednego z buforu **gniazda** metod odbierania danych klasy (<xref:System.Net.Sockets.Socket.Receive%2A> i <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span><span class="sxs-lookup"><span data-stu-id="3b7d4-110">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="3b7d4-111">Synchronicznego gniazda zostanie zawieszone aplikacji, dopóki nie są odbierane z sieci, lub do czasu zamknięcia gniazda.</span><span class="sxs-lookup"><span data-stu-id="3b7d4-111">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="3b7d4-112">Poniższy przykład odbiera dane z sieci i wyświetla go w konsoli.</span><span class="sxs-lookup"><span data-stu-id="3b7d4-112">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="3b7d4-113">W przykładzie założono, że dane pochodzące z sieci należy tekstowymi w formacie ASCII.</span><span class="sxs-lookup"><span data-stu-id="3b7d4-113">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="3b7d4-114">**Receive** metoda zwraca liczbę bajtów odebranych z sieci.</span><span class="sxs-lookup"><span data-stu-id="3b7d4-114">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
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
  
 <span data-ttu-id="3b7d4-115">Gdy gniazda nie jest już potrzebny, musisz zwolnić go przez wywołanie metody <xref:System.Net.Sockets.Socket.Shutdown%2A> metody, a następnie wywołując **Zamknij** metody.</span><span class="sxs-lookup"><span data-stu-id="3b7d4-115">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="3b7d4-116">Poniższy przykład zwalnia **gniazda**.</span><span class="sxs-lookup"><span data-stu-id="3b7d4-116">The following example releases a **Socket**.</span></span> <span data-ttu-id="3b7d4-117"><xref:System.Net.Sockets.SocketShutdown> Wyliczenie definiuje stałe, które wskazują, czy gniazda powinien zostać zamknięty, wysyłanie, odbieranie lub dla obu.</span><span class="sxs-lookup"><span data-stu-id="3b7d4-117">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b7d4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b7d4-118">See also</span></span>

- [<span data-ttu-id="3b7d4-119">Używanie asynchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="3b7d4-119">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="3b7d4-120">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="3b7d4-120">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
- [<span data-ttu-id="3b7d4-121">Przykład synchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="3b7d4-121">Synchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
