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
ms.openlocfilehash: 0bbdab11201171bf8d730276c7f94cbc5317acdd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101123"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="aac87-102">Instrukcje: tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="aac87-102">How to: Create a Socket</span></span>
<span data-ttu-id="aac87-103">Zanim użyjesz gniazda do komunikowania się z urządzeniami zdalnymi gniazda musi zostać zainicjowany z informacjami o adresie protokołu i sieci.</span><span class="sxs-lookup"><span data-stu-id="aac87-103">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="aac87-104">Konstruktor <xref:System.Net.Sockets.Socket> klasa ma parametry, które określają rodziny adresów, typ gniazda i typ protokołu, który gniazda używa do nawiązywania połączeń.</span><span class="sxs-lookup"><span data-stu-id="aac87-104">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aac87-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="aac87-105">Example</span></span>  
 <span data-ttu-id="aac87-106">Poniższy przykład tworzy gniazdo, który może służyć do komunikacji w sieci opartego na protokole IP, takich jak Internet.</span><span class="sxs-lookup"><span data-stu-id="aac87-106">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="aac87-107">Aby użyć protokołu UDP, zamiast połączenia TCP, Zmień typ protokołu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="aac87-107">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="aac87-108"><xref:System.Net.Sockets.AddressFamily> Wyliczenie określa rodzin standardowy adres używany przez **gniazda** klasy do rozpoznawania adresów sieciowych (na przykład **AddressFamily.InterNetwork** elementu członkowskiego Określa adres IP Rodzina adresów w wersji 4).</span><span class="sxs-lookup"><span data-stu-id="aac87-108">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="aac87-109"><xref:System.Net.Sockets.SocketType> Wyliczenie określa rodzaj gniazd (na przykład **SocketType.Stream** członka wskazuje standardowy gniazda do wysyłania i odbierania danych za pomocą sterowanie przepływem).</span><span class="sxs-lookup"><span data-stu-id="aac87-109">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="aac87-110"><xref:System.Net.Sockets.ProtocolType> Wyliczenie Określa protokół do użycia przy komunikacji na **gniazda** (na przykład **ProtocolType.Tcp** wskazuje, że gniazdo używa protokołu TCP; **ProtocolType.Udp** wskazuje, że gniazdo używa protokołu UDP).</span><span class="sxs-lookup"><span data-stu-id="aac87-110">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="aac87-111">Po **gniazda** jest utworzone, jego można inicjować połączenie w celu zdalnego punktu końcowego lub odbierania połączeń z urządzeniami zdalnymi.</span><span class="sxs-lookup"><span data-stu-id="aac87-111">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac87-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aac87-112">See also</span></span>

- [<span data-ttu-id="aac87-113">Używanie gniazd klientów</span><span class="sxs-lookup"><span data-stu-id="aac87-113">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)
- [<span data-ttu-id="aac87-114">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="aac87-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
