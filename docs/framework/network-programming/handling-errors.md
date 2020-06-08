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
# <a name="handling-errors"></a>Obsługa błędów

<xref:System.Net.WebRequest>Klasy i <xref:System.Net.WebResponse> generują zarówno wyjątki systemowe (takie jak <xref:System.ArgumentException> ), jak i specyficzne dla sieci Web wyjątki (które są <xref:System.Net.WebException> generowane przez <xref:System.Net.WebRequest.GetResponse%2A> metodę).  
  
Każdy element **WebException** zawiera <xref:System.Net.WebException.Status%2A> Właściwość, która zawiera wartość z <xref:System.Net.WebExceptionStatus> wyliczenia. Można sprawdzić Właściwość **status** , aby określić błąd, który wystąpił, i podjąć odpowiednie kroki, aby rozwiązać ten problem.  
  
W poniższej tabeli opisano możliwe wartości właściwości **stan** .  
  
|Stan|Opis|  
|------------|-----------------|  
|ConnectFailure|Nie można skontaktować się z usługą zdalną na poziomie transportu.|  
|ConnectionClosed|Połączenie zostało przedwcześnie zakończone.|  
|KeepAliveFailure|Serwer zamknął połączenie wykonane z zestawem nagłówkowym Keep-Alive.|  
|NameResolutionFailure|Usługa nazw nie może rozpoznać nazwy hosta.|  
|ProtocolError|Odpowiedź odebrana z serwera została ukończona, ale wykazała błąd na poziomie protokołu.|  
|ReceiveFailure|Nie odebrano kompletnej odpowiedzi z serwera zdalnego.|  
|RequestCanceled|Żądanie zostało anulowane.|  
|SecureChannelFailure|Wystąpił błąd w łącznym kanale bezpiecznego kanału.|  
|SendFailure|Nie można wysłać kompletnego żądania do serwera zdalnego.|  
|ServerProtocolViolation|Odpowiedź serwera nie jest prawidłową odpowiedzią HTTP.|  
|Powodzenie|Nie wystąpił błąd.|  
|Limit czasu|Nie odebrano odpowiedzi w określonym limicie czasu dla żądania.|  
|TrustFailure|Nie można zweryfikować certyfikatu serwera.|  
|MessageLengthLimitExceeded|Odebrano komunikat, który przekroczył określony limit podczas wysyłania żądania lub odebrania odpowiedzi z serwera.|  
|Oczekiwanie|Wewnętrzne asynchroniczne żądanie jest w stanie oczekiwania.|  
|PipelineFailure|Ta wartość obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.|  
|ProxyNameResolutionFailure|Usługa rozpoznawania nazw nie może rozpoznać nazwy hosta serwera proxy.|  
|UnknownError|Wystąpił wyjątek nieznanego typu.|  
  
Gdy właściwość **status** ma wartość **WebExceptionStatus. ProtocolError**, dostępna jest **WebResponse** , która zawiera odpowiedź z serwera. Tę odpowiedź można sprawdzić w celu ustalenia rzeczywistego źródła błędu protokołu.  
  
Poniższy przykład przedstawia sposób przechwytywania **wyjątku WebException**.  
  
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
  
Aplikacje korzystające z <xref:System.Net.Sockets.Socket> klasy throw w <xref:System.Net.Sockets.SocketException> przypadku wystąpienia błędów w gnieździe Windows. <xref:System.Net.Sockets.TcpClient>Klasy, <xref:System.Net.Sockets.TcpListener> , i <xref:System.Net.Sockets.UdpClient> są zbudowane na podstawie klasy **Socket** i generują **SocketExceptions** .  
  
Gdy zostanie zgłoszony obiekt **SocketException** , Klasa **SocketException** ustawia <xref:System.Net.Sockets.SocketException.ErrorCode%2A> Właściwość na ostatni błąd gniazda systemu operacyjnego, który wystąpił. Aby uzyskać więcej informacji na temat kodów błędów gniazda, zobacz dokumentację kodu błędu interfejsu API Winsock 2,0 w witrynie MSDN.  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa i zgłaszanie wyjątków w programie .NET](../../standard/exceptions/index.md)
- [Żądanie danych](requesting-data.md)
