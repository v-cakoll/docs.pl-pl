---
title: Tworzenie żądań asynchronicznych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, asynchronous access
- Networking
- asynchronous requests, Internet resources
- Network Resources
- WebRequest class, asynchronous access
ms.assetid: 735d3fce-f80c-437f-b02c-5c47f5739674
ms.openlocfilehash: 2bfb33944007f84992d95ebc35c04ab9b97b3a7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963979"
---
# <a name="making-asynchronous-requests"></a>Tworzenie żądań asynchronicznych
<xref:System.Net> Klasy używają standardowego asynchronicznego modelu programowania .NET Framework na potrzeby asynchronicznego dostępu do zasobów internetowych. Metody <xref:System.Net.WebRequest.BeginGetResponse%2A> <xref:System.Net.WebRequest.EndGetResponse%2A> i i kompletne żądania asynchroniczne dla zasobu internetowego. <xref:System.Net.WebRequest>  
  
> [!NOTE]
> Używanie wywołań synchronicznych w asynchronicznych metodach wywołania zwrotnego może skutkować poważnymi karami za wydajność. Żądania internetowe wysyłane z **żądaniem WebRequest** i jego elementy podrzędne muszą <xref:System.IO.Stream.BeginRead%2A?displayProperty=nameWithType> używać do odczytywania <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> strumienia zwróconego przez metodę.  
  
 Poniższy przykładowy kod demonstruje sposób używania wywołań asynchronicznych z klasą **WebRequest** . Przykładem jest program konsolowy, który pobiera identyfikator URI z wiersza polecenia, żąda zasobu pod identyfikatorem URI, a następnie drukuje dane do konsoli w miarę odbierania z Internetu.  
  
 Program definiuje dwie klasy do własnego użytku, klasy **RequestState** , która przekazuje dane w wywołaniach asynchronicznych, oraz klasę **ClientGetAsync** , która implementuje asynchroniczne żądanie do zasobu internetowego.  
  
 Klasa **RequestState** zachowuje stan żądania dla wywołań metod asynchronicznych, które obsługują żądanie. Zawiera WebRequest i <xref:System.IO.Stream> Instances, które zawierają bieżące żądanie do zasobu i strumień odebrany w odpowiedzi, bufor zawierający dane aktualnie odebrane z <xref:System.Text.StringBuilder> zasobu internetowego i zawierający Pełna odpowiedź. **RequestState** jest przenoszona jako <xref:System.AsyncCallback> parametr *stanu* , gdy metoda jest zarejestrowana w **WebRequest. BeginGetResponse**.  
  
 Klasa **ClientGetAsync** implementuje asynchroniczne żądanie do zasobu internetowego i zapisuje wyniki odpowiedzi w konsoli. Zawiera on metody i właściwości opisane na poniższej liście.  
  
- Właściwość zawiera wystąpienie <xref:System.Threading.ManualResetEvent> klasy, które sygnalizuje ukończenie żądania. `allDone`  
  
- `Main()` Metoda odczytuje wiersz polecenia i rozpoczyna żądanie dla określonego zasobu internetowego. Tworzy **żądanie WebRequest** `wreq` i **RequestState** `rs`, wywołuje **BeginGetResponse** , aby rozpocząć przetwarzanie żądania, a następnie wywołuje `allDone.WaitOne()`metodę, aby aplikacja nie wyjdzie do momentu wywołanie zwrotne zostało zakończone. Po odczytaniu odpowiedzi z zasobu internetowego program `Main()` zapisuje ją w konsoli programu, a aplikacja zostanie zakończona.  
  
- `showusage()` Metoda zapisuje przykładowy wiersz polecenia w konsoli programu. Jest wywoływana przez, `Main()` gdy w wierszu polecenia nie podano identyfikatora URI.  
  
- `RespCallBack()` Metoda implementuje asynchroniczne metody wywołania zwrotnego dla żądania internetowego. Tworzy ono wystąpienie **WebResponse** zawierające odpowiedź z zasobu internetowego, pobiera strumień odpowiedzi, a następnie zaczyna odczytywać dane ze strumienia asynchronicznie.  
  
- `ReadCallBack()` Metoda implementuje asynchroniczne metody wywołania zwrotnego do odczytu strumienia odpowiedzi. Przesyła dane otrzymane z zasobu internetowego do właściwości **ResponseData** wystąpienia **RequestState** , a następnie uruchamia kolejną asynchroniczną odczyt strumienia odpowiedzi, dopóki nie zostaną zwrócone żadne dalsze dane. Po odczytaniu wszystkich danych program `ReadCallBack()` zamknie strumień odpowiedzi i `allDone.Set()` wywołuje metodę w celu wskazania, że cała odpowiedź jest obecna w **ResponseData**.  
  
    > [!NOTE]
    > Należy pamiętać, że wszystkie strumienie sieciowe są zamknięte. Jeśli nie zamkniesz wszystkich żądań i strumieni odpowiedzi, aplikacja zostanie uruchomiona z serwerem i nie będzie mogła przetwarzać dodatkowych żądań.  
  
