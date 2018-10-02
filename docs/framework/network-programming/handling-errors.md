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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 776e0a728b56aa2acfb7a033c2a7244b2cc824f9
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863042"
---
# <a name="handling-errors"></a>Obsługa błędów
<xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy zgłaszają wyjątki zarówno system (takie jak <xref:System.ArgumentException>) i wyjątków specyficzne dla sieci Web (służą do <xref:System.Net.WebException> zgłoszony przez <xref:System.Net.WebRequest.GetResponse%2A> metody).  
  
 Każdy **WebException** obejmuje <xref:System.Net.WebException.Status%2A> właściwość, która zawiera wartość z zakresu od <xref:System.Net.WebExceptionStatus> wyliczenia. Można sprawdzić **stan** właściwości, aby ustalić błędu, który wystąpił i wykonaj odpowiednie czynności, aby rozwiązać problem.  
  
 W poniższej tabeli opisano możliwe wartości **stan** właściwości.  
  
|Stan|Opis|  
|------------|-----------------|  
|ConnectFailure|Nie można skontaktować się z usługi zdalnej na poziomie transportu.|  
|ConnectionClosed|Połączenie zostało przedwcześnie zamknięte.|  
|KeepAliveFailure|Serwer zamknął połączenie zostało nawiązane przy użyciu zestawu nagłówków Keep-alive.|  
|NameResolutionFailure|Usługa nazw nie można rozpoznać nazwy hosta.|  
|ProtocolError|Odpowiedź odebraną z serwera zostało ukończone, ale wskazany błąd na poziomie protokołu.|  
|ReceiveFailure|Nie odebrano pełną odpowiedź z serwera zdalnego.|  
|RequestCanceled|Żądanie zostało anulowane.|  
|SecureChannelFailure|Wystąpił błąd w linku bezpiecznego kanału.|  
|SendFailure|Nie można wysłać kompletne żądanie do serwera zdalnego.|  
|ServerProtocolViolation|Odpowiedź serwera nie jest prawidłową odpowiedź HTTP.|  
|Powodzenie|Napotkano błąd braku.|  
|limit czasu|Nie otrzymano odpowiedzi zgodnie z limitem czasu, ustaw dla żądania.|  
|TrustFailure|Nie można zweryfikować certyfikatu serwera.|  
|MessageLengthLimitExceeded|Odebrano komunikat, który przekracza określony limit, podczas wysyłania żądania i odbierania odpowiedzi z serwera.|  
|Oczekujące|Wewnętrzne żądania asynchronicznego jest w stanie oczekiwania.|  
|PipelineFailure|Ta wartość obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.|  
|ProxyNameResolutionFailure|Usługa rozpoznawania nazw nie można rozpoznać nazwy hosta serwera proxy.|  
|Nieznany błąd zostanie|Wystąpił nieznany wyjątek.|  
  
 Gdy **stan** właściwość jest **WebExceptionStatus.ProtocolError**, **elementu WebResponse** zawierający odpowiedź z serwera jest dostępna. Można sprawdzić tej odpowiedzi, aby określić rzeczywiste źródło błędu protokołu.  
  
 Poniższy przykład pokazuje, jak przechwytywać **WebException**.  
  
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
  
 Aplikacje, które używają <xref:System.Net.Sockets.Socket> throw klasy <xref:System.Net.Sockets.SocketException> Jeśli błędy występują w gnieździe Windows. <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, I <xref:System.Net.Sockets.UdpClient> klasy są tworzone w górnej części **gniazda** klasy i zgłosić **SocketExceptions** także.  
  
 Gdy **SocketException** jest zgłaszany, **SocketException** klasy zestawy <xref:System.Net.Sockets.SocketException.ErrorCode%2A> właściwość ostatni błąd gniazda systemu operacyjnego, który wystąpił. Aby uzyskać więcej informacji o kodach błędów gniazda dokumentacji interfejsu API w wersji 2.0 Winsock błąd kodu w bibliotece MSDN.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe założenia obsługi wyjątków](../../../docs/standard/exceptions/exception-handling-fundamentals.md)  
 [Żądanie danych](../../../docs/framework/network-programming/requesting-data.md)
