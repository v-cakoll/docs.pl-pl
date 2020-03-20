---
title: 'Jak: Żądanie danych przy użyciu WebRequest klasy'
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
ms.openlocfilehash: e670a2a503ce704eff847e9e0b3ee340ab52fe62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048166"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="a28e0-102">Jak: Żądanie danych przy użyciu WebRequest klasy</span><span class="sxs-lookup"><span data-stu-id="a28e0-102">How to: Request data by using the WebRequest class</span></span>

<span data-ttu-id="a28e0-103">W poniższej procedurze opisano kroki żądania zasobu, takiego jak strona sieci Web lub plik, z serwera.</span><span class="sxs-lookup"><span data-stu-id="a28e0-103">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="a28e0-104">Zasób musi być identyfikowany przez identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="a28e0-104">The resource must be identified by a URI.</span></span>

## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="a28e0-105">Aby zażądać danych z serwera hosta</span><span class="sxs-lookup"><span data-stu-id="a28e0-105">To request data from a host server</span></span>

1. <span data-ttu-id="a28e0-106">Utwórz <xref:System.Net.WebRequest> wystąpienie, wywołując <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> z identyfikatorem URI zasobu.</span><span class="sxs-lookup"><span data-stu-id="a28e0-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="a28e0-107">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a28e0-107">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
    ```

    > [!NOTE]
    > <span data-ttu-id="a28e0-108">.NET Framework zawiera klasy specyficzne dla <xref:System.Net.WebRequest> protokołu <xref:System.Net.WebResponse> pochodzące z i klasy dla identyfikatorów URI, które zaczynają się od *http:*, *https:*, *ftp:*, i *plik:*.</span><span class="sxs-lookup"><span data-stu-id="a28e0-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="a28e0-109">Jeśli chcesz ustawić lub odczytać właściwości specyficzne dla protokołu, <xref:System.Net.WebResponse> należy rzutować lub <xref:System.Net.WebRequest> obiekt do typu obiektu specyficznego dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="a28e0-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="a28e0-110">Aby uzyskać więcej informacji, zobacz [Programowanie protokołów podłączanych](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="a28e0-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="a28e0-111">Ustaw wszystkie wartości właściwości, `WebRequest` które są potrzebne w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="a28e0-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="a28e0-112">Na przykład, aby włączyć <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> uwierzytelnianie, ustaw <xref:System.Net.NetworkCredential> właściwość na wystąpienie klasy:</span><span class="sxs-lookup"><span data-stu-id="a28e0-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="a28e0-113">Wyślij żądanie do serwera, <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>dzwoniąc .</span><span class="sxs-lookup"><span data-stu-id="a28e0-113">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a28e0-114">Ta metoda zwraca obiekt zawierający odpowiedź serwera.</span><span class="sxs-lookup"><span data-stu-id="a28e0-114">This method returns an object containing the server's response.</span></span> <span data-ttu-id="a28e0-115">Typ <xref:System.Net.WebResponse> zwracanego obiektu jest określany przez schemat identyfikatora URI żądania.</span><span class="sxs-lookup"><span data-stu-id="a28e0-115">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="a28e0-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a28e0-116">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. <span data-ttu-id="a28e0-117">Można uzyskać dostęp do `WebResponse` właściwości obiektu lub przerzucić go do wystąpienia specyficznego dla protokołu, aby odczytać właściwości specyficzne dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="a28e0-117">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="a28e0-118">Na przykład, aby uzyskać dostęp do <xref:System.Net.HttpWebResponse>właściwości `WebResponse` specyficznych `HttpWebResponse` dla protokołu HTTP , rzutuj obiekt na odwołanie.</span><span class="sxs-lookup"><span data-stu-id="a28e0-118">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="a28e0-119">W poniższym przykładzie kodu pokazano, <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> jak wyświetlić właściwość specyficzną dla protokołu HTTP wysłaną z odpowiedzią:</span><span class="sxs-lookup"><span data-stu-id="a28e0-119">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. <span data-ttu-id="a28e0-120">Aby uzyskać strumień zawierający dane odpowiedzi wysyłane <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> przez serwer, należy wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="a28e0-120">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a28e0-121">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a28e0-121">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. <span data-ttu-id="a28e0-122">Po przeczytaniu danych z obiektu odpowiedzi zamknij go <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> za pomocą metody lub zamknij <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> strumień odpowiedzi za pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="a28e0-122">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a28e0-123">Jeśli nie zamkniesz obiektu odpowiedzi lub strumienia, aplikacja może zabraknąć połączeń z serwerem i nie będzie w stanie przetworzyć dodatkowych żądań.</span><span class="sxs-lookup"><span data-stu-id="a28e0-123">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="a28e0-124">Ponieważ `WebResponse.Close` metoda `Stream.Close` wywołuje, gdy zamyka odpowiedź, nie jest `Close` konieczne wywołanie zarówno odpowiedzi i strumienia obiektów, chociaż w ten sposób nie jest szkodliwe.</span><span class="sxs-lookup"><span data-stu-id="a28e0-124">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="a28e0-125">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a28e0-125">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="a28e0-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="a28e0-126">Example</span></span>

<span data-ttu-id="a28e0-127">Poniższy przykład kodu pokazuje, jak utworzyć żądanie do serwera sieci web i odczytać dane w odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="a28e0-127">The following code example shows how to create a request to a web server and read the data in its response:</span></span>

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a><span data-ttu-id="a28e0-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a28e0-128">See also</span></span>

- [<span data-ttu-id="a28e0-129">Tworzenie żądań internetowych</span><span class="sxs-lookup"><span data-stu-id="a28e0-129">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="a28e0-130">Korzystanie ze strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="a28e0-130">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="a28e0-131">Uzyskiwanie dostępu do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="a28e0-131">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="a28e0-132">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="a28e0-132">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="a28e0-133">Jak: Wysyłanie danych przy użyciu WebRequest klasy</span><span class="sxs-lookup"><span data-stu-id="a28e0-133">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
