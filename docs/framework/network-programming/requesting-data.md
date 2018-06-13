---
title: Żądanie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sending data
- WebRequest class, sending and receiving data
- requesting data from Internet, about requesting data
- WebClient class, sending and receiving data
- network, requesting data
- receiving data
- sending data, about sending data
- response to Internet request, about responding to Internet requests
- data requests
- receiving data, about receiving data
- Internet, requesting data
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 166a076eae69b351248bc67570cdaf50b43ab95c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396301"
---
# <a name="requesting-data"></a><span data-ttu-id="c207d-102">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="c207d-102">Requesting Data</span></span>
<span data-ttu-id="c207d-103">Tworzenie aplikacji uruchamianych w rozproszonym środowisku operacyjnym współczesnych Internet wymaga wydajne, łatwy w użyciu metody do pobierania danych z zasoby wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="c207d-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="c207d-104">Protokoły Plug umożliwiają tworzenie aplikacji korzystających z jednego interfejsu do pobierania danych z wielu protokołów internetowych.</span><span class="sxs-lookup"><span data-stu-id="c207d-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="c207d-105">Przekazywanie i pobieranie danych z serwera internetowego</span><span class="sxs-lookup"><span data-stu-id="c207d-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="c207d-106">Proste żądania i odpowiedzi transakcji <xref:System.Net.WebClient> klasy zapewnia najprostszą przekazywanie danych do lub pobieranie danych z serwera internetowego.</span><span class="sxs-lookup"><span data-stu-id="c207d-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="c207d-107">**WebClient** udostępnia metody, przekazywanie i pobieranie plików, wysyłania i odbierania strumieni i wysyłania buforu danych do serwera i odbierania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="c207d-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="c207d-108">**WebClient** używa <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy, do rzeczywistych połączeń z zasobem internetowym, powiększając wszelkie zarejestrowane protokołu podłączanej jest dostępny do użytku.</span><span class="sxs-lookup"><span data-stu-id="c207d-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="c207d-109">Aplikacje klienckie, które należy podjąć bardziej złożonej transakcji żądanie danych z serwerów za pomocą **WebRequest** klasy i jego obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c207d-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="c207d-110">**WebRequest** hermetyzuje szczegóły połączenia z serwerem, wysyłania żądania i odbierania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="c207d-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="c207d-111">**WebRequest** jest klasą abstrakcyjną, który definiuje zestaw właściwości i metod, które są dostępne dla wszystkich aplikacji, które używają protokołów podłączany.</span><span class="sxs-lookup"><span data-stu-id="c207d-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="c207d-112">Elementy podrzędne elementu **WebRequest**, takich jak <xref:System.Net.HttpWebRequest>, implementować właściwości i metody zdefiniowane przez **WebRequest** w taki sposób, który jest zgodny z protokołem podstawowej.</span><span class="sxs-lookup"><span data-stu-id="c207d-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="c207d-113">**WebRequest** klasy tworzy wystąpienia oparte na protokole **WebRequest** elementy podrzędne, używając wartości identyfikatora URI przekazane do jego <xref:System.Net.WebRequest.Create%2A> metodę, aby określić określonych-klas pochodnych wystąpienie do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="c207d-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="c207d-114">Wskazać aplikacje, które **WebRequest** obiekt podrzędny powinien być używany do obsługi żądania, rejestrując konstruktora obiektu podrzędnego z <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c207d-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="c207d-115">Żądań z zasobem internetowym wywołując <xref:System.Net.WebRequest.GetResponse%2A> metoda **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="c207d-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="c207d-116">**GetResponse** metoda tworzy żądanie oparte na protokole z właściwości **WebRequest**, sprawia, że połączenie gniazda TCP lub UDP do serwera i wysyła żądanie.</span><span class="sxs-lookup"><span data-stu-id="c207d-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="c207d-117">Dla żądania, które wysyłają dane do serwera, takich jak HTTP **Post** lub FTP **Put** żądania, <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> metoda zapewnia strumienia sieci przesyłania danych.</span><span class="sxs-lookup"><span data-stu-id="c207d-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="c207d-118">**GetResponse** metoda zwraca wartość określonego protokołu **WebResponse** odpowiadającego **WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="c207d-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="c207d-119">**WebResponse** klasa również jest klasą abstrakcyjną, która definiuje właściwości i metody, które są dostępne dla wszystkich aplikacji, które używają protokołów podłączany.</span><span class="sxs-lookup"><span data-stu-id="c207d-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="c207d-120">**WebResponse** obiektów podrzędnych implementacji tych właściwości i metody dla podstawowy protokół.</span><span class="sxs-lookup"><span data-stu-id="c207d-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="c207d-121"><xref:System.Net.HttpWebResponse> , Na przykład klasa implementuje **WebResponse** klasy dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c207d-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="c207d-122">Danych zwróconych przez serwer w odpowiedzi na tę aplikację w Strumień zwrócony przez <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c207d-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c207d-123">Można użyć tego strumienia, jak każdy inny, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c207d-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="c207d-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c207d-124">See Also</span></span>  
 [<span data-ttu-id="c207d-125">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c207d-125">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="c207d-126">Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia</span><span class="sxs-lookup"><span data-stu-id="c207d-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)  
 [<span data-ttu-id="c207d-127">Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest</span><span class="sxs-lookup"><span data-stu-id="c207d-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