```csharp  
using System;  
using System.Net;  
using System.Threading;  
using System.Text;  
using System.IO;  
  
// The RequestState class passes data across async calls.  
public class RequestState  
{  
   const int BufferSize = 1024;  
   public StringBuilder RequestData;  
   public byte[] BufferRead;  
   public WebRequest Request;  
   public Stream ResponseStream;  
   // Create Decoder for appropriate enconding type.  
   public Decoder StreamDecode = Encoding.UTF8.GetDecoder();  
  
   public RequestState()  
   {  
      BufferRead = new byte[BufferSize];  
      RequestData = new StringBuilder(String.Empty);  
      Request = null;  
      ResponseStream = null;  
   }       
}  
  
// ClientGetAsync issues the async request.  
class ClientGetAsync   
{  
   public static ManualResetEvent allDone = new ManualResetEvent(false);  
   const int BUFFER_SIZE = 1024;  
  
   public static void Main(string[] args)   
   {  
      if (args.Length < 1)   
      {  
         showusage();  
         return;  
      }  
  
      // Get the URI from the command line.  
      Uri httpSite = new Uri(args[0]);  
  
      // Create the request object.  
      WebRequest wreq = WebRequest.Create(httpSite);  
  
      // Create the state object.  
      RequestState rs = new RequestState();  
  
      // Put the request into the state object so it can be passed around.  
      rs.Request = wreq;  
  
      // Issue the async request.  
      IAsyncResult r = (IAsyncResult) wreq.BeginGetResponse(  
         new AsyncCallback(RespCallback), rs);  
  
      // Wait until the ManualResetEvent is set so that the application   
      // does not exit until after the callback is called.  
      allDone.WaitOne();  
  
      Console.WriteLine(rs.RequestData.ToString());  
   }  
  
   public static void showusage() {  
      Console.WriteLine("Attempts to GET a URL");  
      Console.WriteLine("\r\nUsage:");  
      Console.WriteLine("   ClientGetAsync URL");  
      Console.WriteLine("   Example:");  
      Console.WriteLine("      ClientGetAsync http://www.contoso.com/");  
   }  
  
   private static void RespCallback(IAsyncResult ar)  
   {  
      // Get the RequestState object from the async result.  
      RequestState rs = (RequestState) ar.AsyncState;  
  
      // Get the WebRequest from RequestState.  
      WebRequest req = rs.Request;  
  
      // Call EndGetResponse, which produces the WebResponse object  
      //  that came from the request issued above.  
      WebResponse resp = req.EndGetResponse(ar);           
  
      //  Start reading data from the response stream.  
      Stream ResponseStream = resp.GetResponseStream();  
  
      // Store the response stream in RequestState to read   
      // the stream asynchronously.  
      rs.ResponseStream = ResponseStream;  
  
      //  Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead  
      IAsyncResult iarRead = ResponseStream.BeginRead(rs.BufferRead, 0,   
         BUFFER_SIZE, new AsyncCallback(ReadCallBack), rs);   
   }  
  
   private static void ReadCallBack(IAsyncResult asyncResult)  
   {  
      // Get the RequestState object from AsyncResult.  
      RequestState rs = (RequestState)asyncResult.AsyncState;  
  
      // Retrieve the ResponseStream that was set in RespCallback.   
      Stream responseStream = rs.ResponseStream;  
  
      // Read rs.BufferRead to verify that it contains data.   
      int read = responseStream.EndRead( asyncResult );  
      if (read > 0)  
      {  
         // Prepare a Char array buffer for converting to Unicode.  
         Char[] charBuffer = new Char[BUFFER_SIZE];  
  
         // Convert byte stream to Char array and then to String.  
         // len contains the number of characters converted to Unicode.  
      int len =   
         rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0);  
  
         String str = new String(charBuffer, 0, len);  
  
         // Append the recently read data to the RequestData stringbuilder  
         // object contained in RequestState.  
         rs.RequestData.Append(  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read));           
  
         // Continue reading data until   
         // responseStream.EndRead returns –1.  
         IAsyncResult ar = responseStream.BeginRead(   
            rs.BufferRead, 0, BUFFER_SIZE,   
            new AsyncCallback(ReadCallBack), rs);  
      }  
      else  
      {  
         if(rs.RequestData.Length>0)  
         {  
            //  Display data to the console.  
            string strContent;                    
            strContent = rs.RequestData.ToString();  
         }  
         // Close down the response stream.  
         responseStream.Close();           
         // Set the ManualResetEvent so the main thread can exit.  
         allDone.Set();                             
      }  
      return;  
   }      
}  
```  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Threading  
Imports System.Text  
Imports System.IO  
  
