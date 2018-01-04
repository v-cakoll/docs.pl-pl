---
title: "Obsługa błędów"
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
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c7d9c08e38c2d82381c94e8813ef0312806bd010
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="handling-errors"></a><span data-ttu-id="6e177-102">Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="6e177-102">Handling Errors</span></span>
<span data-ttu-id="6e177-103"><xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy zgłaszają wyjątki zarówno system (takich jak <xref:System.ArgumentException>) oraz wyjątków dotyczących sieci Web (, które są <xref:System.Net.WebException> zgłaszanych przez <xref:System.Net.WebRequest.GetResponse%2A> — metoda).</span><span class="sxs-lookup"><span data-stu-id="6e177-103">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
 <span data-ttu-id="6e177-104">Każdy **WebException** obejmuje <xref:System.Net.WebException.Status%2A> właściwość, która zawiera wartość z zakresu od <xref:System.Net.WebExceptionStatus> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="6e177-104">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="6e177-105">Można sprawdzić **stan** właściwości, aby określić wystąpił błąd i podejmij odpowiednie kroki, aby usunąć błąd.</span><span class="sxs-lookup"><span data-stu-id="6e177-105">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
 <span data-ttu-id="6e177-106">W poniższej tabeli opisano możliwe wartości **stan** właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e177-106">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="6e177-107">Stan</span><span class="sxs-lookup"><span data-stu-id="6e177-107">Status</span></span>|<span data-ttu-id="6e177-108">Opis</span><span class="sxs-lookup"><span data-stu-id="6e177-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6e177-109">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="6e177-109">ConnectFailure</span></span>|<span data-ttu-id="6e177-110">Nie można skontaktować się z usługi zdalnej na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="6e177-110">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="6e177-111">ConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="6e177-111">ConnectionClosed</span></span>|<span data-ttu-id="6e177-112">Połączenie zostało przedwcześnie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="6e177-112">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="6e177-113">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="6e177-113">KeepAliveFailure</span></span>|<span data-ttu-id="6e177-114">Serwer zamknął połączenie zostało nawiązane przy użyciu zestawu Keep-alive nagłówka.</span><span class="sxs-lookup"><span data-stu-id="6e177-114">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="6e177-115">NameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="6e177-115">NameResolutionFailure</span></span>|<span data-ttu-id="6e177-116">Nazwa usługi nie można rozpoznać nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="6e177-116">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="6e177-117">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="6e177-117">ProtocolError</span></span>|<span data-ttu-id="6e177-118">Odpowiedzi odebrany od serwera zostało ukończone, ale wskazany błąd na poziomie protokołu.</span><span class="sxs-lookup"><span data-stu-id="6e177-118">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="6e177-119">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="6e177-119">ReceiveFailure</span></span>|<span data-ttu-id="6e177-120">Nie odebrano pełnej odpowiedzi z serwera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="6e177-120">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="6e177-121">RequestCanceled</span><span class="sxs-lookup"><span data-stu-id="6e177-121">RequestCanceled</span></span>|<span data-ttu-id="6e177-122">Żądanie zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="6e177-122">The request was canceled.</span></span>|  
