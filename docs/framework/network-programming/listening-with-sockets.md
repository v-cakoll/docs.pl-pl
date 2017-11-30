---
title: "Nasłuchiwanie z gniazda"
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
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6f96463b4f9cb7e61c403cfd77f747c8aefd99a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="listening-with-sockets"></a><span data-ttu-id="50b13-102">Nasłuchiwanie z gniazda</span><span class="sxs-lookup"><span data-stu-id="50b13-102">Listening with Sockets</span></span>
<span data-ttu-id="50b13-103">Gniazda odbiornika lub serwera Otwórz port w sieci, a następnie poczekaj dla klienta połączyć się z tym portem.</span><span class="sxs-lookup"><span data-stu-id="50b13-103">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="50b13-104">Mimo że istnieją inne rodziny adresów sieci i protokołów, w tym przykładzie pokazano, jak można utworzyć usługi zdalnej dla sieci TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="50b13-104">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="50b13-105">Unikatowy adres usługi TCP/IP jest zdefiniowana przez połączenie adres IP hosta i numer portu usługi można utworzyć punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="50b13-105">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="50b13-106"><xref:System.Net.Dns> Klasa dostarcza metody, które zwracają informacje o adresy sieciowe obsługiwane przez urządzenie sieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="50b13-106">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="50b13-107">Gdy urządzenie sieci lokalnej ma więcej niż jednego adresu sieciowego lub systemu lokalnego obsługuje więcej niż jednego urządzenia sieciowego, **Dns** klasy zwraca informacje o wszystkich adresów sieciowych, a aplikacji należy wybrać odpowiednią adres usługi.</span><span class="sxs-lookup"><span data-stu-id="50b13-107">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="50b13-108">Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług wspólnej (Aby uzyskać więcej informacji, zobacz www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="50b13-108">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="50b13-109">Inne usługi można zarejestrować numery portów z zakresu od 1024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="50b13-109">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="50b13-110">Poniższy przykład tworzy <xref:System.Net.IPEndPoint> dla serwera, łącząc pierwszy adres IP zwrócony przez **Dns** komputera-hosta z numerem portu wybrane z zakresu numerów portów zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="50b13-110">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 <span data-ttu-id="50b13-111">Po lokalny punkt końcowy jest określana, <xref:System.Net.Sockets.Socket> musi być skojarzony z tego punktu końcowego za pomocą <xref:System.Net.Sockets.Socket.Bind%2A> — metoda i zestawu do nasłuchiwania punktu końcowego za pomocą <xref:System.Net.Sockets.Socket.Listen%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="50b13-111">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="50b13-112">**Powiąż** zgłasza wyjątek, jeśli konkretnym kombinacji adres i port jest już używana.</span><span class="sxs-lookup"><span data-stu-id="50b13-112">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="50b13-113">W poniższym przykładzie pokazano kojarzenie **gniazda** z **IPEndPoint**.</span><span class="sxs-lookup"><span data-stu-id="50b13-113">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp) 
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 <span data-ttu-id="50b13-114">**Nasłuchiwania** metoda przyjmuje jeden parametr, który określa liczbę oczekujących połączeń **gniazda** są dozwolone przed zwróceniem do klienta nawiązującego połączenie zajęty błąd serwera.</span><span class="sxs-lookup"><span data-stu-id="50b13-114">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="50b13-115">W takim przypadku maksymalnie 100 klientami są umieszczane w kolejce połączenia przed zwróceniem do klienta o numerze 101 zajęty odpowiedź serwera.</span><span class="sxs-lookup"><span data-stu-id="50b13-115">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b13-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50b13-116">See Also</span></span>  
 [<span data-ttu-id="50b13-117">Przy użyciu gniazda synchroniczne serwera</span><span class="sxs-lookup"><span data-stu-id="50b13-117">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [<span data-ttu-id="50b13-118">Przy użyciu gniazda serwera asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="50b13-118">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [<span data-ttu-id="50b13-119">Używanie klienta gniazd</span><span class="sxs-lookup"><span data-stu-id="50b13-119">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)  
 [<span data-ttu-id="50b13-120">Porady: Tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="50b13-120">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [<span data-ttu-id="50b13-121">Gniazda</span><span class="sxs-lookup"><span data-stu-id="50b13-121">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
