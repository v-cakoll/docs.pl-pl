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
ms.openlocfilehash: 2467b289df7a0361b51ad91d4458d32742c42275
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040827"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="f2e39-102">Instrukcje: Wyślij dane przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="f2e39-102">How to: Send data by using the WebRequest class</span></span>

<span data-ttu-id="f2e39-103">Poniższa procedura zawiera opis czynności, które należy wykonać w celu wysłania danych do serwera programu.</span><span class="sxs-lookup"><span data-stu-id="f2e39-103">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="f2e39-104">Ta procedura jest często używana do publikowania danych na stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f2e39-104">This procedure is commonly used to post data to a Web page.</span></span>

## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="f2e39-105">Aby wysłać dane do serwera hosta</span><span class="sxs-lookup"><span data-stu-id="f2e39-105">To send data to a host server</span></span>

1. <span data-ttu-id="f2e39-106">Utwórz wystąpienie przez wywołanie <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> identyfikatora URI zasobu, takiego jak skrypt lub strona ASP.NET, która akceptuje dane. <xref:System.Net.WebRequest></span><span class="sxs-lookup"><span data-stu-id="f2e39-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="f2e39-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f2e39-107">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > <span data-ttu-id="f2e39-108">.NET Framework zawiera klasy specyficzne <xref:System.Net.WebRequest> dla protokołu pochodzące od klas i <xref:System.Net.WebResponse> dla identyfikatorów URI, które zaczynają się od *http:* , *https:* , *FTP:* i *File:* .</span><span class="sxs-lookup"><span data-stu-id="f2e39-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="f2e39-109">Jeśli konieczne jest ustawienie lub odczytanie właściwości specyficznych dla protokołu, należy rzutować <xref:System.Net.WebRequest> obiekt <xref:System.Net.WebResponse> lub na typ obiektu specyficzny dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="f2e39-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="f2e39-110">Aby uzyskać więcej informacji, zobacz [programowanie protokołów](programming-pluggable-protocols.md)podłączanych.</span><span class="sxs-lookup"><span data-stu-id="f2e39-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="f2e39-111">Ustaw wartości właściwości, które są potrzebne w `WebRequest` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="f2e39-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="f2e39-112">Na przykład aby włączyć uwierzytelnianie, należy ustawić <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> właściwość na wystąpienie <xref:System.Net.NetworkCredential> klasy:</span><span class="sxs-lookup"><span data-stu-id="f2e39-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="f2e39-113">Określ metodę protokołu, która zezwala na wysyłanie danych przy użyciu żądania, takiego jak Metoda http `POST` :</span><span class="sxs-lookup"><span data-stu-id="f2e39-113">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <span data-ttu-id="f2e39-114"><xref:System.Web.HttpRequest.ContentLength> Ustaw właściwość na liczbę bajtów, które są dołączane do żądania.</span><span class="sxs-lookup"><span data-stu-id="f2e39-114">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="f2e39-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f2e39-115">For example:</span></span>

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <span data-ttu-id="f2e39-116"><xref:System.Web.HttpRequest.ContentType> Ustaw właściwość na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="f2e39-116">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="f2e39-117">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f2e39-117">For example:</span></span>

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <span data-ttu-id="f2e39-118">Pobierz strumień, który przechowuje dane żądania przez wywołanie <xref:System.Net.WebRequest.GetRequestStream%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f2e39-118">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="f2e39-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f2e39-119">For example:</span></span>

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <span data-ttu-id="f2e39-120">Zapisz dane do <xref:System.IO.Stream> obiektu zwróconego `GetRequestStream` przez metodę.</span><span class="sxs-lookup"><span data-stu-id="f2e39-120">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="f2e39-121">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f2e39-121">For example:</span></span>

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <span data-ttu-id="f2e39-122">Zamknij strumień żądań, wywołując <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="f2e39-122">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f2e39-123">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f2e39-123">For example:</span></span>

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. <span data-ttu-id="f2e39-124">Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f2e39-124">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f2e39-125">Ta metoda zwraca obiekt zawierający odpowiedź serwera.</span><span class="sxs-lookup"><span data-stu-id="f2e39-125">This method returns an object containing the server's response.</span></span> <span data-ttu-id="f2e39-126">Typ zwracanego `WebResponse` obiektu jest określany przez schemat identyfikatora URI żądania.</span><span class="sxs-lookup"><span data-stu-id="f2e39-126">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="f2e39-127">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f2e39-127">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. <span data-ttu-id="f2e39-128">Możesz uzyskać dostęp do właściwości `WebResponse` obiektu lub rzutować go do wystąpienia specyficznego dla protokołu, aby odczytywać właściwości specyficzne dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="f2e39-128">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="f2e39-129">Na przykład, aby uzyskać dostęp do właściwości <xref:System.Net.HttpWebResponse>specyficznych dla protokołu HTTP, należy `WebResponse` rzutować <xref:System.Net.HttpWebResponse> obiekt na odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f2e39-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="f2e39-130">Poniższy przykład kodu pokazuje, jak wyświetlić Właściwość specyficzną <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> dla protokołu HTTP, która jest wysyłana z odpowiedzią:</span><span class="sxs-lookup"><span data-stu-id="f2e39-130">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. <span data-ttu-id="f2e39-131">Aby uzyskać strumień zawierający dane odpowiedzi wysyłane przez serwer, wywołaj <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodę `WebResponse` obiektu.</span><span class="sxs-lookup"><span data-stu-id="f2e39-131">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="f2e39-132">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f2e39-132">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. <span data-ttu-id="f2e39-133">Po odczytaniu danych z obiektu Response należy zamknąć je za pomocą <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody lub zamknąć strumień odpowiedzi <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="f2e39-133">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f2e39-134">Jeśli nie zamkniesz odpowiedzi lub strumienia, aplikacja może wyłączać połączenia z serwerem i nie może przetwarzać dodatkowych żądań.</span><span class="sxs-lookup"><span data-stu-id="f2e39-134">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="f2e39-135">Ponieważ metoda wywołuje `Stream.Close` się, gdy zamyka odpowiedź, nie jest konieczne wywoływanie `Close` zarówno obiektów odpowiedzi, jak i strumienia, chociaż nie jest to szkodliwe. `WebResponse.Close`</span><span class="sxs-lookup"><span data-stu-id="f2e39-135">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="f2e39-136">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f2e39-136">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="f2e39-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2e39-137">Example</span></span>

<span data-ttu-id="f2e39-138">Poniższy przykład przedstawia sposób wysyłania danych do serwera sieci Web i odczytywania danych w odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="f2e39-138">The following example shows how to send data to a web server and read the data in its response:</span></span>

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="f2e39-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2e39-139">See also</span></span>

- [<span data-ttu-id="f2e39-140">Tworzenie żądań internetowych</span><span class="sxs-lookup"><span data-stu-id="f2e39-140">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="f2e39-141">Używanie strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="f2e39-141">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="f2e39-142">Uzyskiwanie dostępu do Internetu za pomocą serwera proxy</span><span class="sxs-lookup"><span data-stu-id="f2e39-142">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="f2e39-143">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="f2e39-143">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="f2e39-144">Instrukcje: Żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="f2e39-144">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
