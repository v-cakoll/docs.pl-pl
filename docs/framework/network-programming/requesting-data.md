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
ms.openlocfilehash: 4e93b9395e92ff4c1c153f53e0f40ff18c12416a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228513"
---
# <a name="requesting-data"></a><span data-ttu-id="6819e-102">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="6819e-102">Requesting Data</span></span>
<span data-ttu-id="6819e-103">Tworzenie aplikacji działających w rozproszonym środowisku operacyjnym Internet współczesnych wymaga wydajne i łatwy w użyciu metody pobierania danych z wszystkich typów zasobów.</span><span class="sxs-lookup"><span data-stu-id="6819e-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="6819e-104">Podłączanych protokołów umożliwiają tworzenie aplikacji korzystających z jednego interfejsu do pobierania danych z wielu protokołów internetowych.</span><span class="sxs-lookup"><span data-stu-id="6819e-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="6819e-105">Przekazywanie i pobieranie danych z serwera internetowego</span><span class="sxs-lookup"><span data-stu-id="6819e-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="6819e-106">Dla prostego żądania i odpowiedzi transakcji <xref:System.Net.WebClient> klasy zapewnia najprostszą przekazywanie danych do lub pobieranie danych z serwera internetowego.</span><span class="sxs-lookup"><span data-stu-id="6819e-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="6819e-107">**Usługa WebClient** zawiera metody służące do przekazywania i pobierania plików, wysyłania i odbierania strumieni i wysyłania bufor danych do serwera i odbierania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="6819e-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="6819e-108">**Usługa WebClient** używa <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy, aby tworzyć rzeczywiste połączenia z zasobem internetowym, co zarejestrowany dowolny protokół podłączania jest dostępny do użytku.</span><span class="sxs-lookup"><span data-stu-id="6819e-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="6819e-109">Aplikacje klienckie, które muszą stosować bardziej złożone dane żądania transakcji z serwerów za pomocą **WebRequest** klasy i jego obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="6819e-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="6819e-110">**WebRequest** hermetyzuje szczegóły połączenia z serwerem, wysyłania żądania i odbierania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="6819e-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="6819e-111">**WebRequest** jest klasą abstrakcyjną, który definiuje zestaw właściwości i metod, które są dostępne dla wszystkich aplikacji, które za pomocą podłączanych protokołów.</span><span class="sxs-lookup"><span data-stu-id="6819e-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="6819e-112">Elementy podrzędne **WebRequest**, takich jak <xref:System.Net.HttpWebRequest>, implementować właściwości i metody zdefiniowane przez **WebRequest** w sposób, który jest zgodny z podstawowym protokole.</span><span class="sxs-lookup"><span data-stu-id="6819e-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="6819e-113">**WebRequest** klasy tworzy wystąpienia oparte na protokole **WebRequest** elementy podrzędne, używając wartości identyfikatora URI przekazywany do jego <xref:System.Net.WebRequest.Create%2A> metodę pozwala ustalić określonej klasy pochodnej wystąpienie do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="6819e-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="6819e-114">Wskazać aplikacje, które **WebRequest** podrzędny powinien być używany do obsługi żądania, rejestrując elementów podrzędnych konstruktora z <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6819e-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="6819e-115">Żądania z zasobem internetowym, wywołując <xref:System.Net.WebRequest.GetResponse%2A> metody **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="6819e-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="6819e-116">**Metody GetResponse** metoda konstrukcje żądania związane z protokołem we właściwościach **WebRequest**sprawia, że połączenie gniazda TCP lub UDP do serwera i wysyła żądanie.</span><span class="sxs-lookup"><span data-stu-id="6819e-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="6819e-117">Dla żądań, które wysyłają dane do serwera, takich jak HTTP **wpis** lub FTP **umieścić** żądania, <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> metoda zapewnia strumienia sieci, w której chcesz wysłać dane.</span><span class="sxs-lookup"><span data-stu-id="6819e-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="6819e-118">**Metody GetResponse** metoda zwraca związane z protokołem **elementu WebResponse** odpowiadający **WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="6819e-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="6819e-119">**Elementu WebResponse** klasy jest również klasę abstrakcyjną, która definiuje właściwości i metody, które są dostępne dla wszystkich aplikacji, które za pomocą podłączanych protokołów.</span><span class="sxs-lookup"><span data-stu-id="6819e-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="6819e-120">**Elementu WebResponse** elementów potomnych zaimplementować te właściwości i metody dla podstawowych protokołów.</span><span class="sxs-lookup"><span data-stu-id="6819e-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="6819e-121"><xref:System.Net.HttpWebResponse> Klasy, na przykład implementuje **elementu WebResponse** klasy do obsługi protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="6819e-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="6819e-122">Dane zwrócone przez serwer jest prezentowana w aplikacji w Strumień zwrócony przez <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6819e-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6819e-123">Można użyć tego strumienia, jak każdy inny, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6819e-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="6819e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6819e-124">See also</span></span>

- [<span data-ttu-id="6819e-125">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6819e-125">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
- [<span data-ttu-id="6819e-126">Instrukcje: Żądanie strony internetowej i pobieranie wyników jako Stream</span><span class="sxs-lookup"><span data-stu-id="6819e-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="6819e-127">Instrukcje: Pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest</span><span class="sxs-lookup"><span data-stu-id="6819e-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
