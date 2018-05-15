---
title: Używanie klienta gniazd
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 458e67861bfd40b69f7a6f756ddee8be433e9e2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-client-sockets"></a><span data-ttu-id="15af2-102">Używanie klienta gniazd</span><span class="sxs-lookup"><span data-stu-id="15af2-102">Using Client Sockets</span></span>
<span data-ttu-id="15af2-103">Przed rozpoczęciem konwersacji za pośrednictwem <xref:System.Net.Sockets.Socket>, należy utworzyć potok danych pomiędzy aplikacją i urządzenia zdalnego.</span><span class="sxs-lookup"><span data-stu-id="15af2-103">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="15af2-104">Mimo że istnieją inne rodziny adresów sieci i protokołów, w tym przykładzie pokazano, jak można utworzyć połączenia TCP/IP do zdalnej usługi.</span><span class="sxs-lookup"><span data-stu-id="15af2-104">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="15af2-105">Protokół TCP/IP używa adresu sieciowego i numer portu usługi do jednoznacznej identyfikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="15af2-105">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="15af2-106">Adres sieciowy identyfikuje konkretnym urządzeniu w sieci. numer portu identyfikuje określonej usługi na tym urządzeniu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="15af2-106">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="15af2-107">Kombinacja portu adres i usługi sieci jest nazywana punktu końcowego, który jest reprezentowana w programie .NET Framework przez <xref:System.Net.EndPoint> klasy.</span><span class="sxs-lookup"><span data-stu-id="15af2-107">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="15af2-108">Element podrzędny **punktu końcowego** jest zdefiniowany dla każdego obsługiwana Rodzina adresów; rodziny adresów IP jest klasa <xref:System.Net.IPEndPoint>.</span><span class="sxs-lookup"><span data-stu-id="15af2-108">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="15af2-109"><xref:System.Net.Dns> Klasa udostępnia usługi nazwy domeny do aplikacji, które używają usługi internetowe TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="15af2-109">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="15af2-110"><xref:System.Net.Dns.Resolve%2A> Metoda odpytuje serwer DNS, aby zamapować nazwę przyjazną dla użytkownika domeny (na przykład "host.contoso.com") do numerycznego adresu internetowego (na przykład 192.168.1.1).</span><span class="sxs-lookup"><span data-stu-id="15af2-110">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="15af2-111">**Rozwiąż** zwraca <xref:System.Net.IPHostEntry> zawierający listę adresów i aliasów dla żądanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="15af2-111">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="15af2-112">W większości przypadków można użyć pierwszy zwrócony w adres <xref:System.Net.IPHostEntry.AddressList%2A> tablicy.</span><span class="sxs-lookup"><span data-stu-id="15af2-112">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="15af2-113">Poniższy kod pobiera <xref:System.Net.IPAddress> zawierający adres IP dla host.contoso.com serwera.</span><span class="sxs-lookup"><span data-stu-id="15af2-113">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="15af2-114">Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług wspólnej (Aby uzyskać więcej informacji, zobacz www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="15af2-114">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="15af2-115">Inne usługi można zarejestrować numery portów z zakresu od 1024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="15af2-115">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="15af2-116">Poniższy kod łączy adres IP host.contoso.com z numerem portu, aby utworzyć zdalny punkt końcowy dla połączenia.</span><span class="sxs-lookup"><span data-stu-id="15af2-116">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="15af2-117">Po określania adresu urządzenie zdalne i wybierając port do użycia na potrzeby połączenia, aplikacja może próbować nawiązać połączenie z urządzeniem zdalnym.</span><span class="sxs-lookup"><span data-stu-id="15af2-117">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="15af2-118">W poniższym przykładzie użyto istniejące **IPEndPoint** nawiązać połączenia z urządzeniem zdalnym i przechwytuje wszystkie wyjątki, które są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="15af2-118">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="15af2-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15af2-119">See Also</span></span>  
 [<span data-ttu-id="15af2-120">Używanie synchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="15af2-120">Using a Synchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [<span data-ttu-id="15af2-121">Używanie asynchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="15af2-121">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [<span data-ttu-id="15af2-122">Instrukcje: tworzenie gniazda</span><span class="sxs-lookup"><span data-stu-id="15af2-122">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [<span data-ttu-id="15af2-123">Gniazda</span><span class="sxs-lookup"><span data-stu-id="15af2-123">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