' The RequestState class passes data across async calls.  
Public Class RequestState  
  
      Public RequestData As New StringBuilder("")  
      Public BufferRead(1024) As Byte  
      Public Request As HttpWebRequest  
      Public ResponseStream As Stream  
      ' Create Decoder for appropriate encoding type.  
      Public StreamDecode As Decoder = Encoding.UTF8.GetDecoder()  
  
      Public Sub New  
         Request = Nothing  
         ResponseStream = Nothing  
      End Sub  
End Class  
  
' ClientGetAsync issues the async request.  
Class ClientGetAsync  
   Shared allDone As New ManualResetEvent(False)  
      Const BUFFER_SIZE As Integer = 1024  
  
    Shared Sub Main()  
        Dim Args As String() = Environment.GetCommandLineArgs()  
  
        If Args.Length < 2 Then  
            ShowUsage()  
            Return  
        End If  
  
      ' Get the URI from the command line.  
        Dim HttpSite As Uri = New Uri(Args(1))  
  
      ' Create the request object.  
        Dim wreq As HttpWebRequest = _  
           CType(WebRequest.Create(HttpSite), HttpWebRequest)  
  
      ' Create the state object.  
      Dim rs As RequestState = New RequestState()  
  
      ' Put the request into the state so it can be passed around.  
      rs.Request = wreq  
  
      ' Issue the async request.  
        Dim r As IAsyncResult = _  
           CType(wreq.BeginGetResponse( _  
           New AsyncCallback(AddressOf RespCallback), rs), IAsyncResult)  
  
      ' Wait until the ManualResetEvent is set so that the application  
      ' does not exit until after the callback is called.  
        allDone.WaitOne()  
    End Sub  
  
    Shared Sub ShowUsage()  
        Console.WriteLine("Attempts to GET a URI")  
        Console.WriteLine()  
        Console.WriteLine("Usage:")  
        Console.WriteLine("ClientGetAsync URI")  
        Console.WriteLine("Examples:")  
        Console.WriteLine("ClientGetAsync http://www.contoso.com/")  
    End Sub  
  
    Shared Sub RespCallback(ar As IAsyncResult)  
       ' Get the RequestState object from the async result.  
       Dim rs As RequestState = CType(ar.AsyncState, RequestState)  
  
       ' Get the HttpWebRequest from RequestState.  
       Dim req As HttpWebRequest= rs.Request  
  
       ' Call EndGetResponse, which returns the HttpWebResponse object  
       ' that came from the request issued above.  
       Dim resp As HttpWebResponse = _  
           CType(req.EndGetResponse(ar), HttpWebResponse)  
  
       ' Start reading data from the response stream.  
       Dim ResponseStream As Stream = resp.GetResponseStream()  
  
       ' Store the reponse stream in RequestState to read  
       ' the stream asynchronously.  
       rs.ResponseStream = ResponseStream  
  
       ' Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead.  
       Dim iarRead As IAsyncResult = _  
          ResponseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
          New AsyncCallback(AddressOf ReadCallBack), rs)  
    End Sub  
  
   Shared Sub ReadCallBack(asyncResult As IAsyncResult)  
      ' Get the RequestState object from the AsyncResult.  
      Dim rs As RequestState = CType(asyncResult.AsyncState, RequestState)  
  
      ' Retrieve the ResponseStream that was set in RespCallback.  
      Dim responseStream As Stream = rs.ResponseStream  
  
      ' Read rs.BufferRead to verify that it contains data.  
      Dim read As Integer = responseStream.EndRead( asyncResult )  
      If read > 0 Then  
         ' Prepare a Char array buffer for converting to Unicode.  
         Dim charBuffer(1024) As Char  
  
         ' Convert byte stream to Char array and then String.  
         ' len contains the number of characters converted to Unicode.  
         Dim len As Integer = _  
           rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0)  
         Dim str As String = new String(charBuffer, 0, len)      
  
         ' Append the recently read data to the RequestData stringbuilder   
         ' object contained in RequestState.  
         rs.RequestData.Append( _  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read))  
  
         ' Continue reading data until responseStream.EndRead  
         ' returns –1.  
         Dim ar As IAsyncResult = _  
            responseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
            New AsyncCallback(AddressOf ReadCallBack), rs)  
      Else  
          If rs.RequestData.Length > 1 Then  
            ' Display data to the console.  
            Dim strContent As String  
            strContent = rs.RequestData.ToString()  
            Console.WriteLine(strContent)  
         End If  
  
         ' Close down the response stream.  
         responseStream.Close()  
  
         ' Set the ManualResetEvent so the main thread can exit.  
         allDone.Set()  
      End If  
  
      Return  
   End Sub  
End Class  
```  
  
## <a name="see-also"></a>Zobacz także

- [Żądanie danych](../../../docs/framework/network-programming/requesting-data.md)
