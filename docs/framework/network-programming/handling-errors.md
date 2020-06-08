---
title: Obsługa błędów
description: Dowiedz się więcej o wyjątkach dotyczących systemu i sieci Web zgłoszonych przez WebRequest i WebResponse. Użyj właściwości status, aby zrozumieć i rozwiązać problem.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, WebRequest and WebResponse classes exceptions
- Status property
- WebExceptions class, about WebExceptions class
- Timeout enumeration member
- ConnectFailure enumeration member
- TrustFailure enumeration member
- WebRequest class, exceptions
- requesting data from Internet, error handling
- Success enumeration member
- receiving data, errors
- ProtocolError enumeration member
- downloading Internet resources, error handling
- WebResponse class, exceptions
- SendFailure enumeration member
- errors [.NET Framework], WebRequest and WebResponse classes exceptions
- sending data, errors
- response to Internet request, error handling
- NameResolutionFailure enumeration member
- KeepAliveFailure enumeration member
- network resources, WebRequest and WebResponse classes exceptions
- RequestCanceled enumeration member
- ReceiveFailure enumeration member
- ServerProtocolViolation enumeration member
- ConnectionClosed enumeration member
- SecureChannelFailure enumeration member
ms.assetid: 657141cd-5cf5-4fdb-a4b2-4c040eba84b5
ms.openlocfilehash: 786b2bd8bc4d1b394bcfe920053b2f4f55d1cdea
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502577"
---
# <a name="handling-errors"></a><span data-ttu-id="53aa5-104">Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="53aa5-104">Handling Errors</span></span>

