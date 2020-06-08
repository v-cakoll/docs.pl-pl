---
title: 'Instrukcje: tworzenie gniazda'
description: Dowiedz się, jak zainicjować gniazdo do komunikowania się z urządzeniami zdalnymi. Użyj klasy Socket, aby określić rodzinę adresów, typ gniazda i typ protokołu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
ms.openlocfilehash: 1d56ddea721b54192a7dd47d144b6c41bbb9a5d7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502551"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="9518d-104">Instrukcje: tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="9518d-104">How to: Create a Socket</span></span>
<span data-ttu-id="9518d-105">Aby można było używać gniazda do komunikowania się z urządzeniami zdalnymi, gniazdo musi być zainicjowane przy użyciu informacji o protokole i adresie sieciowym.</span><span class="sxs-lookup"><span data-stu-id="9518d-105">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="9518d-106">Konstruktor dla <xref:System.Net.Sockets.Socket> klasy ma parametry, które określają rodzinę adresów, typ gniazda i typ protokołu, który jest wykorzystywany przez gniazdo do nawiązywania połączeń.</span><span class="sxs-lookup"><span data-stu-id="9518d-106">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9518d-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9518d-107">Example</span></span>  
 <span data-ttu-id="9518d-108">Poniższy przykład tworzy gniazdo, którego można użyć do komunikowania się w sieci opartej na protokole TCP/IP, na przykład w Internecie.</span><span class="sxs-lookup"><span data-stu-id="9518d-108">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="9518d-109">Aby użyć protokołu UDP zamiast TCP, należy zmienić typ protokołu, tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9518d-109">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="9518d-110"><xref:System.Net.Sockets.AddressFamily>Wyliczenie określa rodziny adresów standardowych używane przez klasę **Socket** do rozpoznawania adresów sieciowych (na przykład członek **AddressFamily. Internetwork** określa rodzinę adresów IP w wersji 4).</span><span class="sxs-lookup"><span data-stu-id="9518d-110">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="9518d-111"><xref:System.Net.Sockets.SocketType>Wyliczenie określa typ gniazda (na przykład, członek **gniazda. Stream** wskazuje standardowe gniazdo do wysyłania i otrzymywania danych za pomocą sterowania przepływem).</span><span class="sxs-lookup"><span data-stu-id="9518d-111">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="9518d-112"><xref:System.Net.Sockets.ProtocolType>Wyliczenie określa protokół sieciowy, który ma być używany podczas komunikacji w **gnieździe** (na przykład **ProtocolType. TCP** wskazuje, że gniazdo używa protokołu TCP; **ProtocolType. UDP** wskazuje, że gniazdo używa protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="9518d-112">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="9518d-113">Po utworzeniu **gniazda** można zainicjować połączenie ze zdalnym punktem końcowym lub odebrać połączenia z urządzeń zdalnych.</span><span class="sxs-lookup"><span data-stu-id="9518d-113">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9518d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9518d-114">See also</span></span>

- [<span data-ttu-id="9518d-115">Używanie gniazd klientów</span><span class="sxs-lookup"><span data-stu-id="9518d-115">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="9518d-116">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="9518d-116">Listening with Sockets</span></span>](listening-with-sockets.md)
