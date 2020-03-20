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
# <a name="handling-errors"></a>Obsługa błędów

Klasy <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> i zgłaszać zarówno wyjątki <xref:System.ArgumentException>systemowe (takie jak ) <xref:System.Net.WebException> i <xref:System.Net.WebRequest.GetResponse%2A> wyjątki specyficzne dla sieci Web (które są generowane przez metodę).  
  
Każdy **WebException** <xref:System.Net.WebException.Status%2A> zawiera właściwość, która <xref:System.Net.WebExceptionStatus> zawiera wartość z wyliczenia. Można zbadać **Status** właściwości, aby określić błąd, który wystąpił i podjąć odpowiednie kroki, aby rozwiązać błąd.  
  
W poniższej tabeli opisano możliwe wartości właściwości **Status.**  
  
|Stan|Opis|  
|------------|-----------------|  
|ConnectFailure (Połączenie)|Nie można skontaktować się z usługą zdalną na poziomie transportu.|  
|ConnectionClosed (Zamknięte połączenie)|Połączenie zostało zamknięte przedwcześnie.|  
|KeepAliveWłasna|Serwer zamknął połączenie nawiązanym z zestawem nagłówków Keep-alive.|  
|NazwaResolutionFailure|Usługa nazw nie może rozpoznać nazwy hosta.|  
|ProtokółError|Odpowiedź otrzymana z serwera została ukończona, ale wskazywała błąd na poziomie protokołu.|  
|ReceiveFailure (Nieujmowie)|Pełna odpowiedź nie została odebrana z serwera zdalnego.|  
|RequestCanceled (Wyliczył)|Żądanie zostało anulowane.|  
|SecureChannelWładnia|Wystąpił błąd w łączu bezpiecznego kanału.|  
|SendFailure (Niebezpieczeństwo wyślij)|Nie można wysłać kompletnego żądania do serwera zdalnego.|  
|ServerProtocolViolation (Proces serweraProtocolViolation)|Odpowiedź serwera nie była prawidłową odpowiedzią HTTP.|  
|Powodzenie|Nie wystąpił żaden błąd.|  
|Limit czasu|W terminie wyznaczonym dla wniosku nie otrzymano odpowiedzi.|  
|ZaufanieWłasność|Nie można zweryfikować certyfikatu serwera.|  
|WiadomośćLengthLimitExceeded|Odebrano wiadomość, która przekroczyła określony limit podczas wysyłania żądania lub odbierania odpowiedzi z serwera.|  
|Oczekujące|Oczekuje na wewnętrzne żądanie asynchroniczne.|  
|Awaria rurociągu|Ta wartość obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.|  
|ProxyNameResolutionFailure|Usługa rozpoznawania nazw nie może rozpoznać nazwy hosta serwera proxy.|  
|NieznanyError|Wystąpił wyjątek nieznanego typu.|  
  
Gdy **właściwość Status** jest **WebExceptionStatus.ProtocolError**, **WebResponse,** który zawiera odpowiedź z serwera jest dostępna. Można sprawdzić tę odpowiedź, aby określić rzeczywiste źródło błędu protokołu.  
  
W poniższym przykładzie pokazano, jak złapać **WebException**.  
  
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
  
Aplikacje, <xref:System.Net.Sockets.Socket> które <xref:System.Net.Sockets.SocketException> używają rzutu klasy, gdy wystąpią błędy w gnieździe systemu Windows. <xref:System.Net.Sockets.TcpListener> <xref:System.Net.Sockets.UdpClient> , <xref:System.Net.Sockets.TcpClient>i klasy są zbudowane na górze **Socket** klasy i rzucać **SocketExceptions,** jak również.  
  
Po uruchomieniu **SocketException,** **SocketException** klasa <xref:System.Net.Sockets.SocketException.ErrorCode%2A> ustawia właściwość do ostatniego błędu gniazda systemu operacyjnego, który wystąpił. Aby uzyskać więcej informacji na temat kodów błędów gniazda, zobacz dokumentację kodu błędu interfejsu API Winsock 2.0 w sieci MSDN.  
  
## <a name="see-also"></a>Zobacz też

- [Obsługa i zgłaszanie wyjątków w .NET](../../standard/exceptions/index.md)
- [Żądanie danych](requesting-data.md)
