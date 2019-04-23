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
ms.openlocfilehash: c3d5a7d6040038eb6d768815b1ae9e8ad45c5810
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109957"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="5d888-102">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="5d888-102">Listening with Sockets</span></span>
<span data-ttu-id="5d888-103">Gniazda odbiornika lub serwera Otwórz port w sieci, a następnie poczekaj klienta połączyć się z tym portem.</span><span class="sxs-lookup"><span data-stu-id="5d888-103">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="5d888-104">Mimo że istnieją inne rodziny adresów sieciowych i protokołów, w tym przykładzie pokazano, jak utworzyć usługi zdalnej sieci TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="5d888-104">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="5d888-105">Unikatowy adres usługi TCP/IP jest definiowany przez połączenie adres IP hosta i numer portu usługi do tworzenia punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="5d888-105">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="5d888-106"><xref:System.Net.Dns> Klasa dostarcza metody, które zwracają informacje dotyczące adresów sieciowych obsługiwanych przez urządzenie sieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="5d888-106">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="5d888-107">Gdy urządzenie sieci lokalnej ma więcej niż jednego adresu sieciowego, lub jeśli lokalny system obsługuje więcej niż jednego urządzenia sieciowego, **Dns** klasy zwraca informacje o wszystkich adresów sieci i aplikacji, musisz wybrać prawidłowe adres usługi.</span><span class="sxs-lookup"><span data-stu-id="5d888-107">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="5d888-108">Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług common; Aby uzyskać więcej informacji, zobacz [nazwę usługi i rejestru numer portu protokołu transportu](https://www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="5d888-108">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services; for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="5d888-109">Inne usługi można zarejestrowano numery portów z zakresu od 1024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="5d888-109">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="5d888-110">Poniższy przykład tworzy <xref:System.Net.IPEndPoint> dla serwera, łącząc pierwszy adres IP zwrócony przez **Dns** dla komputera hosta, numer portu wybranego z zakresu numerów portów zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="5d888-110">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
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
  
 <span data-ttu-id="5d888-111">Po lokalnym punktem końcowym jest określana, <xref:System.Net.Sockets.Socket> musi być skojarzony z tego punktu końcowego za pomocą <xref:System.Net.Sockets.Socket.Bind%2A> metody i zestawu do nasłuchiwania punktu końcowego za pomocą <xref:System.Net.Sockets.Socket.Listen%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5d888-111">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="5d888-112">**Powiąż** zgłasza wyjątek, jeśli konkretny kombinacji adres i port jest już używana.</span><span class="sxs-lookup"><span data-stu-id="5d888-112">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="5d888-113">W poniższym przykładzie pokazano kojarzenie **gniazda** z **IPEndPoint**.</span><span class="sxs-lookup"><span data-stu-id="5d888-113">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
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
  
 <span data-ttu-id="5d888-114">**Nasłuchiwania** metoda przyjmuje jeden parametr, który określa liczbę oczekujących połączeń **gniazda** są dozwolone przed zwróceniem błąd zajęty serwera do klienta nawiązującego połączenie.</span><span class="sxs-lookup"><span data-stu-id="5d888-114">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="5d888-115">W tym przypadku maksymalnie 100 klientami są umieszczane w kolejce połączenia zanim serwer zajęty odpowiedź jest zwracana do klienta o numerze 101.</span><span class="sxs-lookup"><span data-stu-id="5d888-115">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d888-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d888-116">See also</span></span>

- [<span data-ttu-id="5d888-117">Używanie synchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="5d888-117">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)
- [<span data-ttu-id="5d888-118">Używanie asynchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="5d888-118">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="5d888-119">Używanie gniazd klientów</span><span class="sxs-lookup"><span data-stu-id="5d888-119">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)
- [<span data-ttu-id="5d888-120">Instrukcje: Tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="5d888-120">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)
- [<span data-ttu-id="5d888-121">Gniazda</span><span class="sxs-lookup"><span data-stu-id="5d888-121">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
