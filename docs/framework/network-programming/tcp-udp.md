---
title: TCP-UDP
ms.date: 03/30/2017
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
ms.openlocfilehash: d35278ab7feb42453b5a0adbc86c47b7ac3ff5ca
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047114"
---
# <a name="tcp-udp"></a><span data-ttu-id="81ddf-102">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="81ddf-102">TCP-UDP</span></span>
<span data-ttu-id="81ddf-103">Aplikacje mogą używać usług Transmission Control Protocol (TCP) i UDP (User Datagram Protocol) z <xref:System.Net.Sockets.TcpClient>klasami, <xref:System.Net.Sockets.TcpListener>i <xref:System.Net.Sockets.UdpClient> .</span><span class="sxs-lookup"><span data-stu-id="81ddf-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="81ddf-104">Te klasy protokołów są zbudowane na podstawie <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> klasy i należy wziąć pod uwagę Szczegóły transferu danych.</span><span class="sxs-lookup"><span data-stu-id="81ddf-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="81ddf-105">Klasy protokołu używają metod synchronicznych klasy **Socket** , aby zapewnić prosty i prosty dostęp do usług sieciowych bez konieczności utrzymywania informacji o stanie lub znajomości szczegółów dotyczących konfigurowania gniazd specyficznych dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="81ddf-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="81ddf-106">Aby użyć asynchronicznych metod **gniazda** , można użyć metod asynchronicznych dostarczonych przez <xref:System.Net.Sockets.NetworkStream> klasę.</span><span class="sxs-lookup"><span data-stu-id="81ddf-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="81ddf-107">Aby uzyskać dostęp do funkcji klasy **Socket** , które nie są uwidaczniane przez klasy protokołów, należy użyć klasy **Socket** .</span><span class="sxs-lookup"><span data-stu-id="81ddf-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="81ddf-108">**TcpClient** i **TcpListener** reprezentują sieć przy użyciu klasy **NetworkStream** .</span><span class="sxs-lookup"><span data-stu-id="81ddf-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="81ddf-109">Używasz metody do zwrócenia strumienia sieciowego, a następnie wywołaj metody <xref:System.Net.Sockets.NetworkStream.Read%2A> strumienia i <xref:System.Net.Sockets.NetworkStream.Write%2A>. <xref:System.Net.Sockets.TcpClient.GetStream%2A></span><span class="sxs-lookup"><span data-stu-id="81ddf-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="81ddf-110">**NetworkStream** nie jest własnością gniazda bazowego klasy protokołów, dlatego zamknięcie nie ma wpływu na gniazdo.</span><span class="sxs-lookup"><span data-stu-id="81ddf-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="81ddf-111">Klasa **UdpClient** używa tablicy bajtów do przechowywania datagramu UDP.</span><span class="sxs-lookup"><span data-stu-id="81ddf-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="81ddf-112">Używasz metody do wysyłania danych do sieci <xref:System.Net.Sockets.UdpClient.Receive%2A> i metody odbierania przychodzącego datagramu. <xref:System.Net.Sockets.UdpClient.Send%2A></span><span class="sxs-lookup"><span data-stu-id="81ddf-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ddf-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81ddf-113">See also</span></span>

- [<span data-ttu-id="81ddf-114">Stosowanie usług TCP</span><span class="sxs-lookup"><span data-stu-id="81ddf-114">Using TCP Services</span></span>](using-tcp-services.md)
- [<span data-ttu-id="81ddf-115">Stosowanie usług UDP</span><span class="sxs-lookup"><span data-stu-id="81ddf-115">Using UDP Services</span></span>](using-udp-services.md)
- [<span data-ttu-id="81ddf-116">Stosowanie strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="81ddf-116">Using Streams on the Network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="81ddf-117">Używanie asynchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="81ddf-117">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="81ddf-118">Używanie asynchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="81ddf-118">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="81ddf-119">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="81ddf-119">Using Application Protocols</span></span>](using-application-protocols.md)
