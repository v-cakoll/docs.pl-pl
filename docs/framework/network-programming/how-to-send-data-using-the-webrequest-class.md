---
title: 'Instrukcje: Wyślij dane przy użyciu klasy WebRequest'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 2dcc9e70f51c3c96cbc3af238fed21021ff7ae2c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347370"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="86cca-102">Instrukcje: Wyślij dane przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="86cca-102">How to: Send data by using the WebRequest class</span></span>
<span data-ttu-id="86cca-103">Poniższa procedura opisuje kroki, aby wysłać dane do serwera.</span><span class="sxs-lookup"><span data-stu-id="86cca-103">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="86cca-104">Ta procedura jest często używane dane do strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="86cca-104">This procedure is commonly used to post data to a Web page.</span></span> 
  
## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="86cca-105">Do przesyłania danych do serwera hosta</span><span class="sxs-lookup"><span data-stu-id="86cca-105">To send data to a host server</span></span>  
  
1. <span data-ttu-id="86cca-106">Tworzenie <xref:System.Net.WebRequest> wystąpienia, wywołując <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> za pomocą identyfikatora URI zasobu, takiego jak skrypt lub strony ASP.NET, który akceptuje dane.</span><span class="sxs-lookup"><span data-stu-id="86cca-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="86cca-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="86cca-107">For example:</span></span> 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="86cca-108">Program .NET Framework zawiera klasy pochodne klasy specyficzne dla protokołu <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klas pochodnych identyfikatorów URI, które zaczynają się od *http:* , *https:* , *ftp:* , a *pliku:* .</span><span class="sxs-lookup"><span data-stu-id="86cca-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>
    <span data-ttu-id="86cca-109">Jeśli musisz set lub odczytu właściwości specyficzne dla protokołu, należy rzutować swoje <xref:System.Net.WebRequest> lub <xref:System.Net.WebResponse> obiektu z typem obiektów specyficznych dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="86cca-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="86cca-110">Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="86cca-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span> 
  
2. <span data-ttu-id="86cca-111">Ustaw wszystkie wartości właściwości, które są potrzebne w Twojej `WebRequest` obiektu.</span><span class="sxs-lookup"><span data-stu-id="86cca-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="86cca-112">Na przykład, aby włączyć uwierzytelnianie, należy ustawić <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> właściwości wystąpienia <xref:System.Net.NetworkCredential> klasy:</span><span class="sxs-lookup"><span data-stu-id="86cca-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3. <span data-ttu-id="86cca-113">Określ metodę protokołu, który zezwala na dane mają być wysyłane z żądaniem, takich jak HTTP `POST` metody:</span><span class="sxs-lookup"><span data-stu-id="86cca-113">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4. <span data-ttu-id="86cca-114">Ustaw <xref:System.Web.HttpRequest.ContentLength> liczbę bajtów w przypadku dołączania do żądania.</span><span class="sxs-lookup"><span data-stu-id="86cca-114">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="86cca-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="86cca-115">For example:</span></span> 
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5. <span data-ttu-id="86cca-116">Ustaw <xref:System.Web.HttpRequest.ContentType> właściwość do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="86cca-116">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="86cca-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="86cca-117">For example:</span></span>
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6. <span data-ttu-id="86cca-118">Strumień, że przechowuje dane żądania przez wywołanie metody GET <xref:System.Net.WebRequest.GetRequestStream%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="86cca-118">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="86cca-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="86cca-119">For example:</span></span>
  
    ```csharp  
    Stream dataStream = request.GetRequestStream();  
    ```  
  
    ```vb
    Dim dataStream As Stream = request.GetRequestStream()  
    ```  
  
7. <span data-ttu-id="86cca-120">Zapisane dane <xref:System.IO.Stream> obiektu zwróconego przez `GetRequestStream` metody.</span><span class="sxs-lookup"><span data-stu-id="86cca-120">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="86cca-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="86cca-121">For example:</span></span>
  
    ```csharp  
    dataStream.Write(byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write(byteArray, 0, byteArray.Length)  
    ```  
  
8. <span data-ttu-id="86cca-122">Zamknij strumień żądań przez wywołanie metody <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="86cca-122">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="86cca-123">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="86cca-123">For example:</span></span>
  
    ```csharp  
    dataStream.Close();  
    ```  
  
    ```vb  
    dataStream.Close()  
    ```  
  
9. <span data-ttu-id="86cca-124">Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="86cca-124">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="86cca-125">Ta metoda zwraca obiekt zawierający odpowiedź serwera.</span><span class="sxs-lookup"><span data-stu-id="86cca-125">This method returns an object containing the server's response.</span></span> <span data-ttu-id="86cca-126">Zwrócony `WebResponse` typ obiektu jest określana przez schemat identyfikatora URI żądania.</span><span class="sxs-lookup"><span data-stu-id="86cca-126">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="86cca-127">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="86cca-127">For example:</span></span>
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
10. <span data-ttu-id="86cca-128">Można uzyskać dostęp do właściwości usługi `WebResponse` obiektu lub go rzutować do wystąpienia oparte na protokole można odczytać właściwości specyficzne dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="86cca-128">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span> 

    <span data-ttu-id="86cca-129">Na przykład, aby właściwości dostępu właściwe dla protokołu HTTP <xref:System.Net.HttpWebResponse>, rzutowania swoje `WebResponse` obiekt <xref:System.Net.HttpWebResponse> odwołania.</span><span class="sxs-lookup"><span data-stu-id="86cca-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="86cca-130">Poniższy przykład kodu pokazuje sposób wyświetlania specyficzne dla protokołu HTTP <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> właściwości wysyłane odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="86cca-130">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>
  
    ```csharp  
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);    
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. <span data-ttu-id="86cca-131">Aby uzyskać strumienia zawierające dane odpowiedzi wysyłane przez serwer, należy wywołać <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metody usługi `WebResponse` obiektu.</span><span class="sxs-lookup"><span data-stu-id="86cca-131">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="86cca-132">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="86cca-132">For example:</span></span>
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
12. <span data-ttu-id="86cca-133">Po zapoznaniu się dane z obiektu odpowiedzi, albo zamknij je za pomocą <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody lub zamknij odpowiedzi przesyłania strumieniowego przy użyciu <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="86cca-133">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="86cca-134">Jeśli nie zamkniesz odpowiedzi lub strumienia, aplikację można Brak połączenia z serwerem i stają się nie może przetworzyć żądań dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="86cca-134">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="86cca-135">Ponieważ `WebResponse.Close` wywołania metody `Stream.Close` jego zamknięciem odpowiedzi nie jest konieczne wywołać `Close` obiektów odpowiedzi i strumienia, mimo że takie postępowania tak nie jest szkodliwy.</span><span class="sxs-lookup"><span data-stu-id="86cca-135">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="86cca-136">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="86cca-136">For example:</span></span>
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="86cca-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="86cca-137">Example</span></span>  
  
<span data-ttu-id="86cca-138">Poniższy przykład pokazuje, jak wysyłać dane do serwera sieci web i odczytywać je w swojej odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="86cca-138">The following example shows how to send data to a web server and read the data in its response:</span></span>  

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="86cca-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86cca-139">See also</span></span>

- [<span data-ttu-id="86cca-140">Tworzenie żądań internetowych</span><span class="sxs-lookup"><span data-stu-id="86cca-140">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="86cca-141">Stosowanie strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="86cca-141">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="86cca-142">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="86cca-142">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="86cca-143">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="86cca-143">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="86cca-144">Instrukcje: Żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="86cca-144">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