<span data-ttu-id="53aa5-105"><xref:System.Net.WebRequest>Klasy i <xref:System.Net.WebResponse> generują zarówno wyjątki systemowe (takie jak <xref:System.ArgumentException> ), jak i specyficzne dla sieci Web wyjątki (które są <xref:System.Net.WebException> generowane przez <xref:System.Net.WebRequest.GetResponse%2A> metodę).</span><span class="sxs-lookup"><span data-stu-id="53aa5-105">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
<span data-ttu-id="53aa5-106">Każdy element **WebException** zawiera <xref:System.Net.WebException.Status%2A> Właściwość, która zawiera wartość z <xref:System.Net.WebExceptionStatus> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="53aa5-106">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="53aa5-107">Można sprawdzić Właściwość **status** , aby określić błąd, który wystąpił, i podjąć odpowiednie kroki, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="53aa5-107">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
<span data-ttu-id="53aa5-108">W poniższej tabeli opisano możliwe wartości właściwości **stan** .</span><span class="sxs-lookup"><span data-stu-id="53aa5-108">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="53aa5-109">Stan</span><span class="sxs-lookup"><span data-stu-id="53aa5-109">Status</span></span>|<span data-ttu-id="53aa5-110">Opis</span><span class="sxs-lookup"><span data-stu-id="53aa5-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="53aa5-111">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="53aa5-111">ConnectFailure</span></span>|<span data-ttu-id="53aa5-112">Nie można skontaktować się z usługą zdalną na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="53aa5-112">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="53aa5-113">ConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="53aa5-113">ConnectionClosed</span></span>|<span data-ttu-id="53aa5-114">Połączenie zostało przedwcześnie zakończone.</span><span class="sxs-lookup"><span data-stu-id="53aa5-114">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="53aa5-115">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="53aa5-115">KeepAliveFailure</span></span>|<span data-ttu-id="53aa5-116">Serwer zamknął połączenie wykonane z zestawem nagłówkowym Keep-Alive.</span><span class="sxs-lookup"><span data-stu-id="53aa5-116">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="53aa5-117">NameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="53aa5-117">NameResolutionFailure</span></span>|<span data-ttu-id="53aa5-118">Usługa nazw nie może rozpoznać nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="53aa5-118">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="53aa5-119">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="53aa5-119">ProtocolError</span></span>|<span data-ttu-id="53aa5-120">Odpowiedź odebrana z serwera została ukończona, ale wykazała błąd na poziomie protokołu.</span><span class="sxs-lookup"><span data-stu-id="53aa5-120">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="53aa5-121">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="53aa5-121">ReceiveFailure</span></span>|<span data-ttu-id="53aa5-122">Nie odebrano kompletnej odpowiedzi z serwera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="53aa5-122">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="53aa5-123">RequestCanceled</span><span class="sxs-lookup"><span data-stu-id="53aa5-123">RequestCanceled</span></span>|<span data-ttu-id="53aa5-124">Żądanie zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="53aa5-124">The request was canceled.</span></span>|  
|<span data-ttu-id="53aa5-125">SecureChannelFailure</span><span class="sxs-lookup"><span data-stu-id="53aa5-125">SecureChannelFailure</span></span>|<span data-ttu-id="53aa5-126">Wystąpił błąd w łącznym kanale bezpiecznego kanału.</span><span class="sxs-lookup"><span data-stu-id="53aa5-126">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="53aa5-127">SendFailure</span><span class="sxs-lookup"><span data-stu-id="53aa5-127">SendFailure</span></span>|<span data-ttu-id="53aa5-128">Nie można wysłać kompletnego żądania do serwera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="53aa5-128">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="53aa5-129">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="53aa5-129">ServerProtocolViolation</span></span>|<span data-ttu-id="53aa5-130">Odpowiedź serwera nie jest prawidłową odpowiedzią HTTP.</span><span class="sxs-lookup"><span data-stu-id="53aa5-130">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="53aa5-131">Powodzenie</span><span class="sxs-lookup"><span data-stu-id="53aa5-131">Success</span></span>|<span data-ttu-id="53aa5-132">Nie wystąpił błąd.</span><span class="sxs-lookup"><span data-stu-id="53aa5-132">No error was encountered.</span></span>|  
|<span data-ttu-id="53aa5-133">Limit czasu</span><span class="sxs-lookup"><span data-stu-id="53aa5-133">Timeout</span></span>|<span data-ttu-id="53aa5-134">Nie odebrano odpowiedzi w określonym limicie czasu dla żądania.</span><span class="sxs-lookup"><span data-stu-id="53aa5-134">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="53aa5-135">TrustFailure</span><span class="sxs-lookup"><span data-stu-id="53aa5-135">TrustFailure</span></span>|<span data-ttu-id="53aa5-136">Nie można zweryfikować certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="53aa5-136">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="53aa5-137">MessageLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="53aa5-137">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="53aa5-138">Odebrano komunikat, który przekroczył określony limit podczas wysyłania żądania lub odebrania odpowiedzi z serwera.</span><span class="sxs-lookup"><span data-stu-id="53aa5-138">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="53aa5-139">Oczekiwanie</span><span class="sxs-lookup"><span data-stu-id="53aa5-139">Pending</span></span>|<span data-ttu-id="53aa5-140">Wewnętrzne asynchroniczne żądanie jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="53aa5-140">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="53aa5-141">PipelineFailure</span><span class="sxs-lookup"><span data-stu-id="53aa5-141">PipelineFailure</span></span>|<span data-ttu-id="53aa5-142">Ta wartość obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="53aa5-142">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="53aa5-143">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="53aa5-143">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="53aa5-144">Usługa rozpoznawania nazw nie może rozpoznać nazwy hosta serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="53aa5-144">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="53aa5-145">UnknownError</span><span class="sxs-lookup"><span data-stu-id="53aa5-145">UnknownError</span></span>|<span data-ttu-id="53aa5-146">Wystąpił wyjątek nieznanego typu.</span><span class="sxs-lookup"><span data-stu-id="53aa5-146">An exception of unknown type has occurred.</span></span>|  
  
<span data-ttu-id="53aa5-147">Gdy właściwość **status** ma wartość **WebExceptionStatus. ProtocolError**, dostępna jest **WebResponse** , która zawiera odpowiedź z serwera.</span><span class="sxs-lookup"><span data-stu-id="53aa5-147">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="53aa5-148">Tę odpowiedź można sprawdzić w celu ustalenia rzeczywistego źródła błędu protokołu.</span><span class="sxs-lookup"><span data-stu-id="53aa5-148">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
<span data-ttu-id="53aa5-149">Poniższy przykład przedstawia sposób przechwytywania **wyjątku WebException**.</span><span class="sxs-lookup"><span data-stu-id="53aa5-149">The following example shows how to catch a **WebException**.</span></span>  
  
