---
title: 'Porady: wysyłanie danych przy użyciu klasy WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a40ab63e0fbac4227d74999c8c83f02e3c9e4b4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394660"
---
# <a name="how-to-send-data-using-the-webrequest-class"></a>Porady: wysyłanie danych przy użyciu klasy WebRequest
W poniższej procedurze opisano kroki używane do wysyłania danych do serwera. Ta procedura jest najczęściej używany do publikowania danych do strony sieci Web.  
  
### <a name="to-send-data-to-a-host-server"></a>Do przesyłania danych do serwera hosta  
  
1.  Utwórz <xref:System.Net.WebRequest> wystąpienia przez wywołanie metody <xref:System.Net.WebRequest.Create%2A> o identyfikatorze URI zasobu, który akceptuje dane, na przykład, skrypt lub strony ASP.NET.  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  Platforma .NET Framework zapewnia oparte na protokole klasy pochodzące od **WebRequest** i **WebResponse** identyfikatory URI, które rozpoczynają się od "http:", "https:", "ftp:", i "pliku:". Aby uzyskać dostęp do zasobów przy użyciu innych protokołów, musi implementować klasy specyficzne dla protokołu, pochodzących z **WebRequest** i **WebResponse**. Aby uzyskać więcej informacji, zobacz [programowania podłączany protokołów](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .  
  
2.  Ustawianie wartości właściwości wymaganych w **WebRequest**. Na przykład, aby włączyć uwierzytelnianie, należy ustawić **poświadczenia** dla właściwości wystąpienia <xref:System.Net.NetworkCredential> klasy.  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     W większości przypadków **WebRequest** wystąpienie jest wystarczająca do przesyłania danych. Jednak jeśli należy ustawić właściwości specyficzne dla protokołu, należy rzutować **WebRequest** typowi specyficzne dla protokołu. Na przykład do właściwości dostępu specyficzne dla protokołu HTTP <xref:System.Net.HttpWebRequest>, rzutowanie **WebRequest** do **HttpWebRequest** odwołania. W poniższym przykładzie przedstawiono sposób ustawiania specyficzne dla protokołu HTTP <xref:System.Net.HttpWebRequest.UserAgent%2A> właściwości.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Określ metodę protokołu, która pozwala na dane mają być wysyłane z żądaniem, takich jak HTTP **POST** metody.  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  Ustaw **ContentLength** właściwości.  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  Ustaw **ContentType** właściwości odpowiednią wartość.  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  Strumień, że blokad dane żądania przez wywołanie metody GET <xref:System.Net.WebRequest.GetRequestStream%2A> metody.  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  Zapisane dane <xref:System.IO.Stream> obiektu zwróconego przez tę metodę.  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  Zamknij strumienia żądania przez wywołanie metody **Stream.Close** metody.  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A>. Ta metoda zwraca obiekt zawierający odpowiedzi serwera. Zwrócona <xref:System.Net.WebResponse> typ obiektu jest określany przez schemat identyfikatora URI żądania.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  Po zakończeniu <xref:System.Net.WebResponse> obiektu, należy go zamknąć, wywołując <xref:System.Net.WebResponse.Close%2A> metody. Alternatywnie, jeśli z obiektu odpowiedzi stają się coraz w strumieniu odpowiedzi, można zamknąć strumienia przez wywołanie metody <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody. Jeśli nie zamkniesz odpowiedzi lub strumienia, aplikacja może zabraknie połączenia z serwerem i stają się nie może przetworzyć żądania dodatkowe.  
  
10. Można uzyskać dostęp do właściwości **WebResponse** lub Zastosuj rzutowanie **WebResponse** do wystąpienia Protokołem do odczytu właściwości specyficzne dla protokołu. Na przykład do właściwości dostępu specyficzne dla protokołu HTTP <xref:System.Net.HttpWebResponse>, rzutowanie **WebResponse** do **HttpWebResponse** odwołania.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. Aby uzyskać strumienia zawierające dane odpowiedzi wysyłane przez serwer, należy wywołać <xref:System.Net.WebResponse.GetResponseStream%2A> metody **WebResponse**.  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. Po odczytaniu danych z odpowiedzi, należy albo zamknąć przy użyciu strumienia odpowiedzi **Stream.Close** metody lub zamknij odpowiedzi, za pomocą **WebResponse.Close** metody. Nie jest konieczne do wywołania **Zamknij** metody w strumieniu odpowiedzi i **WebResponse**, ale spowoduje to nie jest szkodliwe.  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>Przykład  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestPostExample  
    {  
        public static void Main ()  
        {  
            // Create a request using a URL that can receive a post.   
            WebRequest request = WebRequest.Create ("http://www.contoso.com/PostAccepter.aspx ");  
            // Set the Method property of the request to POST.  
            request.Method = "POST";  
            // Create POST data and convert it to a byte array.  
            string postData = "This is a test that posts this string to a Web server.";  
            byte[] byteArray = Encoding.UTF8.GetBytes (postData);  
            // Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded";  
            // Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length;  
            // Get the request stream.  
            Stream dataStream = request.GetRequestStream ();  
            // Write the data to the request stream.  
            dataStream.Write (byteArray, 0, byteArray.Length);  
            // Close the Stream object.  
            dataStream.Close ();  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams.  
            reader.Close ();  
            dataStream.Close ();  
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
    Public Class WebRequestPostExample  
  
        Public Shared Sub Main()  
            ' Create a request using a URL that can receive a post.   
            Dim request As WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx ")  
            ' Set the Method property of the request to POST.  
            request.Method = "POST"  
            ' Create POST data and convert it to a byte array.  
            Dim postData As String = "This is a test that posts this string to a Web server."  
            Dim byteArray As Byte() = Encoding.UTF8.GetBytes(postData)  
            ' Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded"  
            ' Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length  
            ' Get the request stream.  
            Dim dataStream As Stream = request.GetRequestStream()  
            ' Write the data to the request stream.  
            dataStream.Write(byteArray, 0, byteArray.Length)  
            ' Close the Stream object.  
            dataStream.Close()  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams.  
            reader.Close()  
            dataStream.Close()  
            response.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie żądań internetowych](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [Stosowanie strumieni w sieci](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Dostęp do Internetu za pośrednictwem serwera proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Żądanie danych](../../../docs/framework/network-programming/requesting-data.md)  
 [Instrukcje: żądanie danych przy użyciu klasy WebRequest](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