|<span data-ttu-id="6e177-123">SecureChannelFailure</span><span class="sxs-lookup"><span data-stu-id="6e177-123">SecureChannelFailure</span></span>|<span data-ttu-id="6e177-124">Wystąpił błąd w łączu bezpiecznego kanału.</span><span class="sxs-lookup"><span data-stu-id="6e177-124">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="6e177-125">SendFailure</span><span class="sxs-lookup"><span data-stu-id="6e177-125">SendFailure</span></span>|<span data-ttu-id="6e177-126">Nie można wysłać wykonać żądanie do serwera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="6e177-126">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="6e177-127">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="6e177-127">ServerProtocolViolation</span></span>|<span data-ttu-id="6e177-128">Odpowiedź serwera nie jest prawidłowa odpowiedź HTTP.</span><span class="sxs-lookup"><span data-stu-id="6e177-128">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="6e177-129">Powodzenie</span><span class="sxs-lookup"><span data-stu-id="6e177-129">Success</span></span>|<span data-ttu-id="6e177-130">Napotkano błąd.</span><span class="sxs-lookup"><span data-stu-id="6e177-130">No error was encountered.</span></span>|  
|<span data-ttu-id="6e177-131">Limit czasu</span><span class="sxs-lookup"><span data-stu-id="6e177-131">Timeout</span></span>|<span data-ttu-id="6e177-132">Nie otrzymano odpowiedzi w ciągu limitu czasu dla żądania.</span><span class="sxs-lookup"><span data-stu-id="6e177-132">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="6e177-133">TrustFailure</span><span class="sxs-lookup"><span data-stu-id="6e177-133">TrustFailure</span></span>|<span data-ttu-id="6e177-134">Nie można sprawdzić poprawności certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="6e177-134">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="6e177-135">MessageLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="6e177-135">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="6e177-136">Odebrano wiadomość, która przekracza limit określony podczas wysyłania żądania lub odpowiedzi z serwera.</span><span class="sxs-lookup"><span data-stu-id="6e177-136">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="6e177-137">Oczekujące</span><span class="sxs-lookup"><span data-stu-id="6e177-137">Pending</span></span>|<span data-ttu-id="6e177-138">Wewnętrzne żądanie asynchroniczne oczekuje.</span><span class="sxs-lookup"><span data-stu-id="6e177-138">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="6e177-139">PipelineFailure</span><span class="sxs-lookup"><span data-stu-id="6e177-139">PipelineFailure</span></span>|<span data-ttu-id="6e177-140">Ta wartość obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6e177-140">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="6e177-141">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="6e177-141">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="6e177-142">Usługa rozpoznawania nazw nie można rozpoznać nazwy hosta serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="6e177-142">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="6e177-143">Nieznany</span><span class="sxs-lookup"><span data-stu-id="6e177-143">UnknownError</span></span>|<span data-ttu-id="6e177-144">Wystąpił nieznany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6e177-144">An exception of unknown type has occurred.</span></span>|  
  
 <span data-ttu-id="6e177-145">Gdy **stan** właściwość jest **WebExceptionStatus.ProtocolError**, **WebResponse** zawierający odpowiedzi z serwera jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="6e177-145">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="6e177-146">Tej odpowiedzi do ustalenia rzeczywistego źródła błędu protokołu, można sprawdzić.</span><span class="sxs-lookup"><span data-stu-id="6e177-146">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
 <span data-ttu-id="6e177-147">Poniższy przykład przedstawia sposób catch **WebException**.</span><span class="sxs-lookup"><span data-stu-id="6e177-147">The following example shows how to catch a **WebException**.</span></span>  
  
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
  
 <span data-ttu-id="6e177-148">Aplikacje używające <xref:System.Net.Sockets.Socket> throw klasy <xref:System.Net.Sockets.SocketException> po wystąpić błędy w gnieździe systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6e177-148">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="6e177-149"><xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, I <xref:System.Net.Sockets.UdpClient> klas są wbudowane nad **gniazda** klasy i zgłosić **SocketExceptions** również.</span><span class="sxs-lookup"><span data-stu-id="6e177-149">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
 <span data-ttu-id="6e177-150">Gdy **socketexception —** jest zgłaszany, **socketexception —** klasy zestawy <xref:System.Net.Sockets.SocketException.ErrorCode%2A> właściwości ostatni błąd gniazda systemu operacyjnego, który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="6e177-150">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="6e177-151">Aby uzyskać więcej informacji o kodach błędów gniazda w dokumentacji interfejsu API 2.0 Winsock błąd kodu w bibliotece MSDN.</span><span class="sxs-lookup"><span data-stu-id="6e177-151">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e177-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e177-152">See Also</span></span>  
 [<span data-ttu-id="6e177-153">Podstawowe założenia obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="6e177-153">Exception Handling Fundamentals</span></span>](../../../docs/standard/exceptions/exception-handling-fundamentals.md)  
 [<span data-ttu-id="6e177-154">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="6e177-154">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
