---
title: Przy użyciu gniazda synchroniczne klienta
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c9101957c6c4b9961ca5985bda8b8f82d69b45d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397705"
---
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="0d825-102">Przy użyciu gniazda synchroniczne klienta</span><span class="sxs-lookup"><span data-stu-id="0d825-102">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="0d825-103">Gniazda synchroniczne klienta zawiesza program aplikacji podczas operacji sieciowej.</span><span class="sxs-lookup"><span data-stu-id="0d825-103">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="0d825-104">Gniazda synchroniczne nie są odpowiednie dla aplikacji, które w znacznym stopniu wykorzystywane sieci dla ich działania, ale umożliwiają one proste dostęp do usług sieciowych dla innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0d825-104">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="0d825-105">Aby wysłać dane, Przekaż tablica bajtów do jednego z <xref:System.Net.Sockets.Socket> metod wysyłania danych klasy (<xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.SendTo%2A>).</span><span class="sxs-lookup"><span data-stu-id="0d825-105">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="0d825-106">Poniższy przykład koduje ciąg w użyciu buforu tablicy bajtów <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> właściwości, a następnie przesyła bufor do urządzenia sieciowego przy użyciu **wysyłania** metody.</span><span class="sxs-lookup"><span data-stu-id="0d825-106">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="0d825-107">**Wysyłania** metoda zwraca liczbę bajtów wysłanych z urządzeniem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="0d825-107">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="0d825-108">**Wysyłania** — metoda usuwa bajtów z buforu, a kolejki je z interfejsem sieciowym do wysłania do urządzenia sieciowego.</span><span class="sxs-lookup"><span data-stu-id="0d825-108">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="0d825-109">Interfejs sieciowy nie może wysłać dane od razu, ale wysyła on po pewnym czasie tak długo, jak połączenie jest zamknięte zwykle z <xref:System.Net.Sockets.Socket.Shutdown%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0d825-109">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="0d825-110">Na odbieranie danych z urządzenia sieciowego, Przekaż bufor do jednego z **gniazda** metody odbierania danych klasy (<xref:System.Net.Sockets.Socket.Receive%2A> i <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span><span class="sxs-lookup"><span data-stu-id="0d825-110">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="0d825-111">Synchroniczne sockets zawiesi stosowanie, dopóki nie są odbierane z sieci, lub do czasu zamknięcia gniazda.</span><span class="sxs-lookup"><span data-stu-id="0d825-111">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="0d825-112">Poniższy przykład odbiera dane z sieci i wyświetla je w konsoli.</span><span class="sxs-lookup"><span data-stu-id="0d825-112">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="0d825-113">W przykładzie założono, że danych przesyłanych przez sieć jest kodowany w formacie ASCII tekstu.</span><span class="sxs-lookup"><span data-stu-id="0d825-113">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="0d825-114">**Receive** metoda zwraca liczbę bajtów odebranych z sieci.</span><span class="sxs-lookup"><span data-stu-id="0d825-114">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
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
  
 <span data-ttu-id="0d825-115">Gniazda jest już potrzebne, musisz zwolnić go przez wywołanie metody <xref:System.Net.Sockets.Socket.Shutdown%2A> — metoda i wywołując **Zamknij** metody.</span><span class="sxs-lookup"><span data-stu-id="0d825-115">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="0d825-116">Poniższy przykład zwalnia **gniazda**.</span><span class="sxs-lookup"><span data-stu-id="0d825-116">The following example releases a **Socket**.</span></span> <span data-ttu-id="0d825-117"><xref:System.Net.Sockets.SocketShutdown> Wyliczenie definiuje stałe, które wskazują, czy gniazda powinno zostać zamknięte do wysyłania do odbierania lub oba.</span><span class="sxs-lookup"><span data-stu-id="0d825-117">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d825-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d825-118">See Also</span></span>  
 [<span data-ttu-id="0d825-119">Używanie asynchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="0d825-119">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [<span data-ttu-id="0d825-120">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="0d825-120">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)  
 [<span data-ttu-id="0d825-121">Przykład synchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="0d825-121">Synchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
