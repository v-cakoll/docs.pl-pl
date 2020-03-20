---
title: Nasłuchiwanie przy użyciu gniazd
ms.date: 03/30/2017
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
ms.openlocfilehash: cf8316ede6888b99a8b0c87cfa3426b33be18b7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180741"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="c6fdb-102">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="c6fdb-102">Listening with Sockets</span></span>
<span data-ttu-id="c6fdb-103">Gniazda odbiornika lub serwera otwierają port w sieci, a następnie czekają na połączenie klienta z tym portem.</span><span class="sxs-lookup"><span data-stu-id="c6fdb-103">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="c6fdb-104">Chociaż istnieją inne rodziny i protokoły adresów sieciowych, w tym przykładzie pokazano, jak utworzyć usługę zdalną dla sieci TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="c6fdb-104">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="c6fdb-105">Unikatowy adres usługi TCP/IP jest definiowany przez połączenie adresu IP hosta z numerem portu usługi w celu utworzenia punktu końcowego dla usługi.</span><span class="sxs-lookup"><span data-stu-id="c6fdb-105">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="c6fdb-106">Klasa <xref:System.Net.Dns> zawiera metody, które zwracają informacje o adresach sieciowych obsługiwanych przez lokalne urządzenie sieciowe.</span><span class="sxs-lookup"><span data-stu-id="c6fdb-106">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="c6fdb-107">Gdy lokalne urządzenie sieciowe ma więcej niż jeden adres sieciowy lub jeśli system lokalny obsługuje więcej niż jedno urządzenie sieciowe, klasa **Dns** zwraca informacje o wszystkich adresach sieciowych, a aplikacja musi wybrać odpowiedni adres usługi.</span><span class="sxs-lookup"><span data-stu-id="c6fdb-107">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="c6fdb-108">Urząd numerów przypisanych do Internetu (Iana) definiuje numery portów dla usług wspólnych; Aby uzyskać więcej informacji, zobacz [Nazwa usługi i Rejestr numerów portów protokołu transportu](https://www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="c6fdb-108">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services; for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="c6fdb-109">Inne usługi mogą mieć zarejestrowane numery portów w zakresie od 1024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="c6fdb-109">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="c6fdb-110">Poniższy przykład <xref:System.Net.IPEndPoint> tworzy dla serwera przez połączenie pierwszego adresu IP zwróconego przez **dns** dla komputera-hosta z numerem portu wybranym z zakresu numerów zarejestrowanych portów.</span><span class="sxs-lookup"><span data-stu-id="c6fdb-110">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 <span data-ttu-id="c6fdb-111">Po określeniu lokalnego <xref:System.Net.Sockets.Socket> punktu końcowego musi być <xref:System.Net.Sockets.Socket.Bind%2A> skojarzony z tym punktem końcowym <xref:System.Net.Sockets.Socket.Listen%2A> przy użyciu metody i ustawić nasłuchiwać na punkt końcowy przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="c6fdb-111">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="c6fdb-112">**Bind** zgłasza wyjątek, jeśli określona kombinacja adresu i portu jest już używana.</span><span class="sxs-lookup"><span data-stu-id="c6fdb-112">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="c6fdb-113">W poniższym przykładzie pokazano skojarzenie **socket** z **IPEndPoint**.</span><span class="sxs-lookup"><span data-stu-id="c6fdb-113">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
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
  
 <span data-ttu-id="c6fdb-114">Listen **Listen** Metoda przyjmuje jeden parametr, który określa, ile oczekujących połączeń **do Gniazda** są dozwolone przed błąd zajęty serwera jest zwracany do klienta łączącego.</span><span class="sxs-lookup"><span data-stu-id="c6fdb-114">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="c6fdb-115">W takim przypadku do 100 klientów są umieszczane w kolejce połączenia przed serwer zajęty odpowiedzi jest zwracany do numeru klienta 101.</span><span class="sxs-lookup"><span data-stu-id="c6fdb-115">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6fdb-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6fdb-116">See also</span></span>

- [<span data-ttu-id="c6fdb-117">Używanie synchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="c6fdb-117">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="c6fdb-118">Używanie asynchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="c6fdb-118">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="c6fdb-119">Używanie gniazd klientów</span><span class="sxs-lookup"><span data-stu-id="c6fdb-119">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="c6fdb-120">Instrukcje: tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="c6fdb-120">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="c6fdb-121">Gniazda</span><span class="sxs-lookup"><span data-stu-id="c6fdb-121">Sockets</span></span>](sockets.md)