```csharp  
try
{  
    // Create a request instance.  
    WebRequest myRequest =
    WebRequest.Create("http://www.contoso.com");  
    // Get the response.  
    WebResponse myResponse = myRequest.GetResponse();  
    //Get a readable stream from the server.
    Stream sr = myResponse.GetResponseStream();  
  
    //Read from the stream and write any data to the console.  
    bytesread = sr.Read( myBuffer, 0, length);  
    while( bytesread > 0 )
    {  
        for (int i=0; i<bytesread; i++) {  
            Console.Write( "{0}", myBuffer[i]);  
        }  
        Console.WriteLine();  
        bytesread = sr.Read( myBuffer, 0, length);  
    }  
    sr.Close();  
    myResponse.Close();  
}  
catch (WebException webExcp)
{  
    // If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.");  
    // Write out the WebException message.  
    Console.WriteLine(webExcp.ToString());  
    // Get the WebException status code.  
    WebExceptionStatus status =  webExcp.Status;  
    // If status is WebExceptionStatus.ProtocolError,
    //   there has been a protocol error and a WebResponse
    //   should exist. Display the protocol error.  
    if (status == WebExceptionStatus.ProtocolError) {  
        Console.Write("The server returned protocol error ");  
        // Get HttpWebResponse so that you can check the HTTP status code.  
        HttpWebResponse httpResponse = (HttpWebResponse)webExcp.Response;  
        Console.WriteLine((int)httpResponse.StatusCode + " - "  
           + httpResponse.StatusCode);  
    }  
}  
catch (Exception e)
{  
    // Code to catch other exceptions goes here.  
}  
```  
  
```vb  
Try  
    ' Create a request instance.  
    Dim myRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ' Get the response.  
    Dim myResponse As WebResponse = myRequest.GetResponse()  
    'Get a readable stream from the server.
    Dim sr As Stream = myResponse.GetResponseStream()  
  
    Dim i As Integer
    'Read from the stream and write any data to the console.  
    bytesread = sr.Read(myBuffer, 0, length)  
    While bytesread > 0  
        For i = 0 To bytesread - 1  
            Console.Write("{0}", myBuffer(i))  
        Next i  
        Console.WriteLine()  
        bytesread = sr.Read(myBuffer, 0, length)  
    End While  
    sr.Close()  
    myResponse.Close()  
Catch webExcp As WebException  
    ' If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.")  
    ' Write out the WebException message.  
    Console.WriteLine(webExcp.ToString())  
    ' Get the WebException status code.  
    Dim status As WebExceptionStatus = webExcp.Status  
    ' If status is WebExceptionStatus.ProtocolError,
    '   there has been a protocol error and a WebResponse
    '   should exist. Display the protocol error.  
    If status = WebExceptionStatus.ProtocolError Then  
        Console.Write("The server returned protocol error ")  
        ' Get HttpWebResponse so that you can check the HTTP status code.  
        Dim httpResponse As HttpWebResponse = _  
           CType(webExcp.Response, HttpWebResponse)  
        Console.WriteLine(CInt(httpResponse.StatusCode).ToString() & _  
           " - " & httpResponse.StatusCode.ToString())  
    End If  
Catch e As Exception  
    ' Code to catch other exceptions goes here.  
End Try  
```  
  
<span data-ttu-id="53aa5-150">Aplikacje korzystające z <xref:System.Net.Sockets.Socket> klasy throw w <xref:System.Net.Sockets.SocketException> przypadku wystąpienia błędów w gnieździe Windows.</span><span class="sxs-lookup"><span data-stu-id="53aa5-150">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="53aa5-151"><xref:System.Net.Sockets.TcpClient>Klasy, <xref:System.Net.Sockets.TcpListener> , i <xref:System.Net.Sockets.UdpClient> są zbudowane na podstawie klasy **Socket** i generują **SocketExceptions** .</span><span class="sxs-lookup"><span data-stu-id="53aa5-151">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
<span data-ttu-id="53aa5-152">Gdy zostanie zgłoszony obiekt **SocketException** , Klasa **SocketException** ustawia <xref:System.Net.Sockets.SocketException.ErrorCode%2A> Właściwość na ostatni błąd gniazda systemu operacyjnego, który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="53aa5-152">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="53aa5-153">Aby uzyskać więcej informacji na temat kodów błędów gniazda, zobacz dokumentację kodu błędu interfejsu API Winsock 2,0 w witrynie MSDN.</span><span class="sxs-lookup"><span data-stu-id="53aa5-153">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53aa5-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53aa5-154">See also</span></span>

- [<span data-ttu-id="53aa5-155">Obsługa i zgłaszanie wyjątków w programie .NET</span><span class="sxs-lookup"><span data-stu-id="53aa5-155">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="53aa5-156">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="53aa5-156">Requesting Data</span></span>](requesting-data.md)
