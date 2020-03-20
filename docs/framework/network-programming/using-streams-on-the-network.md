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
ms.openlocfilehash: 7d5a2e3eec9b49731a09f6eb41a8d8500a59b45c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180624"
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="4465e-102">Stosowanie strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="4465e-102">Using Streams on the Network</span></span>
<span data-ttu-id="4465e-103">Zasoby sieciowe są reprezentowane w ramach .NET Framework jako strumienie.</span><span class="sxs-lookup"><span data-stu-id="4465e-103">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="4465e-104">Traktując strumienie ogólnie, .NET Framework oferuje następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="4465e-104">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
- <span data-ttu-id="4465e-105">Typowy sposób wysyłania i odbierania danych sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4465e-105">A common way to send and receive Web data.</span></span> <span data-ttu-id="4465e-106">Niezależnie od rzeczywistej zawartości pliku — HTML, XML lub <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> cokolwiek innego — aplikacja będzie używać i <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> wysyłać i odbierać dane.</span><span class="sxs-lookup"><span data-stu-id="4465e-106">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
- <span data-ttu-id="4465e-107">Zgodność ze strumieniami w ramach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4465e-107">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="4465e-108">Strumienie są używane w całej .NET Framework, który ma bogatą infrastrukturę do ich obsługi.</span><span class="sxs-lookup"><span data-stu-id="4465e-108">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="4465e-109">Na przykład można zmodyfikować aplikację, która odczytuje dane XML z danych <xref:System.IO.FileStream> do odczytu <xref:System.Net.Sockets.NetworkStream> z zamiast tego, zmieniając tylko kilka wierszy kodu, które inicjują strumień.</span><span class="sxs-lookup"><span data-stu-id="4465e-109">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="4465e-110">Główne różnice między **NetworkStream** klasy i innych strumieni są, że <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> **NetworkStream** nie jest dostępny, właściwość zawsze zwraca **false**, i <xref:System.Net.Sockets.NetworkStream.Seek%2A> <xref:System.Net.Sockets.NetworkStream.Position%2A> metody throw a <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="4465e-110">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
- <span data-ttu-id="4465e-111">Przetwarzanie danych w miarę ich pojawiania się.</span><span class="sxs-lookup"><span data-stu-id="4465e-111">Processing of data as it arrives.</span></span> <span data-ttu-id="4465e-112">Strumienie zapewniają dostęp do danych w miarę ich docierania z sieci, zamiast wymuszać, aby aplikacja czekała na pobranie całego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="4465e-112">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="4465e-113">Obszar <xref:System.Net.Sockets> nazw zawiera **networkstream** klasy, <xref:System.IO.Stream> która implementuje klasy specjalnie do użytku z zasobami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="4465e-113">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="4465e-114">Klasy w <xref:System.Net.Sockets> obszarze nazw używają **NetworkStream** klasy do reprezentowania strumieni.</span><span class="sxs-lookup"><span data-stu-id="4465e-114">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="4465e-115">Aby wysłać dane do sieci przy <xref:System.Net.WebRequest.GetRequestStream%2A> użyciu <xref:System.Net.WebRequest>zwróconego strumienia, zadzwoń do swojego pliku .</span><span class="sxs-lookup"><span data-stu-id="4465e-115">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="4465e-116">**WebRequest** wyśle nagłówki żądań do serwera; następnie można wysłać dane do zasobu sieciowego, wywołując <xref:System.IO.Stream.BeginWrite%2A>metodę , <xref:System.IO.Stream.EndWrite%2A>lub <xref:System.IO.Stream.Write%2A> metodę zwracany strumień.</span><span class="sxs-lookup"><span data-stu-id="4465e-116">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="4465e-117">Niektóre protokoły, takie jak HTTP, mogą wymagać skonfigurowania właściwości specyficznych dla protokołu przed wysłaniem danych.</span><span class="sxs-lookup"><span data-stu-id="4465e-117">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="4465e-118">W poniższym przykładzie kodu pokazano, jak ustawić właściwości specyficzne dla protokołu HTTP do wysyłania danych.</span><span class="sxs-lookup"><span data-stu-id="4465e-118">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="4465e-119">Przyjęto założenie, `sendData` że zmienna zawiera dane `sendLength` do wysłania i że zmienna jest liczbą bajtów danych do wysłania.</span><span class="sxs-lookup"><span data-stu-id="4465e-119">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
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
  
 <span data-ttu-id="4465e-120">Aby odbierać dane z <xref:System.Net.WebResponse.GetResponseStream%2A> sieci, zadzwoń do swojego <xref:System.Net.WebResponse>pliku .</span><span class="sxs-lookup"><span data-stu-id="4465e-120">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="4465e-121">Następnie można odczytać dane z zasobu <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A>sieciowego, wywołując metodę , lub <xref:System.IO.Stream.Read%2A> metodę zwracany strumień.</span><span class="sxs-lookup"><span data-stu-id="4465e-121">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="4465e-122">Korzystając ze strumieni z zasobów sieciowych, należy pamiętać o następujących kwestiach:</span><span class="sxs-lookup"><span data-stu-id="4465e-122">When using streams from network resources, keep in mind the following points:</span></span>  
  
- <span data-ttu-id="4465e-123">Właściwość **CanSeek** zawsze zwraca **false,** ponieważ **Klasa NetworkStream** nie może zmienić pozycji w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="4465e-123">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="4465e-124">**Metody Szukaj** i **Pozycjonurz** **NotSupportedException**.</span><span class="sxs-lookup"><span data-stu-id="4465e-124">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
- <span data-ttu-id="4465e-125">Podczas korzystania **z WebRequest** i **WebResponse**, wystąpienia strumienia utworzone przez wywołanie **GetResponseStream** są tylko do odczytu i wystąpienia strumienia utworzone przez wywołanie **GetRequestStream** są tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="4465e-125">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
- <span data-ttu-id="4465e-126">Użyj <xref:System.IO.StreamReader> klasy, aby ułatwić kodowanie.</span><span class="sxs-lookup"><span data-stu-id="4465e-126">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="4465e-127">Poniższy przykład kodu używa **StreamReader** do odczytu strumienia zakodowanego ascii z **WebResponse** (w przykładzie nie pokazuje tworzenia żądania).</span><span class="sxs-lookup"><span data-stu-id="4465e-127">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
- <span data-ttu-id="4465e-128">Wywołanie **GetResponse** można zablokować, jeśli zasoby sieciowe nie są dostępne.</span><span class="sxs-lookup"><span data-stu-id="4465e-128">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="4465e-129">Należy rozważyć użycie żądania asynchronii <xref:System.Net.WebRequest.BeginGetResponse%2A> <xref:System.Net.WebRequest.EndGetResponse%2A> z i metod.</span><span class="sxs-lookup"><span data-stu-id="4465e-129">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
- <span data-ttu-id="4465e-130">Wywołanie **GetRequestStream** można zablokować podczas tworzenia połączenia z serwerem.</span><span class="sxs-lookup"><span data-stu-id="4465e-130">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="4465e-131">Należy rozważyć użycie asynchronii żądania dla <xref:System.Net.WebRequest.BeginGetRequestStream%2A> strumienia z i <xref:System.Net.WebRequest.EndGetRequestStream%2A> metod.</span><span class="sxs-lookup"><span data-stu-id="4465e-131">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4465e-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4465e-132">See also</span></span>

- [<span data-ttu-id="4465e-133">Instrukcje: żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="4465e-133">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="4465e-134">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="4465e-134">Requesting Data</span></span>](requesting-data.md)
