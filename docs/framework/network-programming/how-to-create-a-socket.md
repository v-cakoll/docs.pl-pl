---
title: 'Instrukcje: tworzenie gniazda'
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
ms.openlocfilehash: e71e7e235048361580c65bdb551919fe3038130b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180825"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="6a9fb-102">Instrukcje: tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="6a9fb-102">How to: Create a Socket</span></span>
<span data-ttu-id="6a9fb-103">Aby można było używać gniazda do komunikowania się z urządzeniami zdalnymi, gniazdo musi zostać zainicjowane z informacjami o protokole i adresie sieciowym.</span><span class="sxs-lookup"><span data-stu-id="6a9fb-103">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="6a9fb-104">Konstruktor <xref:System.Net.Sockets.Socket> dla klasy ma parametry, które określają rodzinę adresów, typ gniazda i typ protokołu, którego gniazdo używa do nawiązywać połączenia.</span><span class="sxs-lookup"><span data-stu-id="6a9fb-104">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a9fb-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6a9fb-105">Example</span></span>  
 <span data-ttu-id="6a9fb-106">Poniższy przykład tworzy Socket, który może służyć do komunikowania się w sieci opartej na TCP/IP, takich jak Internet.</span><span class="sxs-lookup"><span data-stu-id="6a9fb-106">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="6a9fb-107">Aby użyć protokołu UDP zamiast protokołu TCP, zmień typ protokołu, tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6a9fb-107">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="6a9fb-108">Wyliczenie <xref:System.Net.Sockets.AddressFamily> określa standardowe rodziny adresów używane przez **Socket** klasy do rozpoznawania adresów sieciowych (na przykład **AddressFamily.InterNetwork** element członkowski określa ip wersji 4 rodziny adresów rodziny).</span><span class="sxs-lookup"><span data-stu-id="6a9fb-108">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="6a9fb-109">Wyliczenie <xref:System.Net.Sockets.SocketType> określa typ gniazda (na przykład **SocketType.Stream** element członkowski wskazuje standardowe gniazdo do wysyłania i odbierania danych z kontrolą przepływu).</span><span class="sxs-lookup"><span data-stu-id="6a9fb-109">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="6a9fb-110">Wyliczenie <xref:System.Net.Sockets.ProtocolType> określa protokół sieciowy używany podczas komunikacji na **socket** (na przykład **ProtocolType.Tcp** wskazuje, że gniazdo używa protokołu TCP; **ProtocolType.Udp** wskazuje, że gniazdo używa UDP).</span><span class="sxs-lookup"><span data-stu-id="6a9fb-110">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="6a9fb-111">Po utworzeniu **socket** może zainicjować połączenie ze zdalnym punktem końcowym lub odbierać połączenia z urządzeń zdalnych.</span><span class="sxs-lookup"><span data-stu-id="6a9fb-111">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a9fb-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a9fb-112">See also</span></span>

- [<span data-ttu-id="6a9fb-113">Używanie gniazd klientów</span><span class="sxs-lookup"><span data-stu-id="6a9fb-113">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="6a9fb-114">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="6a9fb-114">Listening with Sockets</span></span>](listening-with-sockets.md)
