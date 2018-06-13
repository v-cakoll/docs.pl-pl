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
manager: markl
ms.openlocfilehash: 8702f2329b262fc5c5965ae49365d46ba34091d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391176"
---
# <a name="managing-connections"></a><span data-ttu-id="e9794-102">Zarządzanie połączeniami</span><span class="sxs-lookup"><span data-stu-id="e9794-102">Managing Connections</span></span>
<span data-ttu-id="e9794-103">Aplikacje, które łączą się z zasobami danych przy użyciu protokołu HTTP można używać programu .NET Framework <xref:System.Net.ServicePoint> i <xref:System.Net.ServicePointManager> klasy można zarządzać połączenia z Internetem i pomóc im uzyskać optymalne skalowalność i wydajność.</span><span class="sxs-lookup"><span data-stu-id="e9794-103">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  
  
 <span data-ttu-id="e9794-104">**ServicePoint** klasa udostępnia aplikacji z punktem końcowym, z którym aplikacji może nawiązać połączenie dostępu do zasobów Internetu.</span><span class="sxs-lookup"><span data-stu-id="e9794-104">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="e9794-105">Każdy **ServicePoint** zawiera informacje, że pomaga zoptymalizować połączenia na internetowym serwerze za pomocą udostępniania informacji optymalizacji między połączenia w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="e9794-105">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="e9794-106">Każdy **ServicePoint** są identyfikowane przez zasób identyfikator URI (Uniform) i uporządkowane według fragmenty identyfikator i hosta schemat identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="e9794-106">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="e9794-107">Na przykład taką **ServicePoint** wystąpienia zapewni żądań identyfikatory URI http://www.contoso.com/index.htm i http://www.contoso.com/news.htm?date=today , ponieważ mają one tego samego identyfikatora schemat (http) i host fragmenty (www.contoso.com).</span><span class="sxs-lookup"><span data-stu-id="e9794-107">For example, the same **ServicePoint** instance would provide requests to the URIs http://www.contoso.com/index.htm and http://www.contoso.com/news.htm?date=today since they have the same scheme identifier (http) and host fragments (www.contoso.com).</span></span> <span data-ttu-id="e9794-108">Jeśli aplikacja już ma trwałe połączenie www.contoso.com serwera, używa tego połączenia do pobrania obu żądania, dzięki czemu nie trzeba tworzyć dwa połączenia.</span><span class="sxs-lookup"><span data-stu-id="e9794-108">If the application already has a persistent connection to the server www.contoso.com, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="e9794-109">**Element ServicePointManager** jest statycznej klasy, która zarządza tworzeniem i zniszczenie **ServicePoint** wystąpień.</span><span class="sxs-lookup"><span data-stu-id="e9794-109">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="e9794-110">**ServicePointManager —** tworzy **ServicePoint** gdy aplikacja żąda zasobu internetowego, który nie znajduje się w kolekcji istniejących **ServicePoint** wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e9794-110">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="e9794-111">**ServicePoint** zostaną zniszczone wystąpień, gdy przekraczają maksymalny czas bezczynności lub liczba istniejących **ServicePoint** wystąpień przekracza maksymalną liczbę **ServicePoint**wystąpień dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9794-111">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="e9794-112">Użytkownik może kontrolować zarówno maksymalny czas bezczynności i maksymalną liczbę **ServicePoint** wystąpień przez ustawienie <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> i <xref:System.Net.ServicePointManager.MaxServicePoints%2A> właściwości **ServicePointManager —**.</span><span class="sxs-lookup"><span data-stu-id="e9794-112">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="e9794-113">Liczba połączeń między klientem a serwerem może mieć znaczący wpływ na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9794-113">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="e9794-114">Domyślnie aplikacji przy użyciu <xref:System.Net.HttpWebRequest> klasa korzysta z maksymalnie dwóch połączeń trwałych do danego serwera, ale można ustawić maksymalną liczbę połączeń na podstawie określonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9794-114">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9794-115">Specyfikacja protokołu HTTP/1.1 ogranicza liczbę połączeń z aplikacji do dwóch połączeń na serwer.</span><span class="sxs-lookup"><span data-stu-id="e9794-115">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="e9794-116">Optymalna liczba połączeń zależy od rzeczywistych warunkach, w których jest uruchomiona aplikacja.</span><span class="sxs-lookup"><span data-stu-id="e9794-116">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="e9794-117">Zwiększa liczbę połączeń, które są dostępne dla aplikacji nie mogą wpływać na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9794-117">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="e9794-118">Aby określić wpływ więcej połączeń, Uruchamianie testów wydajnościowych różnicując liczbę połączeń.</span><span class="sxs-lookup"><span data-stu-id="e9794-118">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="e9794-119">Można zmienić liczbę połączeń używanych przez aplikację, zmieniając statycznych <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> właściwość **ServicePointManager —** klasy w czasie inicjowania aplikacji, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="e9794-119">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="e9794-120">Zmiana **ServicePointManager.DefaultConnectionLimit** właściwości nie wpływa na wcześniej zainicjowana **ServicePoint** wystąpień.</span><span class="sxs-lookup"><span data-stu-id="e9794-120">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="e9794-121">Poniższy kod ilustruje, Zmiana limitu połączeń na istniejącym **ServicePoint** serwera http://www.contoso.com do wartości przechowywanej w `newLimit`.</span><span class="sxs-lookup"><span data-stu-id="e9794-121">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server http://www.contoso.com to the value stored in `newLimit`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e9794-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9794-122">See Also</span></span>  
 [<span data-ttu-id="e9794-123">Grupowanie połączeń</span><span class="sxs-lookup"><span data-stu-id="e9794-123">Connection Grouping</span></span>](../../../docs/framework/network-programming/connection-grouping.md)  
 [<span data-ttu-id="e9794-124">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="e9794-124">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
