---
title: 'Instrukcje: Żądanie danych przy użyciu klasy WebRequest'
ms.date: 03/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
ms.openlocfilehash: eb38a95891afaf4cab98e43a250b67823fa5eb24
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040878"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="76a52-102">Instrukcje: Żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="76a52-102">How to: Request data by using the WebRequest class</span></span>

<span data-ttu-id="76a52-103">Poniższa procedura zawiera opis czynności, które należy wykonać w celu zażądania zasobu, takiego jak strona sieci Web lub plik, z serwera programu.</span><span class="sxs-lookup"><span data-stu-id="76a52-103">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="76a52-104">Zasób musi być identyfikowany za pomocą identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="76a52-104">The resource must be identified by a URI.</span></span>

## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="76a52-105">Aby zażądać danych z serwera hosta</span><span class="sxs-lookup"><span data-stu-id="76a52-105">To request data from a host server</span></span>

1. <span data-ttu-id="76a52-106">Utwórz wystąpienie, wywołując <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> identyfikator URI zasobu. <xref:System.Net.WebRequest></span><span class="sxs-lookup"><span data-stu-id="76a52-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="76a52-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="76a52-107">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/default.html");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/default.html")
    ```

    > [!NOTE]
    > <span data-ttu-id="76a52-108">.NET Framework zawiera klasy specyficzne <xref:System.Net.WebRequest> dla protokołu pochodzące od klas i <xref:System.Net.WebResponse> dla identyfikatorów URI, które zaczynają się od *http:* , *https:* , *FTP:* i *File:* .</span><span class="sxs-lookup"><span data-stu-id="76a52-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="76a52-109">Jeśli konieczne jest ustawienie lub odczytanie właściwości specyficznych dla protokołu, należy rzutować <xref:System.Net.WebRequest> obiekt <xref:System.Net.WebResponse> lub na typ obiektu specyficzny dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="76a52-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="76a52-110">Aby uzyskać więcej informacji, zobacz [programowanie protokołów](programming-pluggable-protocols.md)podłączanych.</span><span class="sxs-lookup"><span data-stu-id="76a52-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="76a52-111">Ustaw wartości właściwości, które są potrzebne w `WebRequest` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="76a52-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="76a52-112">Na przykład aby włączyć uwierzytelnianie, należy ustawić <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> właściwość na wystąpienie <xref:System.Net.NetworkCredential> klasy:</span><span class="sxs-lookup"><span data-stu-id="76a52-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="76a52-113">Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="76a52-113">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="76a52-114">Ta metoda zwraca obiekt zawierający odpowiedź serwera.</span><span class="sxs-lookup"><span data-stu-id="76a52-114">This method returns an object containing the server's response.</span></span> <span data-ttu-id="76a52-115">Typ zwracanego <xref:System.Net.WebResponse> obiektu jest określany przez schemat identyfikatora URI żądania.</span><span class="sxs-lookup"><span data-stu-id="76a52-115">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="76a52-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="76a52-116">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. <span data-ttu-id="76a52-117">Możesz uzyskać dostęp do właściwości `WebResponse` obiektu lub rzutować go do wystąpienia specyficznego dla protokołu, aby odczytywać właściwości specyficzne dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="76a52-117">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="76a52-118">Na przykład, aby uzyskać dostęp do właściwości <xref:System.Net.HttpWebResponse>specyficznych dla protokołu HTTP, należy `WebResponse` rzutować `HttpWebResponse` obiekt na odwołanie.</span><span class="sxs-lookup"><span data-stu-id="76a52-118">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="76a52-119">Poniższy przykład kodu pokazuje, jak wyświetlić Właściwość specyficzną <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> dla protokołu HTTP, która jest wysyłana z odpowiedzią:</span><span class="sxs-lookup"><span data-stu-id="76a52-119">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. <span data-ttu-id="76a52-120">Aby uzyskać strumień zawierający dane odpowiedzi wysyłane przez serwer, wywołaj <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="76a52-120">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="76a52-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="76a52-121">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. <span data-ttu-id="76a52-122">Po odczytaniu danych z obiektu Response należy zamknąć je za pomocą <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody lub zamknąć strumień odpowiedzi <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="76a52-122">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="76a52-123">Jeśli nie zamkniesz obiektu Response lub strumienia, aplikacja może wyłączać połączenia z serwerem i nie może przetwarzać dodatkowych żądań.</span><span class="sxs-lookup"><span data-stu-id="76a52-123">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="76a52-124">Ponieważ metoda wywołuje `Stream.Close` się, gdy zamyka odpowiedź, nie jest konieczne wywoływanie `Close` zarówno obiektów odpowiedzi, jak i strumienia, chociaż nie jest to szkodliwe. `WebResponse.Close`</span><span class="sxs-lookup"><span data-stu-id="76a52-124">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="76a52-125">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="76a52-125">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="76a52-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="76a52-126">Example</span></span>

<span data-ttu-id="76a52-127">Poniższy przykład kodu przedstawia sposób tworzenia żądania na serwerze sieci Web i odczytywania danych w odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="76a52-127">The following code example shows how to create a request to a web server and read the data in its response:</span></span>

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a><span data-ttu-id="76a52-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76a52-128">See also</span></span>

- [<span data-ttu-id="76a52-129">Tworzenie żądań internetowych</span><span class="sxs-lookup"><span data-stu-id="76a52-129">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="76a52-130">Używanie strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="76a52-130">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="76a52-131">Uzyskiwanie dostępu do Internetu za pomocą serwera proxy</span><span class="sxs-lookup"><span data-stu-id="76a52-131">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="76a52-132">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="76a52-132">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="76a52-133">Instrukcje: Wyślij dane przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="76a52-133">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
