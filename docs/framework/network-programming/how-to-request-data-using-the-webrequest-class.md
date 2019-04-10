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
ms.openlocfilehash: 1d8f501e90f3942bbfd95fc06e9fdd79d8f6430e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334214"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="3419f-102">Instrukcje: Żądanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="3419f-102">How to: Request data by using the WebRequest class</span></span>
<span data-ttu-id="3419f-103">Poniższa procedura opisuje kroki, aby zażądać zasobu, np. strony sieci Web lub plik z serwera.</span><span class="sxs-lookup"><span data-stu-id="3419f-103">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="3419f-104">Zasób musi być identyfikowany przez identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="3419f-104">The resource must be identified by a URI.</span></span>  
  
## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="3419f-105">Żądanie danych z serwera hosta</span><span class="sxs-lookup"><span data-stu-id="3419f-105">To request data from a host server</span></span>  
  
1. <span data-ttu-id="3419f-106">Tworzenie <xref:System.Net.WebRequest> wystąpienia, wywołując <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> za pomocą identyfikatora URI zasobu.</span><span class="sxs-lookup"><span data-stu-id="3419f-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="3419f-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3419f-107">For example:</span></span> 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/default.html");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/default.html")  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="3419f-108">Program .NET Framework zawiera klasy pochodne klasy specyficzne dla protokołu <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klas pochodnych identyfikatorów URI, które zaczynają się od *http:*, *https:*, *ftp:* , a *pliku:*.</span><span class="sxs-lookup"><span data-stu-id="3419f-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>
    <span data-ttu-id="3419f-109">Jeśli musisz set lub odczytu właściwości specyficzne dla protokołu, należy rzutować swoje <xref:System.Net.WebRequest> lub <xref:System.Net.WebResponse> obiektu z typem obiektów specyficznych dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="3419f-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="3419f-110">Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="3419f-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span> 
  
2. <span data-ttu-id="3419f-111">Ustaw wszystkie wartości właściwości, które są potrzebne w Twojej `WebRequest` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3419f-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="3419f-112">Na przykład, aby włączyć uwierzytelnianie, należy ustawić <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> właściwości wystąpienia <xref:System.Net.NetworkCredential> klasy:</span><span class="sxs-lookup"><span data-stu-id="3419f-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3. <span data-ttu-id="3419f-113">Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3419f-113">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3419f-114">Ta metoda zwraca obiekt zawierający odpowiedź serwera.</span><span class="sxs-lookup"><span data-stu-id="3419f-114">This method returns an object containing the server's response.</span></span> <span data-ttu-id="3419f-115">Zwrócony <xref:System.Net.WebResponse> typ obiektu jest określana przez schemat identyfikatora URI żądania.</span><span class="sxs-lookup"><span data-stu-id="3419f-115">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="3419f-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3419f-116">For example:</span></span>
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
4. <span data-ttu-id="3419f-117">Można uzyskać dostęp do właściwości usługi `WebResponse` obiektu lub go rzutować do wystąpienia oparte na protokole można odczytać właściwości specyficzne dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="3419f-117">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span> 

    <span data-ttu-id="3419f-118">Na przykład, aby właściwości dostępu właściwe dla protokołu HTTP <xref:System.Net.HttpWebResponse>, rzutowania swoje `WebResponse` obiekt `HttpWebResponse` odwołania.</span><span class="sxs-lookup"><span data-stu-id="3419f-118">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="3419f-119">Poniższy przykład kodu pokazuje sposób wyświetlania specyficzne dla protokołu HTTP <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> właściwości wysyłane odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="3419f-119">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5. <span data-ttu-id="3419f-120">Aby uzyskać strumienia zawierające dane odpowiedzi wysyłane przez serwer, należy wywołać <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="3419f-120">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3419f-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3419f-121">For example:</span></span>  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6. <span data-ttu-id="3419f-122">Po zapoznaniu się dane z obiektu odpowiedzi, albo zamknij je za pomocą <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody lub zamknij odpowiedzi przesyłania strumieniowego przy użyciu <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="3419f-122">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3419f-123">Jeśli nie zamkniesz obiekt odpowiedzi lub strumienia, aplikację można Brak połączenia z serwerem i stają się nie może przetworzyć żądań dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="3419f-123">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="3419f-124">Ponieważ `WebResponse.Close` wywołania metody `Stream.Close` jego zamknięciem odpowiedzi nie jest konieczne wywołać `Close` obiektów odpowiedzi i strumienia, mimo że takie postępowania tak nie jest szkodliwy.</span><span class="sxs-lookup"><span data-stu-id="3419f-124">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="3419f-125">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3419f-125">For example:</span></span>
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="3419f-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="3419f-126">Example</span></span>  

<span data-ttu-id="3419f-127">Poniższy przykład kodu pokazuje, jak utworzyć żądanie do serwera sieci web i odczytywać je w swojej odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="3419f-127">The following code example shows how to create a request to a web server and read the data in its response:</span></span>  
  
[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a><span data-ttu-id="3419f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3419f-128">See also</span></span>

- [<span data-ttu-id="3419f-129">Tworzenie żądań internetowych</span><span class="sxs-lookup"><span data-stu-id="3419f-129">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="3419f-130">Stosowanie strumieni w sieci</span><span class="sxs-lookup"><span data-stu-id="3419f-130">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="3419f-131">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="3419f-131">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="3419f-132">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="3419f-132">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="3419f-133">Instrukcje: Wyślij dane przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="3419f-133">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
