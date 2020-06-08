---
title: Stosowanie strumieni w sieci
description: .NET Framework reprezentuje zasoby sieciowe jako strumienie. Klasa NetworkStream implementuje klasę strumienia do użycia z zasobami sieciowymi.
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
ms.openlocfilehash: f8d35b43c9b46a77bfd0c78f7d0118093b6fe824
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501979"
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="c215c-104">Stosowanie strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="c215c-104">Using Streams on the Network</span></span>
<span data-ttu-id="c215c-105">Zasoby sieciowe są reprezentowane w .NET Framework jako strumienie.</span><span class="sxs-lookup"><span data-stu-id="c215c-105">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="c215c-106">Traktując strumienie ogólnie, .NET Framework oferuje następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="c215c-106">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
- <span data-ttu-id="c215c-107">Typowy sposób wysyłania i odbierania danych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c215c-107">A common way to send and receive Web data.</span></span> <span data-ttu-id="c215c-108">Bez względu na rzeczywistą zawartość pliku — HTML, XML lub coś innego — aplikacja będzie używać programu <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> oraz <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> do wysyłania i odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="c215c-108">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
- <span data-ttu-id="c215c-109">Zgodność ze strumieniami w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c215c-109">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="c215c-110">Strumienie są używane w całym .NET Framework, który ma rozbudowaną infrastrukturę do ich obsługi.</span><span class="sxs-lookup"><span data-stu-id="c215c-110">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="c215c-111">Na przykład można zmodyfikować aplikację, która odczytuje dane XML z pliku, <xref:System.IO.FileStream> aby odczytywać dane z <xref:System.Net.Sockets.NetworkStream> zamiast tego, zmieniając tylko kilka wierszy kodu, które inicjują strumień.</span><span class="sxs-lookup"><span data-stu-id="c215c-111">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="c215c-112">Główne różnice między klasą **NetworkStream** i innymi strumieniami polegają na tym, że **NetworkStream** nie można przeszukiwać, <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> Właściwość zawsze zwraca **wartość false**, a <xref:System.Net.Sockets.NetworkStream.Seek%2A> <xref:System.Net.Sockets.NetworkStream.Position%2A> metody i generują <xref:System.NotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="c215c-112">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
- <span data-ttu-id="c215c-113">Przetwarzanie danych po ich nadejściu.</span><span class="sxs-lookup"><span data-stu-id="c215c-113">Processing of data as it arrives.</span></span> <span data-ttu-id="c215c-114">Strumienie zapewniają dostęp do danych w miarę docierania do sieci, a nie wymuszają, aby aplikacja czekała na pobranie całego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="c215c-114">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="c215c-115"><xref:System.Net.Sockets>Przestrzeń nazw zawiera klasę **NetworkStream** , która implementuje <xref:System.IO.Stream> klasę specyficzną do użycia z zasobami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="c215c-115">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="c215c-116">Klasy w <xref:System.Net.Sockets> przestrzeni nazw używają klasy **NetworkStream** do reprezentowania strumieni.</span><span class="sxs-lookup"><span data-stu-id="c215c-116">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="c215c-117">Aby wysłać dane do sieci przy użyciu zwróconego strumienia, wywołaj polecenie <xref:System.Net.WebRequest.GetRequestStream%2A> <xref:System.Net.WebRequest> .</span><span class="sxs-lookup"><span data-stu-id="c215c-117">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="c215c-118">**Żądanie WebRequest** wyśle nagłówki żądań do serwera; następnie można wysłać dane do zasobu sieciowego przez wywołanie <xref:System.IO.Stream.BeginWrite%2A> <xref:System.IO.Stream.EndWrite%2A> metody,, lub <xref:System.IO.Stream.Write%2A> w zwróconym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="c215c-118">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="c215c-119">Niektóre protokoły, takie jak HTTP, mogą wymagać ustawienia właściwości specyficznych dla protokołu przed wysłaniem danych.</span><span class="sxs-lookup"><span data-stu-id="c215c-119">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="c215c-120">Poniższy przykład kodu pokazuje, jak ustawić właściwości specyficzne dla protokołu HTTP na potrzeby wysyłania danych.</span><span class="sxs-lookup"><span data-stu-id="c215c-120">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="c215c-121">Przyjęto założenie, że zmienna `sendData` zawiera dane do wysłania, a zmienna `sendLength` to liczba bajtów danych do wysłania.</span><span class="sxs-lookup"><span data-stu-id="c215c-121">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
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
  
 <span data-ttu-id="c215c-122">Aby odbierać dane z sieci, wywołaj <xref:System.Net.WebResponse.GetResponseStream%2A> <xref:System.Net.WebResponse> .</span><span class="sxs-lookup"><span data-stu-id="c215c-122">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="c215c-123">Następnie można odczytywać dane z zasobu sieciowego przez wywołanie <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A> metody,, lub <xref:System.IO.Stream.Read%2A> w zwróconym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="c215c-123">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="c215c-124">Korzystając ze strumieni z zasobów sieciowych, należy pamiętać o następujących kwestiach:</span><span class="sxs-lookup"><span data-stu-id="c215c-124">When using streams from network resources, keep in mind the following points:</span></span>  
  
- <span data-ttu-id="c215c-125">Właściwość **CanSeek** zawsze zwraca **wartość false** , ponieważ Klasa **NetworkStream** nie może zmienić pozycji w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="c215c-125">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="c215c-126">Metody **Seek** i **Position** zwracają **NotSupportedException**.</span><span class="sxs-lookup"><span data-stu-id="c215c-126">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
- <span data-ttu-id="c215c-127">W przypadku używania **WebRequest** i **WebResponse**wystąpienia strumienia utworzone przez wywołanie **metody GetResponseStream** są tylko do odczytu, a wystąpienia strumienia utworzone przez wywołanie **GetRequestStream** są tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="c215c-127">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
- <span data-ttu-id="c215c-128">Użyj <xref:System.IO.StreamReader> klasy, aby ułatwić kodowanie.</span><span class="sxs-lookup"><span data-stu-id="c215c-128">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="c215c-129">Poniższy przykład kodu używa **StreamReader** , aby odczytać strumień zakodowany w formacie ASCII z **WebResponse** (przykład nie pokazuje tworzenia żądania).</span><span class="sxs-lookup"><span data-stu-id="c215c-129">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
- <span data-ttu-id="c215c-130">Wywołanie metody **GetResponse** może blokować, jeśli zasoby sieciowe są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="c215c-130">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="c215c-131">Należy rozważyć użycie żądania asynchronicznego z <xref:System.Net.WebRequest.BeginGetResponse%2A> <xref:System.Net.WebRequest.EndGetResponse%2A> metodami i.</span><span class="sxs-lookup"><span data-stu-id="c215c-131">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
- <span data-ttu-id="c215c-132">Wywołanie **GetRequestStream** może blokować się podczas tworzenia połączenia z serwerem.</span><span class="sxs-lookup"><span data-stu-id="c215c-132">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="c215c-133">Należy rozważyć użycie asynchronicznego żądania dla strumienia przy użyciu <xref:System.Net.WebRequest.BeginGetRequestStream%2A> <xref:System.Net.WebRequest.EndGetRequestStream%2A> metod i.</span><span class="sxs-lookup"><span data-stu-id="c215c-133">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c215c-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c215c-134">See also</span></span>

- [<span data-ttu-id="c215c-135">Instrukcje: żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="c215c-135">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="c215c-136">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="c215c-136">Requesting Data</span></span>](requesting-data.md)
