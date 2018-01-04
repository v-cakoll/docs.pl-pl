---
title: 'Porady: Tworzenie gniazda'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 24ec39798f5f31cf20cc5c84714efaae6ccbed52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="448dd-102">Porady: Tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="448dd-102">How to: Create a Socket</span></span>
<span data-ttu-id="448dd-103">Zanim użyjesz gniazda komunikację z urządzeniami zdalnego gniazda musi zostać zainicjowany z informacjami o adresie protokołu i sieci.</span><span class="sxs-lookup"><span data-stu-id="448dd-103">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="448dd-104">Konstruktor <xref:System.Net.Sockets.Socket> klasa ma następujące parametry określające rodziny adresów, typ gniazda i typ protokołu, który używa gniazda do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="448dd-104">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="448dd-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="448dd-105">Example</span></span>  
 <span data-ttu-id="448dd-106">Poniższy przykład tworzy gniazda, który może służyć do komunikacji w sieci opartych na protokole TCP/IP, takich jak Internet.</span><span class="sxs-lookup"><span data-stu-id="448dd-106">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="448dd-107">Aby użyć UDP zamiast protokołu TCP, należy zmienić typ protokołu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="448dd-107">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="448dd-108"><xref:System.Net.Sockets.AddressFamily> Wyliczenie określa rodzin standardowy adres używany przez **gniazda** klasy do rozpoznawania adresów sieciowych (na przykład **AddressFamily.InterNetwork** elementu członkowskiego Określa adres IP Rodzina adresów IPv4).</span><span class="sxs-lookup"><span data-stu-id="448dd-108">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="448dd-109"><xref:System.Net.Sockets.SocketType> Wyliczenie Określa typ gniazda (na przykład **SocketType.Stream** Członkowskie wskazuje standardowe gniazda do wysyłania i odbierania danych za pomocą sterowania przepływem).</span><span class="sxs-lookup"><span data-stu-id="448dd-109">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="448dd-110"><xref:System.Net.Sockets.ProtocolType> Wyliczenie Określa protokół do użycia przy komunikacji na **gniazda** (na przykład **ProtocolType.Tcp** wskazuje, że gniazda używa protokołu TCP; **ProtocolType.Udp** wskazuje, że gniazda używa protokołu UDP).</span><span class="sxs-lookup"><span data-stu-id="448dd-110">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="448dd-111">Po **gniazda** jest tworzony, go można inicjować połączenie zdalnego punktu końcowego lub odbierania połączeń z urządzeń zdalnych.</span><span class="sxs-lookup"><span data-stu-id="448dd-111">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="448dd-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="448dd-112">See Also</span></span>  
 [<span data-ttu-id="448dd-113">Używanie gniazd klientów</span><span class="sxs-lookup"><span data-stu-id="448dd-113">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)  
 [<span data-ttu-id="448dd-114">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="448dd-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
