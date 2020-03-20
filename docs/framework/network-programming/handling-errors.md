---
title: Obsługa błędów
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
ms.openlocfilehash: f5be5d8e14d7aa2d98009fc10c9cce314e745ed1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180871"
---
# <a name="handling-errors"></a><span data-ttu-id="cf254-102">Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="cf254-102">Handling Errors</span></span>

<span data-ttu-id="cf254-103">Klasy <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> i zgłaszać zarówno wyjątki <xref:System.ArgumentException>systemowe (takie jak ) <xref:System.Net.WebException> i <xref:System.Net.WebRequest.GetResponse%2A> wyjątki specyficzne dla sieci Web (które są generowane przez metodę).</span><span class="sxs-lookup"><span data-stu-id="cf254-103">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
<span data-ttu-id="cf254-104">Każdy **WebException** <xref:System.Net.WebException.Status%2A> zawiera właściwość, która <xref:System.Net.WebExceptionStatus> zawiera wartość z wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cf254-104">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="cf254-105">Można zbadać **Status** właściwości, aby określić błąd, który wystąpił i podjąć odpowiednie kroki, aby rozwiązać błąd.</span><span class="sxs-lookup"><span data-stu-id="cf254-105">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
<span data-ttu-id="cf254-106">W poniższej tabeli opisano możliwe wartości właściwości **Status.**</span><span class="sxs-lookup"><span data-stu-id="cf254-106">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="cf254-107">Stan</span><span class="sxs-lookup"><span data-stu-id="cf254-107">Status</span></span>|<span data-ttu-id="cf254-108">Opis</span><span class="sxs-lookup"><span data-stu-id="cf254-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cf254-109">ConnectFailure (Połączenie)</span><span class="sxs-lookup"><span data-stu-id="cf254-109">ConnectFailure</span></span>|<span data-ttu-id="cf254-110">Nie można skontaktować się z usługą zdalną na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="cf254-110">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="cf254-111">ConnectionClosed (Zamknięte połączenie)</span><span class="sxs-lookup"><span data-stu-id="cf254-111">ConnectionClosed</span></span>|<span data-ttu-id="cf254-112">Połączenie zostało zamknięte przedwcześnie.</span><span class="sxs-lookup"><span data-stu-id="cf254-112">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="cf254-113">KeepAliveWłasna</span><span class="sxs-lookup"><span data-stu-id="cf254-113">KeepAliveFailure</span></span>|<span data-ttu-id="cf254-114">Serwer zamknął połączenie nawiązanym z zestawem nagłówków Keep-alive.</span><span class="sxs-lookup"><span data-stu-id="cf254-114">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="cf254-115">NazwaResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="cf254-115">NameResolutionFailure</span></span>|<span data-ttu-id="cf254-116">Usługa nazw nie może rozpoznać nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="cf254-116">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="cf254-117">ProtokółError</span><span class="sxs-lookup"><span data-stu-id="cf254-117">ProtocolError</span></span>|<span data-ttu-id="cf254-118">Odpowiedź otrzymana z serwera została ukończona, ale wskazywała błąd na poziomie protokołu.</span><span class="sxs-lookup"><span data-stu-id="cf254-118">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="cf254-119">ReceiveFailure (Nieujmowie)</span><span class="sxs-lookup"><span data-stu-id="cf254-119">ReceiveFailure</span></span>|<span data-ttu-id="cf254-120">Pełna odpowiedź nie została odebrana z serwera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="cf254-120">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="cf254-121">RequestCanceled (Wyliczył)</span><span class="sxs-lookup"><span data-stu-id="cf254-121">RequestCanceled</span></span>|<span data-ttu-id="cf254-122">Żądanie zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="cf254-122">The request was canceled.</span></span>|  
|<span data-ttu-id="cf254-123">SecureChannelWładnia</span><span class="sxs-lookup"><span data-stu-id="cf254-123">SecureChannelFailure</span></span>|<span data-ttu-id="cf254-124">Wystąpił błąd w łączu bezpiecznego kanału.</span><span class="sxs-lookup"><span data-stu-id="cf254-124">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="cf254-125">SendFailure (Niebezpieczeństwo wyślij)</span><span class="sxs-lookup"><span data-stu-id="cf254-125">SendFailure</span></span>|<span data-ttu-id="cf254-126">Nie można wysłać kompletnego żądania do serwera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="cf254-126">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="cf254-127">ServerProtocolViolation (Proces serweraProtocolViolation)</span><span class="sxs-lookup"><span data-stu-id="cf254-127">ServerProtocolViolation</span></span>|<span data-ttu-id="cf254-128">Odpowiedź serwera nie była prawidłową odpowiedzią HTTP.</span><span class="sxs-lookup"><span data-stu-id="cf254-128">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="cf254-129">Powodzenie</span><span class="sxs-lookup"><span data-stu-id="cf254-129">Success</span></span>|<span data-ttu-id="cf254-130">Nie wystąpił żaden błąd.</span><span class="sxs-lookup"><span data-stu-id="cf254-130">No error was encountered.</span></span>|  
|<span data-ttu-id="cf254-131">Limit czasu</span><span class="sxs-lookup"><span data-stu-id="cf254-131">Timeout</span></span>|<span data-ttu-id="cf254-132">W terminie wyznaczonym dla wniosku nie otrzymano odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="cf254-132">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="cf254-133">ZaufanieWłasność</span><span class="sxs-lookup"><span data-stu-id="cf254-133">TrustFailure</span></span>|<span data-ttu-id="cf254-134">Nie można zweryfikować certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="cf254-134">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="cf254-135">WiadomośćLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="cf254-135">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="cf254-136">Odebrano wiadomość, która przekroczyła określony limit podczas wysyłania żądania lub odbierania odpowiedzi z serwera.</span><span class="sxs-lookup"><span data-stu-id="cf254-136">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="cf254-137">Oczekujące</span><span class="sxs-lookup"><span data-stu-id="cf254-137">Pending</span></span>|<span data-ttu-id="cf254-138">Oczekuje na wewnętrzne żądanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="cf254-138">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="cf254-139">Awaria rurociągu</span><span class="sxs-lookup"><span data-stu-id="cf254-139">PipelineFailure</span></span>|<span data-ttu-id="cf254-140">Ta wartość obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="cf254-140">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="cf254-141">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="cf254-141">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="cf254-142">Usługa rozpoznawania nazw nie może rozpoznać nazwy hosta serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="cf254-142">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="cf254-143">NieznanyError</span><span class="sxs-lookup"><span data-stu-id="cf254-143">UnknownError</span></span>|<span data-ttu-id="cf254-144">Wystąpił wyjątek nieznanego typu.</span><span class="sxs-lookup"><span data-stu-id="cf254-144">An exception of unknown type has occurred.</span></span>|  
  
