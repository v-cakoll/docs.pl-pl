---
title: Stosowanie strumieni w sieci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, streams
- Networking
- response to Internet request, streams
- network resources, stream capabilities
- receiving data, stream capabilities
- Network Resources
- sending data, stream capabilities
- downloading Internet resources, streams
- streams, capabilities
- Internet, streams
- streams
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
ms.openlocfilehash: aa3fc56dc461d4fe22e2ff391f3561d8834128d8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046879"
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="27882-102">Stosowanie strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="27882-102">Using Streams on the Network</span></span>
<span data-ttu-id="27882-103">Zasoby sieciowe są reprezentowane w .NET Framework jako strumienie.</span><span class="sxs-lookup"><span data-stu-id="27882-103">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="27882-104">Traktując strumienie ogólnie, .NET Framework oferuje następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="27882-104">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
- <span data-ttu-id="27882-105">Typowy sposób wysyłania i odbierania danych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="27882-105">A common way to send and receive Web data.</span></span> <span data-ttu-id="27882-106">Bez względu na rzeczywistą zawartość pliku — HTML, XML lub coś innego — aplikacja będzie używać <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> programu oraz <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> do wysyłania i odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="27882-106">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
- <span data-ttu-id="27882-107">Zgodność ze strumieniami w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27882-107">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="27882-108">Strumienie są używane w całym .NET Framework, który ma rozbudowaną infrastrukturę do ich obsługi.</span><span class="sxs-lookup"><span data-stu-id="27882-108">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="27882-109">Na przykład można zmodyfikować aplikację, która odczytuje dane XML z <xref:System.IO.FileStream> pliku, aby odczytywać dane <xref:System.Net.Sockets.NetworkStream> z zamiast tego, zmieniając tylko kilka wierszy kodu, które inicjują strumień.</span><span class="sxs-lookup"><span data-stu-id="27882-109">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="27882-110">Główne różnice między klasą **NetworkStream** i innymi strumieniami polegają na tym, że **NetworkStream** nie jest <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> możliwy do odszukania, właściwość <xref:System.Net.Sockets.NetworkStream.Seek%2A> zawsze <xref:System.Net.Sockets.NetworkStream.Position%2A> zwraca **wartość false**, a metody i generują <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="27882-110">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
- <span data-ttu-id="27882-111">Przetwarzanie danych po ich nadejściu.</span><span class="sxs-lookup"><span data-stu-id="27882-111">Processing of data as it arrives.</span></span> <span data-ttu-id="27882-112">Strumienie zapewniają dostęp do danych w miarę docierania do sieci, a nie wymuszają, aby aplikacja czekała na pobranie całego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="27882-112">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="27882-113">Przestrzeń nazw zawiera<xref:System.IO.Stream> klasę NetworkStream, która implementuje klasę specyficzną do użycia z zasobami sieciowymi. <xref:System.Net.Sockets></span><span class="sxs-lookup"><span data-stu-id="27882-113">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="27882-114">Klasy w <xref:System.Net.Sockets> przestrzeni nazw używają klasy **NetworkStream** do reprezentowania strumieni.</span><span class="sxs-lookup"><span data-stu-id="27882-114">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="27882-115">Aby wysłać dane do sieci przy użyciu zwróconego strumienia, wywołaj <xref:System.Net.WebRequest.GetRequestStream%2A> <xref:System.Net.WebRequest>polecenie.</span><span class="sxs-lookup"><span data-stu-id="27882-115">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="27882-116">**Żądanie WebRequest** wyśle nagłówki żądań do serwera; następnie można wysłać dane do zasobu sieciowego przez wywołanie <xref:System.IO.Stream.BeginWrite%2A>metody, <xref:System.IO.Stream.EndWrite%2A>, lub <xref:System.IO.Stream.Write%2A> w zwróconym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="27882-116">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="27882-117">Niektóre protokoły, takie jak HTTP, mogą wymagać ustawienia właściwości specyficznych dla protokołu przed wysłaniem danych.</span><span class="sxs-lookup"><span data-stu-id="27882-117">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="27882-118">Poniższy przykład kodu pokazuje, jak ustawić właściwości specyficzne dla protokołu HTTP na potrzeby wysyłania danych.</span><span class="sxs-lookup"><span data-stu-id="27882-118">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="27882-119">Przyjęto założenie, `sendData` że zmienna zawiera dane do wysłania, a `sendLength` zmienna to liczba bajtów danych do wysłania.</span><span class="sxs-lookup"><span data-stu-id="27882-119">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
```csharp  
HttpWebRequest request =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 <span data-ttu-id="27882-120">Aby odbierać dane z sieci, wywołaj <xref:System.Net.WebResponse.GetResponseStream%2A>. <xref:System.Net.WebResponse></span><span class="sxs-lookup"><span data-stu-id="27882-120">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="27882-121">Następnie można odczytywać dane z zasobu sieciowego przez wywołanie <xref:System.IO.Stream.BeginRead%2A>metody, <xref:System.IO.Stream.EndRead%2A>, lub <xref:System.IO.Stream.Read%2A> w zwróconym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="27882-121">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="27882-122">Korzystając ze strumieni z zasobów sieciowych, należy pamiętać o następujących kwestiach:</span><span class="sxs-lookup"><span data-stu-id="27882-122">When using streams from network resources, keep in mind the following points:</span></span>  
  
- <span data-ttu-id="27882-123">Właściwość **CanSeek** zawsze zwraca **wartość false** , ponieważ Klasa **NetworkStream** nie może zmienić pozycji w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="27882-123">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="27882-124">Metody **Seek** i **Position** zwracają **NotSupportedException**.</span><span class="sxs-lookup"><span data-stu-id="27882-124">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
- <span data-ttu-id="27882-125">W przypadku używania **WebRequest** i **WebResponse**wystąpienia strumienia utworzone przez wywołanie **metody GetResponseStream** są tylko do odczytu, a wystąpienia strumienia utworzone przez wywołanie **GetRequestStream** są tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="27882-125">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
- <span data-ttu-id="27882-126">Użyj klasy <xref:System.IO.StreamReader> , aby ułatwić kodowanie.</span><span class="sxs-lookup"><span data-stu-id="27882-126">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="27882-127">Poniższy przykład kodu używa **StreamReader** , aby odczytać strumień zakodowany w formacie ASCII z **WebResponse** (przykład nie pokazuje tworzenia żądania).</span><span class="sxs-lookup"><span data-stu-id="27882-127">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
- <span data-ttu-id="27882-128">Wywołanie metody **GetResponse** może blokować, jeśli zasoby sieciowe są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="27882-128">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="27882-129">Należy rozważyć użycie żądania asynchronicznego z <xref:System.Net.WebRequest.BeginGetResponse%2A> metodami i. <xref:System.Net.WebRequest.EndGetResponse%2A></span><span class="sxs-lookup"><span data-stu-id="27882-129">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
- <span data-ttu-id="27882-130">Wywołanie **GetRequestStream** może blokować się podczas tworzenia połączenia z serwerem.</span><span class="sxs-lookup"><span data-stu-id="27882-130">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="27882-131">Należy rozważyć użycie asynchronicznego żądania dla strumienia przy użyciu <xref:System.Net.WebRequest.BeginGetRequestStream%2A> metod i. <xref:System.Net.WebRequest.EndGetRequestStream%2A></span><span class="sxs-lookup"><span data-stu-id="27882-131">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =   
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _   
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="27882-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27882-132">See also</span></span>

- [<span data-ttu-id="27882-133">Instrukcje: Żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="27882-133">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="27882-134">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="27882-134">Requesting Data</span></span>](requesting-data.md)
