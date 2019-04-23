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
ms.openlocfilehash: 26e2a25855485bdd19d30e8497d0f75b7d4432e0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097164"
---
# <a name="handling-errors"></a><span data-ttu-id="762f3-102">Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="762f3-102">Handling Errors</span></span>
<span data-ttu-id="762f3-103"><xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy zgłaszają wyjątki zarówno system (takie jak <xref:System.ArgumentException>) i wyjątków specyficzne dla sieci Web (służą do <xref:System.Net.WebException> zgłoszony przez <xref:System.Net.WebRequest.GetResponse%2A> metody).</span><span class="sxs-lookup"><span data-stu-id="762f3-103">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
 <span data-ttu-id="762f3-104">Każdy **WebException** obejmuje <xref:System.Net.WebException.Status%2A> właściwość, która zawiera wartość z zakresu od <xref:System.Net.WebExceptionStatus> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="762f3-104">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="762f3-105">Można sprawdzić **stan** właściwości, aby ustalić błędu, który wystąpił i wykonaj odpowiednie czynności, aby rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="762f3-105">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
 <span data-ttu-id="762f3-106">W poniższej tabeli opisano możliwe wartości **stan** właściwości.</span><span class="sxs-lookup"><span data-stu-id="762f3-106">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="762f3-107">Stan</span><span class="sxs-lookup"><span data-stu-id="762f3-107">Status</span></span>|<span data-ttu-id="762f3-108">Opis</span><span class="sxs-lookup"><span data-stu-id="762f3-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="762f3-109">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="762f3-109">ConnectFailure</span></span>|<span data-ttu-id="762f3-110">Nie można skontaktować się z usługi zdalnej na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="762f3-110">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="762f3-111">ConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="762f3-111">ConnectionClosed</span></span>|<span data-ttu-id="762f3-112">Połączenie zostało przedwcześnie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="762f3-112">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="762f3-113">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="762f3-113">KeepAliveFailure</span></span>|<span data-ttu-id="762f3-114">Serwer zamknął połączenie zostało nawiązane przy użyciu zestawu nagłówków Keep-alive.</span><span class="sxs-lookup"><span data-stu-id="762f3-114">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="762f3-115">NameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="762f3-115">NameResolutionFailure</span></span>|<span data-ttu-id="762f3-116">Usługa nazw nie można rozpoznać nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="762f3-116">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="762f3-117">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="762f3-117">ProtocolError</span></span>|<span data-ttu-id="762f3-118">Odpowiedź odebraną z serwera zostało ukończone, ale wskazany błąd na poziomie protokołu.</span><span class="sxs-lookup"><span data-stu-id="762f3-118">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="762f3-119">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="762f3-119">ReceiveFailure</span></span>|<span data-ttu-id="762f3-120">Nie odebrano pełną odpowiedź z serwera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="762f3-120">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="762f3-121">RequestCanceled</span><span class="sxs-lookup"><span data-stu-id="762f3-121">RequestCanceled</span></span>|<span data-ttu-id="762f3-122">Żądanie zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="762f3-122">The request was canceled.</span></span>|  
