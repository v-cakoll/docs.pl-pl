---
title: Zarządzanie połączeniami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, connections
- HTTP, classes for connecting
- requesting data from Internet, connections
- sending data, connections
- receiving data, connections
- ServicePoint class, about ServicePoint class
- response to Internet request, connections
- connections [.NET Framework], classes
- network resources, connections
- downloading Internet resources, connections
- ServicePointManager class, about ServicePointManager class
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
ms.openlocfilehash: 2b7b54ab569a3f03363b2f30bf595c2087b9fe70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963954"
---
# <a name="managing-connections"></a><span data-ttu-id="6f6cd-102">Zarządzanie połączeniami</span><span class="sxs-lookup"><span data-stu-id="6f6cd-102">Managing Connections</span></span>
<span data-ttu-id="6f6cd-103">Aplikacje korzystające z protokołu HTTP do łączenia się z zasobami danych mogą używać <xref:System.Net.ServicePoint> .NET Framework <xref:System.Net.ServicePointManager> i klas do zarządzania połączeniami z Internetem, aby ułatwić im osiągnięcie optymalnej skali i wydajności.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-103">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  
  
 <span data-ttu-id="6f6cd-104">Klasa **ServicePoint** zapewnia aplikację z punktem końcowym, do którego aplikacja może połączyć się z dostępem do zasobów internetowych.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-104">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="6f6cd-105">Każdy **ServicePoint** zawiera informacje pomagające zoptymalizować połączenia z serwerem internetowym przez udostępnienie informacji o optymalizacji między połączeniami w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-105">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="6f6cd-106">Każdy **ServicePoint** jest identyfikowany przez Uniform Resource Identifier (URI) i jest kategoryzowany według identyfikatora schematu i fragmentów hosta identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-106">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="6f6cd-107">Na przykład to samo wystąpienie **ServicePoint** będzie dostarczać żądania do identyfikatorów URI `http://www.contoso.com/index.htm` , `http://www.contoso.com/news.htm?date=today` ponieważ mają one ten sam identyfikator schematu (http) i fragmenty hosta (`www.contoso.com`).</span><span class="sxs-lookup"><span data-stu-id="6f6cd-107">For example, the same **ServicePoint** instance would provide requests to the URIs `http://www.contoso.com/index.htm` and `http://www.contoso.com/news.htm?date=today` since they have the same scheme identifier (http) and host fragments (`www.contoso.com`).</span></span> <span data-ttu-id="6f6cd-108">Jeśli aplikacja ma już stałe połączenie z serwerem `www.contoso.com`, używa tego połączenia do pobierania obu żądań, unikając konieczności tworzenia dwóch połączeń.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-108">If the application already has a persistent connection to the server `www.contoso.com`, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="6f6cd-109">ServicePointManager jest klasą statyczną, która zarządza tworzeniem i zniszczeniem wystąpień **ServicePoint** .</span><span class="sxs-lookup"><span data-stu-id="6f6cd-109">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="6f6cd-110">ServicePointManager tworzy **ServicePoint** , gdy aplikacja żąda zasobu internetowego, który nie znajduje się w kolekcji istniejących wystąpień **ServicePoint** .</span><span class="sxs-lookup"><span data-stu-id="6f6cd-110">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="6f6cd-111">Wystąpienia **ServicePoint** są niszczone po przekroczeniu maksymalnego czasu bezczynności lub liczby istniejących wystąpień **ServicePoint** przekraczających maksymalną liczbę wystąpień **ServicePoint** dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-111">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="6f6cd-112">Można kontrolować zarówno domyślny maksymalny czas bezczynności, jak i maksymalną liczbę wystąpień **ServicePoint** przez ustawienie <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> właściwości i <xref:System.Net.ServicePointManager.MaxServicePoints%2A> w ServicePointManager.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-112">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="6f6cd-113">Liczba połączeń między klientem a serwerem może mieć znaczący wpływ na przepływność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-113">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="6f6cd-114">Domyślnie aplikacja używająca <xref:System.Net.HttpWebRequest> klasy używa maksymalnie dwóch trwałych połączeń z danym serwerem, ale można ustawić maksymalną liczbę połączeń dla poszczególnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-114">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f6cd-115">Specyfikacja protokołu HTTP/1.1 ogranicza liczbę połączeń z aplikacji do dwóch połączeń na serwer.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-115">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="6f6cd-116">Optymalna liczba połączeń zależy od rzeczywistych warunków, w których działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-116">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="6f6cd-117">Zwiększenie liczby połączeń dostępnych dla aplikacji może nie wpływać na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-117">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="6f6cd-118">Aby określić wpływ większej liczby połączeń, należy uruchomić testy wydajnościowe, zmieniając liczbę połączeń.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-118">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="6f6cd-119">Można zmienić liczbę połączeń używanych przez aplikację, zmieniając właściwość statyczną <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> w klasie ServicePointManager podczas inicjowania aplikacji, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-119">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="6f6cd-120">Zmiana właściwości **ServicePointManager. DefaultConnectionLimit** nie wpływa na wcześniej zainicjowane wystąpienia **ServicePoint** .</span><span class="sxs-lookup"><span data-stu-id="6f6cd-120">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="6f6cd-121">Poniższy kod ilustruje zmianę limitu połączeń na istniejącym **ServicePoint** dla serwera `http://www.contoso.com` na wartość przechowywaną w `newLimit`systemie.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-121">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server `http://www.contoso.com` to the value stored in `newLimit`.</span></span>  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f6cd-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f6cd-122">See also</span></span>

- [<span data-ttu-id="6f6cd-123">Grupowanie połączeń</span><span class="sxs-lookup"><span data-stu-id="6f6cd-123">Connection Grouping</span></span>](../../../docs/framework/network-programming/connection-grouping.md)
- [<span data-ttu-id="6f6cd-124">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="6f6cd-124">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
