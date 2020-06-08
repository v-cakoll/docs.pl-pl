---
title: Żądanie danych
description: Dowiedz się, jak podłączane protokoły umożliwiają tworzenie aplikacji korzystających z jednego interfejsu do pobierania danych z wielu protokołów.
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
ms.openlocfilehash: 19350d685a81d56657ca0a117d61b50ae24fab6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502187"
---
# <a name="requesting-data"></a><span data-ttu-id="0dfb3-103">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="0dfb3-103">Requesting Data</span></span>
<span data-ttu-id="0dfb3-104">Tworzenie aplikacji działających w rozproszonym środowisku operacyjnym dzisiejszej sieci Internet wymaga wydajnej, łatwej w użyciu metody do pobierania danych z zasobów wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-104">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="0dfb3-105">Protokoły podłączane umożliwiają tworzenie aplikacji korzystających z jednego interfejsu do pobierania danych z wielu protokołów internetowych.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-105">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="0dfb3-106">Przekazywanie i pobieranie danych z serwera internetowego</span><span class="sxs-lookup"><span data-stu-id="0dfb3-106">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="0dfb3-107">W przypadku prostych transakcji żądań i odpowiedzi <xref:System.Net.WebClient> Klasa zapewnia najłatwą metodę przekazywania danych do lub pobierania danych z serwera internetowego.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-107">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="0dfb3-108">**Klient WebClient** oferuje metody przekazywania i pobierania plików, wysyłania i otrzymywania strumieni oraz wysyłania bufora danych do serwera i otrzymywania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-108">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="0dfb3-109">**Klient WebClient** używa <xref:System.Net.WebRequest> klas i, aby nawiązać <xref:System.Net.WebResponse> rzeczywiste połączenia z zasobem internetowym, tak aby wszystkie zarejestrowane protokoły podłączane były dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-109">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="0dfb3-110">Aplikacje klienckie, które muszą wykonywać bardziej złożone transakcje żądania danych z serwerów przy użyciu klasy **WebRequest** i jej obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-110">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="0dfb3-111">**Żądanie WebRequest** hermetyzuje szczegóły dotyczące łączenia się z serwerem, wysyłania żądania i otrzymywania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-111">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="0dfb3-112">**WebRequest** to Klasa abstrakcyjna, która definiuje zestaw właściwości i metod, które są dostępne dla wszystkich aplikacji, które korzystają z protokołów podłączanych.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-112">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="0dfb3-113">Elementy podrzędne **żądania WebRequest**, takie jak <xref:System.Net.HttpWebRequest> , implementują właściwości i metody zdefiniowane przez **WebRequest** w sposób, który jest zgodny z bazowym protokołem.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-113">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="0dfb3-114">Klasa **WebRequest** tworzy wystąpienia obiektów podrzędnych **żądania WebRequest** zależnych od protokołu przy użyciu wartości identyfikatora URI przesłanej do metody, <xref:System.Net.WebRequest.Create%2A> Aby określić konkretne wystąpienie klasy pochodnej do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-114">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="0dfb3-115">Aplikacje wskazują, które elementy podrzędne **żądania WebRequest** mają być używane do obsługi żądania przez zarejestrowanie konstruktora elementu podrzędnego za pomocą <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-115">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="0dfb3-116">Do zasobu internetowego jest wykonywane żądanie wywołujące <xref:System.Net.WebRequest.GetResponse%2A> metodę w **żądaniu WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-116">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="0dfb3-117">Metoda **GetResponse** konstruuje żądanie specyficzne dla protokołu ze wszystkich właściwości **żądania WebRequest**, sprawia, że połączenie TCP lub UDP gniazda z serwerem i wysyła żądanie.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-117">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="0dfb3-118">W przypadku żądań wysyłających dane do serwera, takich jak żądania HTTP **post** lub FTP **Put** , <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> Metoda zawiera strumień sieciowy, do którego mają być wysyłane dane.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-118">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="0dfb3-119">Metoda **GetResponse** zwraca **WebResponse** specyficzny dla protokołu, który jest zgodny z **żądaniem WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="0dfb3-119">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="0dfb3-120">Klasa **WebResponse** jest również klasą abstrakcyjną, która definiuje właściwości i metody, które są dostępne dla wszystkich aplikacji, które korzystają z protokołów podłączanych.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-120">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="0dfb3-121">Elementy podrzędne **WebResponse** implementują te właściwości i metody dla bazowego protokołu.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-121">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="0dfb3-122"><xref:System.Net.HttpWebResponse>Klasa, na przykład implementuje klasę **WebResponse** dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-122">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="0dfb3-123">Dane zwrócone przez serwer są prezentowane aplikacji w strumieniu zwracanym przez <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-123">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0dfb3-124">Tego strumienia można użyć jak dowolnego innego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0dfb3-124">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="0dfb3-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0dfb3-125">See also</span></span>

- [<span data-ttu-id="0dfb3-126">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0dfb3-126">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="0dfb3-127">Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia</span><span class="sxs-lookup"><span data-stu-id="0dfb3-127">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="0dfb3-128">Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest</span><span class="sxs-lookup"><span data-stu-id="0dfb3-128">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
