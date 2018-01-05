---
title: TCP I UDP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- protocols, TCP/UDP
- network resources, TCP/UDP
- sending data, TCP/UDP
- TCP/UDP
- TcpClient class, about TcpClient class
- application protocols, TCP/UDP
- receiving data, TCP/UDP
- TcpListener class, about TcpListener class
- Socket class, about Socket class
- UDP
- data requests, TCP/UDP
- requesting data from Internet, TCP/UDP
- Internet, TCP/UDP
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f62475e8b44d9cdda13322dc223509572c4ae541
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="tcp-udp"></a><span data-ttu-id="8265e-102">TCP I UDP</span><span class="sxs-lookup"><span data-stu-id="8265e-102">TCP-UDP</span></span>
<span data-ttu-id="8265e-103">Aplikacje mogą używać usług Transmission Control Protocol (TCP) i protokół UDP (User Datagram) z <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, i <xref:System.Net.Sockets.UdpClient> klasy.</span><span class="sxs-lookup"><span data-stu-id="8265e-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="8265e-104">Te klasy protokołu są wbudowane nad <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> klasy a zajmie się szczegóły transferu danych.</span><span class="sxs-lookup"><span data-stu-id="8265e-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="8265e-105">Klasy protokołu Użyj metod synchronicznych **gniazda** klasa umożliwia proste i bezpośrednie dostęp do usług sieciowych bez zwiększania utrzymywanie informacji o stanie i wiedzy o szczegóły konfiguracji oparte na protokole gniazda.</span><span class="sxs-lookup"><span data-stu-id="8265e-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="8265e-106">Aby używać asynchronicznych **gniazda** metod, można użyć metod asynchronicznych dostarczonych przez <xref:System.Net.Sockets.NetworkStream> klasy.</span><span class="sxs-lookup"><span data-stu-id="8265e-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="8265e-107">Dostępu do funkcji z **gniazda** klasy nie jest udostępniany przez protokół klasy, należy użyć **gniazda** klasy.</span><span class="sxs-lookup"><span data-stu-id="8265e-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="8265e-108">**TcpClient** i **TcpListener** reprezentują sieci za pomocą funkcji **Strumień NetworkStream** klasy.</span><span class="sxs-lookup"><span data-stu-id="8265e-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="8265e-109">Możesz użyć <xref:System.Net.Sockets.TcpClient.GetStream%2A> metodę, aby zwrócić strumień sieci, a następnie wywołać strumienia <xref:System.Net.Sockets.NetworkStream.Read%2A> i <xref:System.Net.Sockets.NetworkStream.Write%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8265e-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="8265e-110">**Strumień NetworkStream** nie jest właścicielem podstawowej gniazda z klas protokołu, więc jego zamknięciem nie wpływa na gniazdo.</span><span class="sxs-lookup"><span data-stu-id="8265e-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="8265e-111">**UdpClient** klasa korzysta z tablicy bajtów do przechowywania datagramów protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="8265e-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="8265e-112">Możesz użyć <xref:System.Net.Sockets.UdpClient.Send%2A> do wysyłania danych do sieci i <xref:System.Net.Sockets.UdpClient.Receive%2A> metodę, aby odbierać przychodzące datagramów.</span><span class="sxs-lookup"><span data-stu-id="8265e-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8265e-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8265e-113">See Also</span></span>  
 [<span data-ttu-id="8265e-114">Stosowanie usług TCP</span><span class="sxs-lookup"><span data-stu-id="8265e-114">Using TCP Services</span></span>](../../../docs/framework/network-programming/using-tcp-services.md)  
 [<span data-ttu-id="8265e-115">Stosowanie usług UDP</span><span class="sxs-lookup"><span data-stu-id="8265e-115">Using UDP Services</span></span>](../../../docs/framework/network-programming/using-udp-services.md)  
 [<span data-ttu-id="8265e-116">Stosowanie strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="8265e-116">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="8265e-117">Używanie asynchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="8265e-117">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [<span data-ttu-id="8265e-118">Używanie asynchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="8265e-118">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [<span data-ttu-id="8265e-119">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="8265e-119">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