<span data-ttu-id="cf254-145">Gdy **właściwość Status** jest **WebExceptionStatus.ProtocolError**, **WebResponse,** który zawiera odpowiedź z serwera jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="cf254-145">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="cf254-146">Można sprawdzić tę odpowiedź, aby określić rzeczywiste źródło błędu protokołu.</span><span class="sxs-lookup"><span data-stu-id="cf254-146">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
<span data-ttu-id="cf254-147">W poniższym przykładzie pokazano, jak złapać **WebException**.</span><span class="sxs-lookup"><span data-stu-id="cf254-147">The following example shows how to catch a **WebException**.</span></span>  
  
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
  
<span data-ttu-id="cf254-148">Aplikacje, <xref:System.Net.Sockets.Socket> które <xref:System.Net.Sockets.SocketException> używają rzutu klasy, gdy wystąpią błędy w gnieździe systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cf254-148">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="cf254-149"><xref:System.Net.Sockets.TcpListener> <xref:System.Net.Sockets.UdpClient> , <xref:System.Net.Sockets.TcpClient>i klasy są zbudowane na górze **Socket** klasy i rzucać **SocketExceptions,** jak również.</span><span class="sxs-lookup"><span data-stu-id="cf254-149">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
<span data-ttu-id="cf254-150">Po uruchomieniu **SocketException,** **SocketException** klasa <xref:System.Net.Sockets.SocketException.ErrorCode%2A> ustawia właściwość do ostatniego błędu gniazda systemu operacyjnego, który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="cf254-150">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="cf254-151">Aby uzyskać więcej informacji na temat kodów błędów gniazda, zobacz dokumentację kodu błędu interfejsu API Winsock 2.0 w sieci MSDN.</span><span class="sxs-lookup"><span data-stu-id="cf254-151">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf254-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf254-152">See also</span></span>

- [<span data-ttu-id="cf254-153">Obsługa i zgłaszanie wyjątków w .NET</span><span class="sxs-lookup"><span data-stu-id="cf254-153">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="cf254-154">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="cf254-154">Requesting Data</span></span>](requesting-data.md)
