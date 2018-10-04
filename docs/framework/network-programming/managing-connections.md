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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1e4eb6c88bfad132f9e974445adf9ae0d6531f57
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48782210"
---
# <a name="managing-connections"></a><span data-ttu-id="078c4-102">Zarządzanie połączeniami</span><span class="sxs-lookup"><span data-stu-id="078c4-102">Managing Connections</span></span>
<span data-ttu-id="078c4-103">Aplikacje, które używają protokołu HTTP do łączenia z zasobami danych można używać programu .NET Framework <xref:System.Net.ServicePoint> i <xref:System.Net.ServicePointManager> klasy do zarządzania połączenia z Internetem i aby pomóc im osiągnięcia optymalnej skali i wydajności.</span><span class="sxs-lookup"><span data-stu-id="078c4-103">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  
  
 <span data-ttu-id="078c4-104">**ServicePoint** klasa udostępnia aplikacji przy użyciu punktu końcowego, do której aplikacji można podłączyć do dostępu do zasobów internetowych.</span><span class="sxs-lookup"><span data-stu-id="078c4-104">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="078c4-105">Każdy **ServicePoint** zawiera informacje, że pomaga zoptymalizować połączenia z serwerem internetowym, udostępniając informacje o optymalizacji między połączeniami, aby zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="078c4-105">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="078c4-106">Każdy **ServicePoint** jest określana przez jednolite zasobów identyfikator (URI), a następnie jest dzielony na kategorie zgodnie z fragmentów identyfikator i hosta schemat identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="078c4-106">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="078c4-107">Na przykład takie same **ServicePoint** wystąpienia zapewni żądań identyfikatory URI `http://www.contoso.com/index.htm` i `http://www.contoso.com/news.htm?date=today` ponieważ mają one ten sam identyfikator schemat (http) i host fragmentów (`www.contoso.com`).</span><span class="sxs-lookup"><span data-stu-id="078c4-107">For example, the same **ServicePoint** instance would provide requests to the URIs `http://www.contoso.com/index.htm` and `http://www.contoso.com/news.htm?date=today` since they have the same scheme identifier (http) and host fragments (`www.contoso.com`).</span></span> <span data-ttu-id="078c4-108">Jeśli aplikacja już ma trwałe połączenie z serwerem `www.contoso.com`, używa tego połączenia można pobrać zarówno w przypadku żądań, unikając konieczności tworzenia dwa połączenia.</span><span class="sxs-lookup"><span data-stu-id="078c4-108">If the application already has a persistent connection to the server `www.contoso.com`, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="078c4-109">**ServicePointManager —** jest klasą statyczną, zarządza tworzeniem i niszczeniem **ServicePoint** wystąpień.</span><span class="sxs-lookup"><span data-stu-id="078c4-109">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="078c4-110">**ServicePointManager —** tworzy **ServicePoint** gdy aplikacja żąda zasobu internetowego, który nie znajduje się w kolekcji istniejących **ServicePoint** wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="078c4-110">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="078c4-111">**ServicePoint** wystąpienia są niszczone, gdy przekroczyły ich maksymalny czas bezczynności lub liczba istniejących **ServicePoint** wystąpień przekracza maksymalną liczbę **ServicePoint**wystąpień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="078c4-111">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="078c4-112">Można kontrolować maksymalny czas bezczynności i maksymalna liczba **ServicePoint** wystąpienia, ustawiając <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> i <xref:System.Net.ServicePointManager.MaxServicePoints%2A> właściwości **ServicePointManager —**.</span><span class="sxs-lookup"><span data-stu-id="078c4-112">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="078c4-113">Liczba połączeń między klientem i serwerem może mieć znaczący wpływ na przepływność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="078c4-113">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="078c4-114">Domyślnie aplikacji za pomocą <xref:System.Net.HttpWebRequest> klasa korzysta z maksymalnie dwóch połączeń trwałych na danym serwerze, ale można ustawić maksymalną liczbę połączeń, na podstawie poszczególnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="078c4-114">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="078c4-115">Specyfikacją HTTP/1.1 ogranicza liczbę połączeń z aplikacji do dwóch połączeń na serwer.</span><span class="sxs-lookup"><span data-stu-id="078c4-115">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="078c4-116">Optymalną liczbę połączeń, zależy od rzeczywistych warunków, w których jest uruchomiona aplikacja.</span><span class="sxs-lookup"><span data-stu-id="078c4-116">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="078c4-117">Zwiększa liczbę połączeń, które są dostępne dla aplikacji może nie mieć wpływ na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="078c4-117">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="078c4-118">Aby określić wpływ więcej połączeń, uruchom testy wydajności różnicując liczbę połączeń.</span><span class="sxs-lookup"><span data-stu-id="078c4-118">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="078c4-119">Można zmienić liczbę połączeń używanych przez aplikację, zmieniając statycznej <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> właściwość **ServicePointManager —** klasy podczas inicjowania aplikacji, jak pokazano w następującym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="078c4-119">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="078c4-120">Zmiana **ServicePointManager.DefaultConnectionLimit** właściwość nie ma wpływu na wcześniej zainicjowane **ServicePoint** wystąpień.</span><span class="sxs-lookup"><span data-stu-id="078c4-120">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="078c4-121">Poniższy kod przedstawia zmiany limitu połączeń na istniejącym **ServicePoint** serwera `http://www.contoso.com` na wartość przechowywaną w `newLimit`.</span><span class="sxs-lookup"><span data-stu-id="078c4-121">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server `http://www.contoso.com` to the value stored in `newLimit`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="078c4-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="078c4-122">See Also</span></span>  
 [<span data-ttu-id="078c4-123">Grupowanie połączeń</span><span class="sxs-lookup"><span data-stu-id="078c4-123">Connection Grouping</span></span>](../../../docs/framework/network-programming/connection-grouping.md)  
 [<span data-ttu-id="078c4-124">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="078c4-124">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
