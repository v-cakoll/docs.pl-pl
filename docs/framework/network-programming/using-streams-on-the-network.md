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
ms.openlocfilehash: 9849c64b30ed1021c12f34a7920104537292197a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628464"
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="fde98-102">Stosowanie strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="fde98-102">Using Streams on the Network</span></span>
<span data-ttu-id="fde98-103">Zasoby sieciowe są reprezentowane w .NET Framework jako strumieni.</span><span class="sxs-lookup"><span data-stu-id="fde98-103">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="fde98-104">Traktując strumieni ogólną, .NET Framework oferuje następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="fde98-104">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
-   <span data-ttu-id="fde98-105">Typowym sposobem wysyłania i odbierania danych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="fde98-105">A common way to send and receive Web data.</span></span> <span data-ttu-id="fde98-106">Niezależnie od rzeczywistej zawartości pliku — HTML, XML lub czymkolwiek — aplikacja będzie używać <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> i <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> do wysyłania i odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="fde98-106">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
-   <span data-ttu-id="fde98-107">Zgodność ze strumieniami w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fde98-107">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="fde98-108">Strumienie są używane w .NET Framework, który ma rozbudowane infrastruktury do ich obsługi.</span><span class="sxs-lookup"><span data-stu-id="fde98-108">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="fde98-109">Na przykład, można zmodyfikować aplikację, która odczytuje dane XML z <xref:System.IO.FileStream> można odczytać danych z <xref:System.Net.Sockets.NetworkStream> zamiast zmieniając tylko kilka wierszy kodu, które zainicjować strumienia.</span><span class="sxs-lookup"><span data-stu-id="fde98-109">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="fde98-110">Główne różnice między **Strumień NetworkStream** klasy i inne strumienie są, **Strumień NetworkStream** nie można wyszukać, <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> właściwość zawsze zwraca **false**i <xref:System.Net.Sockets.NetworkStream.Seek%2A> i <xref:System.Net.Sockets.NetworkStream.Position%2A> metod generują <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="fde98-110">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
-   <span data-ttu-id="fde98-111">Przetwarzanie danych podczas ich nadejściu.</span><span class="sxs-lookup"><span data-stu-id="fde98-111">Processing of data as it arrives.</span></span> <span data-ttu-id="fde98-112">Strumienie zapewniają dostęp do danych niezapisywanie ich w sieci, zamiast wymuszania aplikacji oczekiwania dla całego zestawu danych do pobrania.</span><span class="sxs-lookup"><span data-stu-id="fde98-112">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="fde98-113"><xref:System.Net.Sockets> Przestrzeń nazw zawiera **Strumień NetworkStream** klasę, która implementuje <xref:System.IO.Stream> klasy specjalnie do użytku z zasobów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="fde98-113">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="fde98-114">Klasy w <xref:System.Net.Sockets> przestrzeni nazw korzystają z **Strumień NetworkStream** klasy do reprezentowania strumieni.</span><span class="sxs-lookup"><span data-stu-id="fde98-114">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="fde98-115">Aby wysyłać dane do sieci przy użyciu zwróconym strumieniu, należy wywołać <xref:System.Net.WebRequest.GetRequestStream%2A> na Twoje <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="fde98-115">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="fde98-116">**WebRequest** wyśle nagłówki żądania do serwera; a następnie mogą wysyłać dane do zasobu sieciowego, wywołując <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, lub <xref:System.IO.Stream.Write%2A> metody w zwróconym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="fde98-116">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="fde98-117">Niektóre protokoły, takie jak HTTP, może wymagać ustawienia właściwości specyficzne dla protokołu przed wysłaniem danych.</span><span class="sxs-lookup"><span data-stu-id="fde98-117">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="fde98-118">Poniższy przykład kodu pokazuje sposób ustawiania właściwości specyficzne dla protokołu HTTP do wysyłania danych.</span><span class="sxs-lookup"><span data-stu-id="fde98-118">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="fde98-119">Założono, że zmienna `sendData` zawiera dane do wysłania oraz że zmiennej `sendLength` jest to liczba bajtów danych do wysłania.</span><span class="sxs-lookup"><span data-stu-id="fde98-119">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
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
  
 <span data-ttu-id="fde98-120">Aby odbierać dane z sieci, należy wywołać <xref:System.Net.WebResponse.GetResponseStream%2A> na Twoje <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="fde98-120">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="fde98-121">Można następnie odczytywać dane z zasobów sieciowych, wywołując <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, lub <xref:System.IO.Stream.Read%2A> metody w zwróconym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="fde98-121">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="fde98-122">Podczas za pomocą strumieni z zasobów sieciowych, należy uwzględnić następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="fde98-122">When using streams from network resources, keep in mind the following points:</span></span>  
  
-   <span data-ttu-id="fde98-123">**CanSeek** właściwość zawsze zwraca **false** ponieważ **Strumień NetworkStream** klasy nie można zmienić pozycji w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="fde98-123">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="fde98-124">**Seek** i **pozycji** metod generują **wyjątek NotSupportedException**.</span><span class="sxs-lookup"><span data-stu-id="fde98-124">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
-   <span data-ttu-id="fde98-125">Kiedy używasz **WebRequest** i **elementu WebResponse**, strumienia wystąpienia utworzone przez wywołanie metody **GetResponseStream dla** są przeznaczone tylko do odczytu i przesyłania strumieniowego utworzonych przez wywoływanie wystąpień **GetRequestStream** są przeznaczone tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="fde98-125">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
-   <span data-ttu-id="fde98-126">Użyj <xref:System.IO.StreamReader> klasie, aby łatwiej kodowania.</span><span class="sxs-lookup"><span data-stu-id="fde98-126">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="fde98-127">Poniższy przykład kodu wykorzystuje **StreamReader** do odczytu strumień zakodowany w formacie ASCII od **elementu WebResponse** (przykład wyświetla tworzenia żądania).</span><span class="sxs-lookup"><span data-stu-id="fde98-127">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
-   <span data-ttu-id="fde98-128">Wywołanie **metody GetResponse** można zablokować, jeśli zasoby sieciowe nie są dostępne.</span><span class="sxs-lookup"><span data-stu-id="fde98-128">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="fde98-129">Należy rozważyć użycie żądania asynchronicznego przy użyciu <xref:System.Net.WebRequest.BeginGetResponse%2A> i <xref:System.Net.WebRequest.EndGetResponse%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fde98-129">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
-   <span data-ttu-id="fde98-130">Wywołanie **GetRequestStream** można zablokować, gdy zostanie utworzone połączenie z serwerem.</span><span class="sxs-lookup"><span data-stu-id="fde98-130">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="fde98-131">Należy rozważyć użycie żądania asynchronicznego strumienia z <xref:System.Net.WebRequest.BeginGetRequestStream%2A> i <xref:System.Net.WebRequest.EndGetRequestStream%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fde98-131">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fde98-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fde98-132">See also</span></span>
- [<span data-ttu-id="fde98-133">Instrukcje: Żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="fde98-133">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="fde98-134">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="fde98-134">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
