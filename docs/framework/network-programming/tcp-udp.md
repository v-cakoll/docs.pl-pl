---
title: TCP-UDP
description: Dowiedz się, w jaki sposób klasy TcpClient, TcpListener i UdpClient obsługują protokoły TCP i UDP, które uwzględniają Szczegóły transferu danych w .NET Framework.
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
ms.openlocfilehash: ae6d2f9ced2235aa1b9b8fada8064d7e4be970a0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502096"
---
# <a name="tcp-udp"></a><span data-ttu-id="dac9c-103">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="dac9c-103">TCP-UDP</span></span>
<span data-ttu-id="dac9c-104">Aplikacje mogą używać usług Transmission Control Protocol (TCP) i UDP (User Datagram Protocol) z <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener> klasami, i <xref:System.Net.Sockets.UdpClient> .</span><span class="sxs-lookup"><span data-stu-id="dac9c-104">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="dac9c-105">Te klasy protokołów są zbudowane na podstawie <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> klasy i należy wziąć pod uwagę Szczegóły transferu danych.</span><span class="sxs-lookup"><span data-stu-id="dac9c-105">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="dac9c-106">Klasy protokołu używają metod synchronicznych klasy **Socket** , aby zapewnić prosty i prosty dostęp do usług sieciowych bez konieczności utrzymywania informacji o stanie lub znajomości szczegółów dotyczących konfigurowania gniazd specyficznych dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="dac9c-106">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="dac9c-107">Aby użyć asynchronicznych metod **gniazda** , można użyć metod asynchronicznych dostarczonych przez <xref:System.Net.Sockets.NetworkStream> klasę.</span><span class="sxs-lookup"><span data-stu-id="dac9c-107">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="dac9c-108">Aby uzyskać dostęp do funkcji klasy **Socket** , które nie są uwidaczniane przez klasy protokołów, należy użyć klasy **Socket** .</span><span class="sxs-lookup"><span data-stu-id="dac9c-108">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="dac9c-109">**TcpClient** i **TcpListener** reprezentują sieć przy użyciu klasy **NetworkStream** .</span><span class="sxs-lookup"><span data-stu-id="dac9c-109">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="dac9c-110">Używasz <xref:System.Net.Sockets.TcpClient.GetStream%2A> metody do zwrócenia strumienia sieciowego, a następnie Wywołaj <xref:System.Net.Sockets.NetworkStream.Read%2A> metody strumienia i <xref:System.Net.Sockets.NetworkStream.Write%2A> .</span><span class="sxs-lookup"><span data-stu-id="dac9c-110">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="dac9c-111">**NetworkStream** nie jest własnością gniazda bazowego klasy protokołów, dlatego zamknięcie nie ma wpływu na gniazdo.</span><span class="sxs-lookup"><span data-stu-id="dac9c-111">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="dac9c-112">Klasa **UdpClient** używa tablicy bajtów do przechowywania datagramu UDP.</span><span class="sxs-lookup"><span data-stu-id="dac9c-112">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="dac9c-113">Używasz <xref:System.Net.Sockets.UdpClient.Send%2A> metody do wysyłania danych do sieci i <xref:System.Net.Sockets.UdpClient.Receive%2A> metody odbierania przychodzącego datagramu.</span><span class="sxs-lookup"><span data-stu-id="dac9c-113">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac9c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dac9c-114">See also</span></span>

- [<span data-ttu-id="dac9c-115">Stosowanie usług TCP</span><span class="sxs-lookup"><span data-stu-id="dac9c-115">Using TCP Services</span></span>](using-tcp-services.md)
- [<span data-ttu-id="dac9c-116">Stosowanie usług UDP</span><span class="sxs-lookup"><span data-stu-id="dac9c-116">Using UDP Services</span></span>](using-udp-services.md)
- [<span data-ttu-id="dac9c-117">Stosowanie strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="dac9c-117">Using Streams on the Network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="dac9c-118">Używanie asynchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="dac9c-118">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="dac9c-119">Używanie asynchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="dac9c-119">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="dac9c-120">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="dac9c-120">Using Application Protocols</span></span>](using-application-protocols.md)
