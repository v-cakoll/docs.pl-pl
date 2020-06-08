---
title: 'Instrukcje: żądanie danych przy użyciu klasy WebRequest'
description: Dowiedz się, jak zażądać zasobu, takiego jak strona sieci Web lub plik, z serwera przy użyciu klasy WebRequest w .NET Framework.
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
ms.openlocfilehash: 5dcc1a7dad226288e3f74969b86e2dd457c0eed0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502473"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="f2612-103">Instrukcje: żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="f2612-103">How to: Request data by using the WebRequest class</span></span>

<span data-ttu-id="f2612-104">Poniższa procedura zawiera opis czynności, które należy wykonać w celu zażądania zasobu, takiego jak strona sieci Web lub plik, z serwera programu.</span><span class="sxs-lookup"><span data-stu-id="f2612-104">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="f2612-105">Zasób musi być identyfikowany za pomocą identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="f2612-105">The resource must be identified by a URI.</span></span>

## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="f2612-106">Aby zażądać danych z serwera hosta</span><span class="sxs-lookup"><span data-stu-id="f2612-106">To request data from a host server</span></span>

1. <span data-ttu-id="f2612-107">Utwórz <xref:System.Net.WebRequest> wystąpienie, wywołując <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> Identyfikator URI zasobu.</span><span class="sxs-lookup"><span data-stu-id="f2612-107">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="f2612-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f2612-108">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
    ```

    > [!NOTE]
    > <span data-ttu-id="f2612-109">.NET Framework zawiera klasy specyficzne dla protokołu pochodzące od <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> klas i dla identyfikatorów URI, które zaczynają się od *http:*, *https:*, *FTP:* i *File:*.</span><span class="sxs-lookup"><span data-stu-id="f2612-109">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="f2612-110">Jeśli konieczne jest ustawienie lub odczytanie właściwości specyficznych dla protokołu, należy rzutować <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> obiekt lub na typ obiektu specyficzny dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="f2612-110">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="f2612-111">Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="f2612-111">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="f2612-112">Ustaw wartości właściwości, które są potrzebne w `WebRequest` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="f2612-112">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="f2612-113">Na przykład aby włączyć uwierzytelnianie, należy ustawić <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> Właściwość na wystąpienie <xref:System.Net.NetworkCredential> klasy:</span><span class="sxs-lookup"><span data-stu-id="f2612-113">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="f2612-114">Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f2612-114">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f2612-115">Ta metoda zwraca obiekt zawierający odpowiedź serwera.</span><span class="sxs-lookup"><span data-stu-id="f2612-115">This method returns an object containing the server's response.</span></span> <span data-ttu-id="f2612-116">Typ zwracanego <xref:System.Net.WebResponse> obiektu jest określany przez schemat identyfikatora URI żądania.</span><span class="sxs-lookup"><span data-stu-id="f2612-116">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="f2612-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f2612-117">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. <span data-ttu-id="f2612-118">Możesz uzyskać dostęp do właściwości `WebResponse` obiektu lub rzutować go do wystąpienia specyficznego dla protokołu, aby odczytywać właściwości specyficzne dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="f2612-118">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="f2612-119">Na przykład, aby uzyskać dostęp do właściwości specyficznych dla protokołu HTTP <xref:System.Net.HttpWebResponse> , należy rzutować `WebResponse` obiekt na `HttpWebResponse` odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f2612-119">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="f2612-120">Poniższy przykład kodu pokazuje, jak wyświetlić Właściwość specyficzną dla protokołu HTTP, która <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> jest wysyłana z odpowiedzią:</span><span class="sxs-lookup"><span data-stu-id="f2612-120">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. <span data-ttu-id="f2612-121">Aby uzyskać strumień zawierający dane odpowiedzi wysyłane przez serwer, wywołaj <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="f2612-121">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f2612-122">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f2612-122">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. <span data-ttu-id="f2612-123">Po odczytaniu danych z obiektu Response należy zamknąć je za pomocą <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody lub zamknąć strumień odpowiedzi przy użyciu <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f2612-123">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f2612-124">Jeśli nie zamkniesz obiektu Response lub strumienia, aplikacja może wyłączać połączenia z serwerem i nie może przetwarzać dodatkowych żądań.</span><span class="sxs-lookup"><span data-stu-id="f2612-124">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="f2612-125">Ponieważ `WebResponse.Close` Metoda wywołuje się `Stream.Close` , gdy zamyka odpowiedź, nie jest konieczne wywoływanie `Close` zarówno obiektów odpowiedzi, jak i strumienia, chociaż nie jest to szkodliwe.</span><span class="sxs-lookup"><span data-stu-id="f2612-125">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="f2612-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f2612-126">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="f2612-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2612-127">Example</span></span>

<span data-ttu-id="f2612-128">Poniższy przykład kodu przedstawia sposób tworzenia żądania na serwerze sieci Web i odczytywania danych w odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="f2612-128">The following code example shows how to create a request to a web server and read the data in its response:</span></span>

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a><span data-ttu-id="f2612-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2612-129">See also</span></span>

- [<span data-ttu-id="f2612-130">Tworzenie żądań internetowych</span><span class="sxs-lookup"><span data-stu-id="f2612-130">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="f2612-131">Używanie strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="f2612-131">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="f2612-132">Uzyskiwanie dostępu do Internetu za pomocą serwera proxy</span><span class="sxs-lookup"><span data-stu-id="f2612-132">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="f2612-133">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="f2612-133">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="f2612-134">Instrukcje: wysyłanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="f2612-134">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
