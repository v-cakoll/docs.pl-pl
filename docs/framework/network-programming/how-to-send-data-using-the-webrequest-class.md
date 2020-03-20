---
title: 'Jak: Wysyłanie danych przy użyciu WebRequest klasy'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 2467b289df7a0361b51ad91d4458d32742c42275
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70040827"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="08ce3-102">Jak: Wysyłanie danych przy użyciu WebRequest klasy</span><span class="sxs-lookup"><span data-stu-id="08ce3-102">How to: Send data by using the WebRequest class</span></span>

<span data-ttu-id="08ce3-103">W poniższej procedurze opisano kroki wysyłania danych do serwera.</span><span class="sxs-lookup"><span data-stu-id="08ce3-103">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="08ce3-104">Ta procedura jest często używana do publikowania danych na stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="08ce3-104">This procedure is commonly used to post data to a Web page.</span></span>

## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="08ce3-105">Aby wysłać dane do serwera hosta</span><span class="sxs-lookup"><span data-stu-id="08ce3-105">To send data to a host server</span></span>

1. <span data-ttu-id="08ce3-106">Utwórz <xref:System.Net.WebRequest> wystąpienie, wywołując <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> z identyfikatorem URI zasobu, takiego jak skrypt lub strona ASP.NET, która akceptuje dane.</span><span class="sxs-lookup"><span data-stu-id="08ce3-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="08ce3-107">Przykład:</span><span class="sxs-lookup"><span data-stu-id="08ce3-107">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > <span data-ttu-id="08ce3-108">.NET Framework zawiera klasy specyficzne dla <xref:System.Net.WebRequest> protokołu <xref:System.Net.WebResponse> pochodzące z i klasy dla identyfikatorów URI, które zaczynają się od *http:*, *https:*, *ftp:*, i *plik:*.</span><span class="sxs-lookup"><span data-stu-id="08ce3-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="08ce3-109">Jeśli chcesz ustawić lub odczytać właściwości specyficzne dla protokołu, <xref:System.Net.WebResponse> należy rzutować lub <xref:System.Net.WebRequest> obiekt do typu obiektu specyficznego dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="08ce3-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="08ce3-110">Aby uzyskać więcej informacji, zobacz [Programowanie protokołów podłączanych](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="08ce3-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="08ce3-111">Ustaw wszystkie wartości właściwości, `WebRequest` które są potrzebne w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="08ce3-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="08ce3-112">Na przykład, aby włączyć <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> uwierzytelnianie, ustaw <xref:System.Net.NetworkCredential> właściwość na wystąpienie klasy:</span><span class="sxs-lookup"><span data-stu-id="08ce3-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="08ce3-113">Określ metodę protokołu, która umożliwia przesyłanie danych za `POST` pomocą żądania, na przykład metodę HTTP:</span><span class="sxs-lookup"><span data-stu-id="08ce3-113">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <span data-ttu-id="08ce3-114">Ustaw <xref:System.Web.HttpRequest.ContentLength> właściwość na liczbę bajtów, które zawierasz z żądaniem.</span><span class="sxs-lookup"><span data-stu-id="08ce3-114">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="08ce3-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="08ce3-115">For example:</span></span>

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <span data-ttu-id="08ce3-116">Ustaw <xref:System.Web.HttpRequest.ContentType> właściwość na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="08ce3-116">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="08ce3-117">Przykład:</span><span class="sxs-lookup"><span data-stu-id="08ce3-117">For example:</span></span>

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <span data-ttu-id="08ce3-118">Pobierz strumień, który przechowuje <xref:System.Net.WebRequest.GetRequestStream%2A> dane żądania, wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="08ce3-118">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="08ce3-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="08ce3-119">For example:</span></span>

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <span data-ttu-id="08ce3-120">Zapisz dane do <xref:System.IO.Stream> obiektu zwróconego `GetRequestStream` przez metodę.</span><span class="sxs-lookup"><span data-stu-id="08ce3-120">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="08ce3-121">Przykład:</span><span class="sxs-lookup"><span data-stu-id="08ce3-121">For example:</span></span>

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <span data-ttu-id="08ce3-122">Zamknij strumień żądania, <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="08ce3-122">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="08ce3-123">Przykład:</span><span class="sxs-lookup"><span data-stu-id="08ce3-123">For example:</span></span>

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. <span data-ttu-id="08ce3-124">Wyślij żądanie do serwera, <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>dzwoniąc .</span><span class="sxs-lookup"><span data-stu-id="08ce3-124">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="08ce3-125">Ta metoda zwraca obiekt zawierający odpowiedź serwera.</span><span class="sxs-lookup"><span data-stu-id="08ce3-125">This method returns an object containing the server's response.</span></span> <span data-ttu-id="08ce3-126">Typ `WebResponse` zwracanego obiektu jest określany przez schemat identyfikatora URI żądania.</span><span class="sxs-lookup"><span data-stu-id="08ce3-126">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="08ce3-127">Przykład:</span><span class="sxs-lookup"><span data-stu-id="08ce3-127">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. <span data-ttu-id="08ce3-128">Można uzyskać dostęp do `WebResponse` właściwości obiektu lub przerzucić go do wystąpienia specyficznego dla protokołu, aby odczytać właściwości specyficzne dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="08ce3-128">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="08ce3-129">Na przykład, aby uzyskać dostęp do <xref:System.Net.HttpWebResponse>właściwości `WebResponse` specyficznych <xref:System.Net.HttpWebResponse> dla protokołu HTTP , rzutuj obiekt na odwołanie.</span><span class="sxs-lookup"><span data-stu-id="08ce3-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="08ce3-130">W poniższym przykładzie kodu pokazano, <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> jak wyświetlić właściwość specyficzną dla protokołu HTTP wysłaną z odpowiedzią:</span><span class="sxs-lookup"><span data-stu-id="08ce3-130">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. <span data-ttu-id="08ce3-131">Aby uzyskać strumień zawierający dane odpowiedzi wysyłane <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> przez serwer, wywołaj metodę obiektu. `WebResponse`</span><span class="sxs-lookup"><span data-stu-id="08ce3-131">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="08ce3-132">Przykład:</span><span class="sxs-lookup"><span data-stu-id="08ce3-132">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. <span data-ttu-id="08ce3-133">Po przeczytaniu danych z obiektu odpowiedzi zamknij go <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> za pomocą metody lub zamknij <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> strumień odpowiedzi za pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="08ce3-133">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="08ce3-134">Jeśli nie zamkniesz odpowiedzi lub strumienia, aplikacja może zabraknąć połączeń z serwerem i nie będzie w stanie przetworzyć dodatkowych żądań.</span><span class="sxs-lookup"><span data-stu-id="08ce3-134">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="08ce3-135">Ponieważ `WebResponse.Close` metoda `Stream.Close` wywołuje, gdy zamyka odpowiedź, nie jest `Close` konieczne wywołanie zarówno odpowiedzi i strumienia obiektów, chociaż w ten sposób nie jest szkodliwe.</span><span class="sxs-lookup"><span data-stu-id="08ce3-135">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="08ce3-136">Przykład:</span><span class="sxs-lookup"><span data-stu-id="08ce3-136">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="08ce3-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="08ce3-137">Example</span></span>

<span data-ttu-id="08ce3-138">W poniższym przykładzie pokazano, jak wysyłać dane do serwera sieci web i odczytywać dane w odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="08ce3-138">The following example shows how to send data to a web server and read the data in its response:</span></span>

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="08ce3-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08ce3-139">See also</span></span>

- [<span data-ttu-id="08ce3-140">Tworzenie żądań internetowych</span><span class="sxs-lookup"><span data-stu-id="08ce3-140">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="08ce3-141">Korzystanie ze strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="08ce3-141">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="08ce3-142">Uzyskiwanie dostępu do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="08ce3-142">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="08ce3-143">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="08ce3-143">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="08ce3-144">Jak: Żądanie danych przy użyciu WebRequest klasy</span><span class="sxs-lookup"><span data-stu-id="08ce3-144">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
