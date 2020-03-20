---
title: Używanie gniazd klientów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
ms.openlocfilehash: fe2ad55c3f60347369c0e92bc834d81d98f3870e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046956"
---
# <a name="using-client-sockets"></a><span data-ttu-id="95a5a-102">Używanie gniazd klientów</span><span class="sxs-lookup"><span data-stu-id="95a5a-102">Using Client Sockets</span></span>
<span data-ttu-id="95a5a-103">Przed rozpoczęciem konwersacji <xref:System.Net.Sockets.Socket>za pośrednictwem programów należy utworzyć potok danych między aplikacją a urządzeniem zdalnym.</span><span class="sxs-lookup"><span data-stu-id="95a5a-103">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="95a5a-104">Chociaż istnieją inne rodziny i protokoły adresów sieciowych, w tym przykładzie pokazano, jak utworzyć połączenie TCP/IP z usługą zdalną.</span><span class="sxs-lookup"><span data-stu-id="95a5a-104">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="95a5a-105">Protokół TCP/IP używa adresu sieciowego i numeru portu usługi do jednoznacznej identyfikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="95a5a-105">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="95a5a-106">Adres sieciowy identyfikuje określone urządzenie w sieci; numer portu identyfikuje określoną usługę na tym urządzeniu, z którą ma się łączyć.</span><span class="sxs-lookup"><span data-stu-id="95a5a-106">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="95a5a-107">Połączenie adresu sieciowego i portu usługi jest nazywany punktem końcowym, który <xref:System.Net.EndPoint> jest reprezentowany w programie .NET Framework przez klasę.</span><span class="sxs-lookup"><span data-stu-id="95a5a-107">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="95a5a-108">Element podrzędny **programu EndPoint** jest zdefiniowany dla każdej obsługiwanej rodziny adresów; dla rodziny adresów IP, <xref:System.Net.IPEndPoint>klasa jest .</span><span class="sxs-lookup"><span data-stu-id="95a5a-108">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="95a5a-109">Klasa <xref:System.Net.Dns> udostępnia usługi nazw domen aplikacjom korzystającym z usług internetowych TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="95a5a-109">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="95a5a-110">Metoda <xref:System.Net.Dns.Resolve%2A> wysyła zapytanie do serwera DNS o mapowanie przyjaznej dla użytkownika nazwy domeny (takiej jak "host.contoso.com") na numeryczny adres internetowy (na przykład 192.168.1.1).</span><span class="sxs-lookup"><span data-stu-id="95a5a-110">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="95a5a-111">**Resolve** zwraca <xref:System.Net.IPHostEntry> listę adresów i aliasów żądanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="95a5a-111">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="95a5a-112">W większości przypadków można użyć pierwszego adresu <xref:System.Net.IPHostEntry.AddressList%2A> zwróconego w tablicy.</span><span class="sxs-lookup"><span data-stu-id="95a5a-112">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="95a5a-113">Poniższy kod <xref:System.Net.IPAddress> otrzymuje adres IP serwera host.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="95a5a-113">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="95a5a-114">Urząd numerów przypisanych do Internetu (Iana) definiuje numery portów dla usług wspólnych (aby uzyskać więcej informacji, zobacz [Rejestracja numeru portu usługi i protokołu transportu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="95a5a-114">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="95a5a-115">Inne usługi mogą mieć zarejestrowane numery portów w zakresie od 1024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="95a5a-115">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="95a5a-116">Poniższy kod łączy adres IP dla host.contoso.com z numerem portu w celu utworzenia zdalnego punktu końcowego dla połączenia.</span><span class="sxs-lookup"><span data-stu-id="95a5a-116">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="95a5a-117">Po określeniu adresu urządzenia zdalnego i wybraniu portu do użycia dla połączenia, aplikacja może podjąć próbę nawiązania połączenia z urządzeniem zdalnym.</span><span class="sxs-lookup"><span data-stu-id="95a5a-117">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="95a5a-118">Poniższy przykład używa istniejącego **ipendpoint** do łączenia się z urządzeniem zdalnym i połowy wszelkich wyjątków, które są generowane.</span><span class="sxs-lookup"><span data-stu-id="95a5a-118">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="95a5a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95a5a-119">See also</span></span>

- [<span data-ttu-id="95a5a-120">Używanie synchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="95a5a-120">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="95a5a-121">Używanie asynchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="95a5a-121">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="95a5a-122">Instrukcje: tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="95a5a-122">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="95a5a-123">Gniazda</span><span class="sxs-lookup"><span data-stu-id="95a5a-123">Sockets</span></span>](sockets.md)
