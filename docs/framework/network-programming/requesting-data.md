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
ms.openlocfilehash: 1f367caf7656a83597b6262a5746686df15d33b4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047314"
---
# <a name="requesting-data"></a><span data-ttu-id="65bf1-102">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="65bf1-102">Requesting Data</span></span>
<span data-ttu-id="65bf1-103">Tworzenie aplikacji działających w rozproszonym środowisku operacyjnym dzisiejszej sieci Internet wymaga wydajnej, łatwej w użyciu metody do pobierania danych z zasobów wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="65bf1-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="65bf1-104">Protokoły podłączane umożliwiają tworzenie aplikacji korzystających z jednego interfejsu do pobierania danych z wielu protokołów internetowych.</span><span class="sxs-lookup"><span data-stu-id="65bf1-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="65bf1-105">Przekazywanie i pobieranie danych z serwera internetowego</span><span class="sxs-lookup"><span data-stu-id="65bf1-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="65bf1-106">W przypadku prostych transakcji <xref:System.Net.WebClient> żądań i odpowiedzi Klasa zapewnia najłatwą metodę przekazywania danych do lub pobierania danych z serwera internetowego.</span><span class="sxs-lookup"><span data-stu-id="65bf1-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="65bf1-107">**Klient WebClient** oferuje metody przekazywania i pobierania plików, wysyłania i otrzymywania strumieni oraz wysyłania bufora danych do serwera i otrzymywania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="65bf1-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="65bf1-108">**Klient WebClient** używa <xref:System.Net.WebRequest> klas <xref:System.Net.WebResponse> i, aby nawiązać rzeczywiste połączenia z zasobem internetowym, tak aby wszystkie zarejestrowane protokoły podłączane były dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="65bf1-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="65bf1-109">Aplikacje klienckie, które muszą wykonywać bardziej złożone transakcje żądania danych z serwerów przy użyciu klasy **WebRequest** i jej obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="65bf1-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="65bf1-110">**Żądanie WebRequest** hermetyzuje szczegóły dotyczące łączenia się z serwerem, wysyłania żądania i otrzymywania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="65bf1-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="65bf1-111">**WebRequest** to Klasa abstrakcyjna, która definiuje zestaw właściwości i metod, które są dostępne dla wszystkich aplikacji, które korzystają z protokołów podłączanych.</span><span class="sxs-lookup"><span data-stu-id="65bf1-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="65bf1-112">Elementy podrzędne **żądania WebRequest**, takie jak <xref:System.Net.HttpWebRequest>, implementują właściwości i metody zdefiniowane przez **WebRequest** w sposób, który jest zgodny z bazowym protokołem.</span><span class="sxs-lookup"><span data-stu-id="65bf1-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="65bf1-113">Klasa **WebRequest** tworzy wystąpienia obiektów podrzędnych **żądania WebRequest** zależnych od protokołu przy użyciu wartości identyfikatora URI <xref:System.Net.WebRequest.Create%2A> przesłanej do metody, aby określić konkretne wystąpienie klasy pochodnej do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="65bf1-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="65bf1-114">Aplikacje wskazują, które elementy podrzędne **żądania WebRequest** mają być używane do obsługi żądania przez zarejestrowanie konstruktora elementu podrzędnego za pomocą <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="65bf1-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="65bf1-115">Do zasobu internetowego jest wykonywane żądanie wywołujące <xref:System.Net.WebRequest.GetResponse%2A> metodę w **żądaniu WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="65bf1-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="65bf1-116">Metoda **GetResponse** konstruuje żądanie specyficzne dla protokołu ze wszystkich właściwości **żądania WebRequest**, sprawia, że połączenie TCP lub UDP gniazda z serwerem i wysyła żądanie.</span><span class="sxs-lookup"><span data-stu-id="65bf1-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="65bf1-117">W przypadku żądań wysyłających dane do serwera, takich jak <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> żądania HTTP **post** lub FTP **Put** , Metoda zawiera strumień sieciowy, do którego mają być wysyłane dane.</span><span class="sxs-lookup"><span data-stu-id="65bf1-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="65bf1-118">Metoda **GetResponse** zwraca **WebResponse** specyficzny dla protokołu, który jest zgodny z **żądaniem WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="65bf1-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="65bf1-119">Klasa **WebResponse** jest również klasą abstrakcyjną, która definiuje właściwości i metody, które są dostępne dla wszystkich aplikacji, które korzystają z protokołów podłączanych.</span><span class="sxs-lookup"><span data-stu-id="65bf1-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="65bf1-120">Elementy podrzędne **WebResponse** implementują te właściwości i metody dla bazowego protokołu.</span><span class="sxs-lookup"><span data-stu-id="65bf1-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="65bf1-121">Klasa, na przykład implementuje klasę WebResponse dla protokołu HTTP. <xref:System.Net.HttpWebResponse></span><span class="sxs-lookup"><span data-stu-id="65bf1-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="65bf1-122">Dane zwrócone przez serwer są prezentowane aplikacji w strumieniu zwracanym przez <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="65bf1-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="65bf1-123">Tego strumienia można użyć jak dowolnego innego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="65bf1-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="65bf1-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65bf1-124">See also</span></span>

- [<span data-ttu-id="65bf1-125">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="65bf1-125">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="65bf1-126">Instrukcje: Zażądaj strony sieci Web i Pobierz wyniki jako strumień</span><span class="sxs-lookup"><span data-stu-id="65bf1-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="65bf1-127">Instrukcje: Pobieranie WebResponse specyficznych dla protokołu, które pasują do żądania sieci</span><span class="sxs-lookup"><span data-stu-id="65bf1-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
