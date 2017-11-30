---
title: "Porady: dane przy użyciu klasy WebRequest żądania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e831f3c305716afe11df6c0b1e21db1ed5a4f01e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-request-data-using-the-webrequest-class"></a><span data-ttu-id="66b5a-102">Porady: dane przy użyciu klasy WebRequest żądania</span><span class="sxs-lookup"><span data-stu-id="66b5a-102">How to: Request Data Using the WebRequest Class</span></span>
<span data-ttu-id="66b5a-103">W poniższej procedurze opisano kroki używane do żądania zasobów z serwera, na przykład, strony sieci Web lub pliku.</span><span class="sxs-lookup"><span data-stu-id="66b5a-103">The following procedure describes the steps used to request a resource from a server, for example, a Web page or file.</span></span> <span data-ttu-id="66b5a-104">Zasób musi być identyfikowany przez identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="66b5a-104">The resource must be identified by a URI.</span></span>  
  
### <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="66b5a-105">Żądanie danych z serwera hosta</span><span class="sxs-lookup"><span data-stu-id="66b5a-105">To request data from a host server</span></span>  
  
1.  <span data-ttu-id="66b5a-106">Utwórz <xref:System.Net.WebRequest> wystąpienia przez wywołanie metody <xref:System.Net.WebRequest.Create%2A> o identyfikatorze URI zasobu.</span><span class="sxs-lookup"><span data-stu-id="66b5a-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="66b5a-107">Platforma .NET Framework zapewnia oparte na protokole klasy pochodzące od **WebRequest** i **WebResponse** identyfikatory URI, które rozpoczynają się od "http:", "https:", "ftp:", i "pliku:".</span><span class="sxs-lookup"><span data-stu-id="66b5a-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="66b5a-108">Aby uzyskać dostęp do zasobów przy użyciu innych protokołów, musi implementować klasy specyficzne dla protokołu, pochodzących z **WebRequest** i **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="66b5a-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="66b5a-109">Aby uzyskać więcej informacji, zobacz [programowania podłączany protokołów](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span><span class="sxs-lookup"><span data-stu-id="66b5a-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="66b5a-110">Ustawianie wartości właściwości wymaganych w **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="66b5a-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="66b5a-111">Na przykład, aby włączyć uwierzytelnianie, należy ustawić **poświadczenia** dla właściwości wystąpienia <xref:System.Net.NetworkCredential> klasy.</span><span class="sxs-lookup"><span data-stu-id="66b5a-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="66b5a-112">W większości przypadków **WebRequest** klasy są wystarczające, aby odbierać dane.</span><span class="sxs-lookup"><span data-stu-id="66b5a-112">In most cases, the **WebRequest** class is sufficient to receive data.</span></span> <span data-ttu-id="66b5a-113">Jednak jeśli należy ustawić właściwości specyficzne dla protokołu, należy rzutować **WebRequest** typowi specyficzne dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="66b5a-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="66b5a-114">Na przykład do właściwości dostępu specyficzne dla protokołu HTTP <xref:System.Net.HttpWebRequest>, rzutowanie **WebRequest** do **HttpWebRequest** odwołania.</span><span class="sxs-lookup"><span data-stu-id="66b5a-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="66b5a-115">W poniższym przykładzie przedstawiono sposób ustawiania specyficzne dla protokołu HTTP <xref:System.Net.HttpWebRequest.UserAgent%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="66b5a-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="66b5a-116">Aby wysłać żądania do serwera, należy wywołać <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span><span class="sxs-lookup"><span data-stu-id="66b5a-116">To send the request to the server, call <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="66b5a-117">Rzeczywisty typ zwróconego **WebResponse** obiektu jest określane przez schemat żądanego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="66b5a-117">The actual type of the returned **WebResponse** object is determined by the scheme of the requested URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="66b5a-118">Po zakończeniu <xref:System.Net.WebResponse> obiektu, należy go zamknąć, wywołując <xref:System.Net.WebResponse.Close%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="66b5a-118">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="66b5a-119">Alternatywnie, jeśli z obiektu odpowiedzi stają się coraz w strumieniu odpowiedzi, można zamknąć strumienia przez wywołanie metody <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="66b5a-119">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="66b5a-120">Jeśli nie zamkniesz odpowiedzi lub strumienia, aplikacja może zabraknie połączenia z serwerem i stają się nie może przetworzyć żądania dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="66b5a-120">If you do not close either the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
4.  <span data-ttu-id="66b5a-121">Można uzyskać dostęp do właściwości **WebResponse** lub Zastosuj rzutowanie **WebResponse** do wystąpienia Protokołem do odczytu właściwości specyficzne dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="66b5a-121">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="66b5a-122">Na przykład do właściwości dostępu specyficzne dla protokołu HTTP <xref:System.Net.HttpWebResponse>, rzutowanie **WebResponse** do **HttpWebResponse** odwołania.</span><span class="sxs-lookup"><span data-stu-id="66b5a-122">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to a **HttpWebResponse** reference.</span></span> <span data-ttu-id="66b5a-123">Poniższy przykład kodu pokazuje, jak można wyświetlić informacje o stanie wysyłane z odpowiedzią.</span><span class="sxs-lookup"><span data-stu-id="66b5a-123">The following code example shows how to display the status information sent with a response.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  <span data-ttu-id="66b5a-124">Aby uzyskać strumienia zawierające dane odpowiedzi wysyłane przez serwer, należy użyć <xref:System.Net.HttpWebResponse.GetResponseStream%2A> metody **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="66b5a-124">To get the stream containing response data sent by the server, use the <xref:System.Net.HttpWebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream ();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  <span data-ttu-id="66b5a-125">Po odczytaniu danych z odpowiedzi, należy albo zamknąć przy użyciu strumienia odpowiedzi **Stream.Close** metody lub zamknij odpowiedzi, za pomocą **WebResponse.Close** metody.</span><span class="sxs-lookup"><span data-stu-id="66b5a-125">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="66b5a-126">Nie jest konieczne do wywołania **Zamknij** metody w strumieniu odpowiedzi i **WebResponse**, ale spowoduje to nie jest szkodliwe.</span><span class="sxs-lookup"><span data-stu-id="66b5a-126">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span> <span data-ttu-id="66b5a-127">**WebResponse.Close** wywołania **Stream.Close** podczas zamykania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="66b5a-127">**WebResponse.Close** calls **Stream.Close** when closing the response.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="66b5a-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="66b5a-128">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main ()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create (  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close ();  
            response.Close ();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Net  
Imports System.Text  
Namespace Examples.System.Net  
    Public Class WebRequestGetExample  
  
        Public Shared Sub Main()  
            ' Create a request for the URL.   
            Dim request As WebRequest = _  
              WebRequest.Create("http://www.contoso.com/default.html")  
            ' If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            Dim dataStream As Stream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams and the response.  
            reader.Close()  
            response.Close()  
        End Sub   
    End Class   
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="66b5a-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66b5a-129">See Also</span></span>  
 [<span data-ttu-id="66b5a-130">Tworzenie żądania internetowe</span><span class="sxs-lookup"><span data-stu-id="66b5a-130">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [<span data-ttu-id="66b5a-131">W sieci za pomocą strumieni</span><span class="sxs-lookup"><span data-stu-id="66b5a-131">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="66b5a-132">Dostęp do Internetu za pośrednictwem serwera Proxy</span><span class="sxs-lookup"><span data-stu-id="66b5a-132">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="66b5a-133">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="66b5a-133">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 [<span data-ttu-id="66b5a-134">Porady: wysyłanie danych przy użyciu klasy WebRequest</span><span class="sxs-lookup"><span data-stu-id="66b5a-134">How to: Send Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