|<span data-ttu-id="762f3-123">SecureChannelFailure</span><span class="sxs-lookup"><span data-stu-id="762f3-123">SecureChannelFailure</span></span>|<span data-ttu-id="762f3-124">Wystąpił błąd w linku bezpiecznego kanału.</span><span class="sxs-lookup"><span data-stu-id="762f3-124">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="762f3-125">SendFailure</span><span class="sxs-lookup"><span data-stu-id="762f3-125">SendFailure</span></span>|<span data-ttu-id="762f3-126">Nie można wysłać kompletne żądanie do serwera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="762f3-126">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="762f3-127">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="762f3-127">ServerProtocolViolation</span></span>|<span data-ttu-id="762f3-128">Odpowiedź serwera nie jest prawidłową odpowiedź HTTP.</span><span class="sxs-lookup"><span data-stu-id="762f3-128">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="762f3-129">Powodzenie</span><span class="sxs-lookup"><span data-stu-id="762f3-129">Success</span></span>|<span data-ttu-id="762f3-130">Napotkano błąd braku.</span><span class="sxs-lookup"><span data-stu-id="762f3-130">No error was encountered.</span></span>|  
|<span data-ttu-id="762f3-131">limit czasu</span><span class="sxs-lookup"><span data-stu-id="762f3-131">Timeout</span></span>|<span data-ttu-id="762f3-132">Nie otrzymano odpowiedzi zgodnie z limitem czasu, ustaw dla żądania.</span><span class="sxs-lookup"><span data-stu-id="762f3-132">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="762f3-133">TrustFailure</span><span class="sxs-lookup"><span data-stu-id="762f3-133">TrustFailure</span></span>|<span data-ttu-id="762f3-134">Nie można zweryfikować certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="762f3-134">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="762f3-135">MessageLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="762f3-135">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="762f3-136">Odebrano komunikat, który przekracza określony limit, podczas wysyłania żądania i odbierania odpowiedzi z serwera.</span><span class="sxs-lookup"><span data-stu-id="762f3-136">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="762f3-137">Oczekujące</span><span class="sxs-lookup"><span data-stu-id="762f3-137">Pending</span></span>|<span data-ttu-id="762f3-138">Wewnętrzne żądania asynchronicznego jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="762f3-138">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="762f3-139">PipelineFailure</span><span class="sxs-lookup"><span data-stu-id="762f3-139">PipelineFailure</span></span>|<span data-ttu-id="762f3-140">Ta wartość obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="762f3-140">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="762f3-141">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="762f3-141">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="762f3-142">Usługa rozpoznawania nazw nie można rozpoznać nazwy hosta serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="762f3-142">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="762f3-143">Nieznany błąd zostanie</span><span class="sxs-lookup"><span data-stu-id="762f3-143">UnknownError</span></span>|<span data-ttu-id="762f3-144">Wystąpił nieznany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="762f3-144">An exception of unknown type has occurred.</span></span>|  
  
 <span data-ttu-id="762f3-145">Gdy **stan** właściwość jest **WebExceptionStatus.ProtocolError**, **elementu WebResponse** zawierający odpowiedź z serwera jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="762f3-145">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="762f3-146">Można sprawdzić tej odpowiedzi, aby określić rzeczywiste źródło błędu protokołu.</span><span class="sxs-lookup"><span data-stu-id="762f3-146">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
 <span data-ttu-id="762f3-147">Poniższy przykład pokazuje, jak przechwytywać **WebException**.</span><span class="sxs-lookup"><span data-stu-id="762f3-147">The following example shows how to catch a **WebException**.</span></span>  
  
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
  
 <span data-ttu-id="762f3-148">Aplikacje, które używają <xref:System.Net.Sockets.Socket> throw klasy <xref:System.Net.Sockets.SocketException> Jeśli błędy występują w gnieździe Windows.</span><span class="sxs-lookup"><span data-stu-id="762f3-148">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="762f3-149"><xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, I <xref:System.Net.Sockets.UdpClient> klasy są tworzone w górnej części **gniazda** klasy i zgłosić **SocketExceptions** także.</span><span class="sxs-lookup"><span data-stu-id="762f3-149">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
 <span data-ttu-id="762f3-150">Gdy **SocketException** jest zgłaszany, **SocketException** klasy zestawy <xref:System.Net.Sockets.SocketException.ErrorCode%2A> właściwość ostatni błąd gniazda systemu operacyjnego, który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="762f3-150">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="762f3-151">Aby uzyskać więcej informacji o kodach błędów gniazda dokumentacji interfejsu API w wersji 2.0 Winsock błąd kodu w bibliotece MSDN.</span><span class="sxs-lookup"><span data-stu-id="762f3-151">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="762f3-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="762f3-152">See also</span></span>

- [<span data-ttu-id="762f3-153">Podstawowe założenia obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="762f3-153">Exception Handling Fundamentals</span></span>](../../../docs/standard/exceptions/exception-handling-fundamentals.md)
- [<span data-ttu-id="762f3-154">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="762f3-154">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
