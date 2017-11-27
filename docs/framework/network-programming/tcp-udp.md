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
ms.openlocfilehash: 04a3bb1c7499a60175aaaa9715e780ea5ddceb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="tcp-udp"></a><span data-ttu-id="e7109-102">TCP I UDP</span><span class="sxs-lookup"><span data-stu-id="e7109-102">TCP-UDP</span></span>
<span data-ttu-id="e7109-103">Aplikacje mogą używać usług Transmission Control Protocol (TCP) i protokół UDP (User Datagram) z <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, i <xref:System.Net.Sockets.UdpClient> klasy.</span><span class="sxs-lookup"><span data-stu-id="e7109-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="e7109-104">Te klasy protokołu są wbudowane nad <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> klasy a zajmie się szczegóły transferu danych.</span><span class="sxs-lookup"><span data-stu-id="e7109-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="e7109-105">Klasy protokołu Użyj metod synchronicznych **gniazda** klasa umożliwia proste i bezpośrednie dostęp do usług sieciowych bez zwiększania utrzymywanie informacji o stanie i wiedzy o szczegóły konfiguracji oparte na protokole gniazda.</span><span class="sxs-lookup"><span data-stu-id="e7109-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="e7109-106">Aby używać asynchronicznych **gniazda** metod, można użyć metod asynchronicznych dostarczonych przez <xref:System.Net.Sockets.NetworkStream> klasy.</span><span class="sxs-lookup"><span data-stu-id="e7109-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="e7109-107">Dostępu do funkcji z **gniazda** klasy nie jest udostępniany przez protokół klasy, należy użyć **gniazda** klasy.</span><span class="sxs-lookup"><span data-stu-id="e7109-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="e7109-108">**TcpClient** i **TcpListener** reprezentują sieci za pomocą funkcji **Strumień NetworkStream** klasy.</span><span class="sxs-lookup"><span data-stu-id="e7109-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="e7109-109">Możesz użyć <xref:System.Net.Sockets.TcpClient.GetStream%2A> metodę, aby zwrócić strumień sieci, a następnie wywołać strumienia <xref:System.Net.Sockets.NetworkStream.Read%2A> i <xref:System.Net.Sockets.NetworkStream.Write%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e7109-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="e7109-110">**Strumień NetworkStream** nie jest właścicielem podstawowej gniazda z klas protokołu, więc jego zamknięciem nie wpływa na gniazdo.</span><span class="sxs-lookup"><span data-stu-id="e7109-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="e7109-111">**UdpClient** klasa korzysta z tablicy bajtów do przechowywania datagramów protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="e7109-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="e7109-112">Możesz użyć <xref:System.Net.Sockets.UdpClient.Send%2A> do wysyłania danych do sieci i <xref:System.Net.Sockets.UdpClient.Receive%2A> metodę, aby odbierać przychodzące datagramów.</span><span class="sxs-lookup"><span data-stu-id="e7109-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7109-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7109-113">See Also</span></span>  
 [<span data-ttu-id="e7109-114">Za pomocą usług TCP</span><span class="sxs-lookup"><span data-stu-id="e7109-114">Using TCP Services</span></span>](../../../docs/framework/network-programming/using-tcp-services.md)  
 [<span data-ttu-id="e7109-115">Za pomocą usług UDP</span><span class="sxs-lookup"><span data-stu-id="e7109-115">Using UDP Services</span></span>](../../../docs/framework/network-programming/using-udp-services.md)  
 [<span data-ttu-id="e7109-116">W sieci za pomocą strumieni</span><span class="sxs-lookup"><span data-stu-id="e7109-116">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="e7109-117">Przy użyciu gniazda serwera asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="e7109-117">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [<span data-ttu-id="e7109-118">Przy użyciu gniazda asynchroniczne klienta</span><span class="sxs-lookup"><span data-stu-id="e7109-118">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [<span data-ttu-id="e7109-119">Przy użyciu protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="e7109-119">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
