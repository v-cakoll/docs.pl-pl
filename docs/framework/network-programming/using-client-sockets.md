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
ms.openlocfilehash: b99720b9653b8454419acd35085bfe9a7ac4b5af
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171395"
---
# <a name="using-client-sockets"></a><span data-ttu-id="75bb8-102">Używanie gniazd klientów</span><span class="sxs-lookup"><span data-stu-id="75bb8-102">Using Client Sockets</span></span>
<span data-ttu-id="75bb8-103">Przed rozpoczęciem konwersacji za pośrednictwem <xref:System.Net.Sockets.Socket>, należy utworzyć potok danych między aplikacją i urządzenie zdalne.</span><span class="sxs-lookup"><span data-stu-id="75bb8-103">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="75bb8-104">Mimo że istnieją inne rodziny adresów sieciowych i protokołów, w tym przykładzie pokazano, jak utworzyć połączenie TCP/IP do usługi zdalnej.</span><span class="sxs-lookup"><span data-stu-id="75bb8-104">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="75bb8-105">Protokół TCP/IP używa adresu sieciowego i numer portu usługi do unikatowego identyfikowania usługi.</span><span class="sxs-lookup"><span data-stu-id="75bb8-105">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="75bb8-106">Adres sieciowy identyfikuje konkretnym urządzeniu w sieci. numer portu identyfikuje określonej usługi na tym urządzeniu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="75bb8-106">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="75bb8-107">Kombinacja portu adresu i usługi sieciowej jest nazywana punktu końcowego, która jest reprezentowana w .NET Framework według <xref:System.Net.EndPoint> klasy.</span><span class="sxs-lookup"><span data-stu-id="75bb8-107">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="75bb8-108">Element podrzędny **punktu końcowego** jest zdefiniowana dla każdego obsługiwane rodziny adresów; Rodzina adresów IP, klasa jest <xref:System.Net.IPEndPoint>.</span><span class="sxs-lookup"><span data-stu-id="75bb8-108">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="75bb8-109"><xref:System.Net.Dns> Klasa udostępnia usługi nazwy domeny dla aplikacji korzystających z usług internetowych TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="75bb8-109">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="75bb8-110"><xref:System.Net.Dns.Resolve%2A> Metoda odpytuje serwer DNS, aby zamapować nazwę przyjazną dla użytkownika domeny (na przykład "host.contoso.com") do numerycznego adresu internetowego (np. 192.168.1.1).</span><span class="sxs-lookup"><span data-stu-id="75bb8-110">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="75bb8-111">**Rozwiąż** zwraca <xref:System.Net.IPHostEntry> zawierający listę adresów i aliasy dla żądanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="75bb8-111">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="75bb8-112">W większości przypadków można użyć pierwszego adresu zwracane w <xref:System.Net.IPHostEntry.AddressList%2A> tablicy.</span><span class="sxs-lookup"><span data-stu-id="75bb8-112">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="75bb8-113">Poniższy kod pobiera <xref:System.Net.IPAddress> zawierające adres IP dla host.contoso.com serwera.</span><span class="sxs-lookup"><span data-stu-id="75bb8-113">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="75bb8-114">Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług common (Aby uzyskać więcej informacji, zobacz [nazwę usługi i rejestru numer portu protokołu transportu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="75bb8-114">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="75bb8-115">Inne usługi można zarejestrowano numery portów z zakresu od 1024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="75bb8-115">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="75bb8-116">Poniższy kod łączy adres IP dla host.contoso.com z numerem portu, aby utworzyć zdalnego punktu końcowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="75bb8-116">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="75bb8-117">Po określająca adres urządzenia zdalnego, a następnie wybierając port do użycia na potrzeby połączenia, aplikacja może próbować nawiązać połączenie z urządzeniem zdalnym.</span><span class="sxs-lookup"><span data-stu-id="75bb8-117">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="75bb8-118">W poniższym przykładzie użyto istniejącej **IPEndPoint** nawiązać połączenia z urządzeniem zdalnym i przechwytuje wszystkie wyjątki, które są generowane.</span><span class="sxs-lookup"><span data-stu-id="75bb8-118">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="75bb8-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75bb8-119">See also</span></span>

- [<span data-ttu-id="75bb8-120">Używanie synchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="75bb8-120">Using a Synchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)
- [<span data-ttu-id="75bb8-121">Używanie asynchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="75bb8-121">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="75bb8-122">Instrukcje: tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="75bb8-122">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)
- [<span data-ttu-id="75bb8-123">Gniazda</span><span class="sxs-lookup"><span data-stu-id="75bb8-123">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
