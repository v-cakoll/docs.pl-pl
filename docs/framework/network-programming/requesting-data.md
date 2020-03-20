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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047314"
---
# <a name="requesting-data"></a><span data-ttu-id="1535e-102">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="1535e-102">Requesting Data</span></span>
<span data-ttu-id="1535e-103">Tworzenie aplikacji, które działają w rozproszonym środowisku operacyjnym dzisiejszego Internetu wymaga wydajnej, łatwej w użyciu metody pobierania danych z zasobów wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="1535e-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="1535e-104">Protokoły podłączane umożliwiają tworzenie aplikacji korzystających z jednego interfejsu do pobierania danych z wielu protokołów internetowych.</span><span class="sxs-lookup"><span data-stu-id="1535e-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="1535e-105">Przekazywanie i pobieranie danych z serwera internetowego</span><span class="sxs-lookup"><span data-stu-id="1535e-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="1535e-106">W przypadku prostych transakcji żądań i odpowiedzi <xref:System.Net.WebClient> klasa zapewnia najprostszą metodę przekazywania danych do lub pobierania danych z serwera internetowego.</span><span class="sxs-lookup"><span data-stu-id="1535e-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="1535e-107">**WebClient** udostępnia metody przekazywania i pobierania plików, wysyłania i odbierania strumieni oraz wysyłania buforu danych do serwera i odbierania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1535e-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="1535e-108">**WebClient** używa <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klas do tworzenia rzeczywistych połączeń z zasobem internetowym, więc każdy zarejestrowany protokół pluggable jest dostępny do użycia.</span><span class="sxs-lookup"><span data-stu-id="1535e-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="1535e-109">Aplikacje klienckie, które muszą dokonać bardziej złożonych transakcji żądają danych z serwerów przy użyciu **klasy WebRequest** i jej elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1535e-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="1535e-110">**WebRequest** hermetyzuje szczegóły łączenia się z serwerem, wysyłania żądania i odbierania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1535e-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="1535e-111">**WebRequest** to klasa abstrakcyjna, która definiuje zestaw właściwości i metod, które są dostępne dla wszystkich aplikacji, które używają protokołów podłączanych.</span><span class="sxs-lookup"><span data-stu-id="1535e-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="1535e-112">Elementy podrzędne **WebRequest** <xref:System.Net.HttpWebRequest>, takie jak , implementują właściwości i metody zdefiniowane przez **WebRequest** w sposób zgodny z podstawowym protokołem.</span><span class="sxs-lookup"><span data-stu-id="1535e-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="1535e-113">**Klasa WebRequest** tworzy specyficzne dla protokołu wystąpienia elementów podrzędnych **WebRequest,** przy <xref:System.Net.WebRequest.Create%2A> użyciu wartości identyfikatora URI przekazany do jego metody w celu określenia określonego wystąpienia klasy pochodnej do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="1535e-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="1535e-114">Aplikacje wskazują, które **WebRequest** element podrzędny powinien być używany do <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> obsługi żądania, rejestrując konstruktora podrzędnego z metodą.</span><span class="sxs-lookup"><span data-stu-id="1535e-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="1535e-115">Żądanie jest dokonywane do zasobu <xref:System.Net.WebRequest.GetResponse%2A> internetowego, wywołując metodę w **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="1535e-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="1535e-116">**Metoda GetResponse** konstruuje żądanie specyficzne dla protokołu z właściwości **WebRequest**, sprawia, że TCP lub UDP gniazdo połączenia z serwerem i wysyła żądanie.</span><span class="sxs-lookup"><span data-stu-id="1535e-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="1535e-117">W przypadku żądań, które wysyłają dane do serwera, takich <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> jak http **post** lub ftp **put** żądań, metoda zapewnia strumień sieciowy, w którym do wysyłania danych.</span><span class="sxs-lookup"><span data-stu-id="1535e-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="1535e-118">**Metoda GetResponse** zwraca **webresponse** specyficzne dla protokołu, który pasuje **do WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="1535e-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="1535e-119">**Klasa WebResponse** jest również klasą abstrakcyjną, która definiuje właściwości i metody, które są dostępne dla wszystkich aplikacji korzystających z protokołów podłączanych.</span><span class="sxs-lookup"><span data-stu-id="1535e-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="1535e-120">**Elementy podrzędne WebResponse** implementują te właściwości i metody dla protokołu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="1535e-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="1535e-121">Klasa, <xref:System.Net.HttpWebResponse> na przykład, implementuje **WebResponse** klasy http.</span><span class="sxs-lookup"><span data-stu-id="1535e-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="1535e-122">Dane zwracane przez serwer są prezentowane do aplikacji <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> w strumieniu zwrócone przez metodę.</span><span class="sxs-lookup"><span data-stu-id="1535e-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1535e-123">Można użyć tego strumienia, jak każdy inny, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1535e-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="1535e-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1535e-124">See also</span></span>

- [<span data-ttu-id="1535e-125">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1535e-125">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="1535e-126">Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia</span><span class="sxs-lookup"><span data-stu-id="1535e-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="1535e-127">Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest</span><span class="sxs-lookup"><span data-stu-id="1535e-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
