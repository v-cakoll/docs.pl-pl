---
title: 'Instrukcje: wysyłanie danych przy użyciu klasy WebRequest'
description: Dowiedz się, jak wysyłać dane do serwera przy użyciu klasy WebRequest w .NET Framework. Ta procedura jest często używana do publikowania danych na stronie sieci Web.
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 4b353250fec778ee8b352f13de6d7faaf15c13ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502447"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="cdf9f-104">Instrukcje: wysyłanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="cdf9f-104">How to: Send data by using the WebRequest class</span></span>

<span data-ttu-id="cdf9f-105">Poniższa procedura zawiera opis czynności, które należy wykonać w celu wysłania danych do serwera programu.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-105">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="cdf9f-106">Ta procedura jest często używana do publikowania danych na stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-106">This procedure is commonly used to post data to a Web page.</span></span>

## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="cdf9f-107">Aby wysłać dane do serwera hosta</span><span class="sxs-lookup"><span data-stu-id="cdf9f-107">To send data to a host server</span></span>

1. <span data-ttu-id="cdf9f-108">Utwórz <xref:System.Net.WebRequest> wystąpienie przez wywołanie <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> identyfikatora URI zasobu, takiego jak skrypt lub strona ASP.NET, która akceptuje dane.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-108">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="cdf9f-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cdf9f-109">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > <span data-ttu-id="cdf9f-110">.NET Framework zawiera klasy specyficzne dla protokołu pochodzące od <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> klas i dla identyfikatorów URI, które zaczynają się od *http:*, *https:*, *FTP:* i *File:*.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-110">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="cdf9f-111">Jeśli konieczne jest ustawienie lub odczytanie właściwości specyficznych dla protokołu, należy rzutować <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> obiekt lub na typ obiektu specyficzny dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-111">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="cdf9f-112">Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="cdf9f-112">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="cdf9f-113">Ustaw wartości właściwości, które są potrzebne w `WebRequest` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-113">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="cdf9f-114">Na przykład aby włączyć uwierzytelnianie, należy ustawić <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> Właściwość na wystąpienie <xref:System.Net.NetworkCredential> klasy:</span><span class="sxs-lookup"><span data-stu-id="cdf9f-114">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="cdf9f-115">Określ metodę protokołu, która zezwala na wysyłanie danych przy użyciu żądania, takiego jak `POST` Metoda http:</span><span class="sxs-lookup"><span data-stu-id="cdf9f-115">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <span data-ttu-id="cdf9f-116">Ustaw <xref:System.Web.HttpRequest.ContentLength> Właściwość na liczbę bajtów, które są dołączane do żądania.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-116">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="cdf9f-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cdf9f-117">For example:</span></span>

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <span data-ttu-id="cdf9f-118">Ustaw <xref:System.Web.HttpRequest.ContentType> Właściwość na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-118">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="cdf9f-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cdf9f-119">For example:</span></span>

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <span data-ttu-id="cdf9f-120">Pobierz strumień, który przechowuje dane żądania przez wywołanie <xref:System.Net.WebRequest.GetRequestStream%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-120">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="cdf9f-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cdf9f-121">For example:</span></span>

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <span data-ttu-id="cdf9f-122">Zapisz dane do <xref:System.IO.Stream> obiektu zwróconego przez `GetRequestStream` metodę.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-122">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="cdf9f-123">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cdf9f-123">For example:</span></span>

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <span data-ttu-id="cdf9f-124">Zamknij strumień żądań, wywołując <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-124">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cdf9f-125">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cdf9f-125">For example:</span></span>

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. <span data-ttu-id="cdf9f-126">Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cdf9f-126">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cdf9f-127">Ta metoda zwraca obiekt zawierający odpowiedź serwera.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-127">This method returns an object containing the server's response.</span></span> <span data-ttu-id="cdf9f-128">Typ zwracanego `WebResponse` obiektu jest określany przez schemat identyfikatora URI żądania.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-128">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="cdf9f-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cdf9f-129">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. <span data-ttu-id="cdf9f-130">Możesz uzyskać dostęp do właściwości `WebResponse` obiektu lub rzutować go do wystąpienia specyficznego dla protokołu, aby odczytywać właściwości specyficzne dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-130">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="cdf9f-131">Na przykład, aby uzyskać dostęp do właściwości specyficznych dla protokołu HTTP <xref:System.Net.HttpWebResponse> , należy rzutować `WebResponse` obiekt na <xref:System.Net.HttpWebResponse> odwołanie.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-131">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="cdf9f-132">Poniższy przykład kodu pokazuje, jak wyświetlić Właściwość specyficzną dla protokołu HTTP, która <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> jest wysyłana z odpowiedzią:</span><span class="sxs-lookup"><span data-stu-id="cdf9f-132">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. <span data-ttu-id="cdf9f-133">Aby uzyskać strumień zawierający dane odpowiedzi wysyłane przez serwer, wywołaj <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodę `WebResponse` obiektu.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-133">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="cdf9f-134">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cdf9f-134">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. <span data-ttu-id="cdf9f-135">Po odczytaniu danych z obiektu Response należy zamknąć je za pomocą <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody lub zamknąć strumień odpowiedzi przy użyciu <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-135">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cdf9f-136">Jeśli nie zamkniesz odpowiedzi lub strumienia, aplikacja może wyłączać połączenia z serwerem i nie może przetwarzać dodatkowych żądań.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-136">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="cdf9f-137">Ponieważ `WebResponse.Close` Metoda wywołuje się `Stream.Close` , gdy zamyka odpowiedź, nie jest konieczne wywoływanie `Close` zarówno obiektów odpowiedzi, jak i strumienia, chociaż nie jest to szkodliwe.</span><span class="sxs-lookup"><span data-stu-id="cdf9f-137">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="cdf9f-138">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cdf9f-138">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="cdf9f-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="cdf9f-139">Example</span></span>

<span data-ttu-id="cdf9f-140">Poniższy przykład przedstawia sposób wysyłania danych do serwera sieci Web i odczytywania danych w odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="cdf9f-140">The following example shows how to send data to a web server and read the data in its response:</span></span>

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="cdf9f-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdf9f-141">See also</span></span>

- [<span data-ttu-id="cdf9f-142">Tworzenie żądań internetowych</span><span class="sxs-lookup"><span data-stu-id="cdf9f-142">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="cdf9f-143">Używanie strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="cdf9f-143">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="cdf9f-144">Uzyskiwanie dostępu do Internetu za pomocą serwera proxy</span><span class="sxs-lookup"><span data-stu-id="cdf9f-144">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="cdf9f-145">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="cdf9f-145">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="cdf9f-146">Instrukcje: żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="cdf9f-146">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
