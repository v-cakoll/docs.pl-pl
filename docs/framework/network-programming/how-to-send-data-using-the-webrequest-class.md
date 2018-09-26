---
title: 'Instrukcje: przesyłanie danych przy użyciu klasy WebRequest'
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
ms.openlocfilehash: f62775a41f70e4dd96c749acd99bf8b850d96407
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084959"
---
# <a name="how-to-send-data-using-the-webrequest-class"></a>Instrukcje: przesyłanie danych przy użyciu klasy WebRequest
Poniższa procedura opisuje kroki używane do przesyłania danych do serwera. Ta procedura jest często używane dane do strony sieci Web.  
  
### <a name="to-send-data-to-a-host-server"></a>Do przesyłania danych do serwera hosta  
  
1.  Tworzenie <xref:System.Net.WebRequest> wystąpienia, wywołując <xref:System.Net.WebRequest.Create%2A> za pomocą identyfikatora URI zasobu, który akceptuje dane, na przykład, skryptu lub strony ASP.NET.  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  Program .NET Framework zawiera klasy pochodne klasy specyficzne dla protokołu **WebRequest** i **elementu WebResponse** identyfikatory URI, które zaczynają się od "http:", "https:", "ftp:", i "plik:". Aby uzyskać dostęp do zasobów przy użyciu innych protokołów, musi implementować klasy specyficzne dla protokołu, które wynikają z **WebRequest** i **elementu WebResponse**. Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .  
  
2.  Ustaw wszystkie wartości właściwości, które są potrzebne w **WebRequest**. Na przykład, aby włączyć uwierzytelnianie, należy ustawić **poświadczenia** właściwości wystąpienia <xref:System.Net.NetworkCredential> klasy.  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     W większości przypadków **WebRequest** samego wystąpienia jest wystarczająca do przesyłania danych. Jednak jeśli potrzebujesz ustawić właściwości specyficzne dla protokołu, należy rzutować **WebRequest** typowi specyficzne dla protokołu. Na przykład, aby właściwości dostępu właściwe dla protokołu HTTP <xref:System.Net.HttpWebRequest>, rzutowania **WebRequest** do **HttpWebRequest** odwołania. Poniższy przykład kodu pokazuje, jak ustawić specyficzne dla protokołu HTTP <xref:System.Net.HttpWebRequest.UserAgent%2A> właściwości.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Określ metodę protokołu, który zezwala na dane mają być wysyłane z żądaniem, takich jak HTTP **WPIS** metody.  
  
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
  
5.  Ustaw **ContentType** właściwość do odpowiedniej wartości.  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  Strumień, że przechowuje dane żądania przez wywołanie metody GET <xref:System.Net.WebRequest.GetRequestStream%2A> metody.  
  
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
  
8.  Zamknij strumień żądań przez wywołanie metody **Stream.Close** metody.  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A>. Ta metoda zwraca obiekt zawierający odpowiedź serwera. Zwrócony <xref:System.Net.WebResponse> typ obiektu jest określana przez schemat identyfikatora URI żądania.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  Po zakończeniu <xref:System.Net.WebResponse> obiektu, należy go zamknąć, wywołując <xref:System.Net.WebResponse.Close%2A> metody. Alternatywnie w strumieniu odpowiedzi zostały uzyskane z obiekt odpowiedzi, aby zamknąć strumień przez wywołanie metody <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody. Jeśli nie zamkniesz odpowiedzi lub strumienia, aplikację można zabraknie połączenia z serwerem i stają się nie może przetworzyć żądań dodatkowych.  
  
10. Można uzyskać dostęp do właściwości **elementu WebResponse** lub Zastosuj rzutowanie **elementu WebResponse** do wystąpienia oparte na protokole można odczytać właściwości specyficzne dla protokołu. Na przykład, aby właściwości dostępu właściwe dla protokołu HTTP <xref:System.Net.HttpWebResponse>, rzutowania **elementu WebResponse** do **HttpWebResponse** odwołania.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. Aby uzyskać strumienia zawierające dane odpowiedzi wysyłane przez serwer, należy wywołać <xref:System.Net.WebResponse.GetResponseStream%2A> metody **elementu WebResponse**.  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. Po odczytaniu danych z odpowiedzi, należy to zamknąć przy użyciu strumienia odpowiedzi **Stream.Close** metody lub Zamknij przy użyciu odpowiedzi **WebResponse.Close** metody. Nie jest konieczne do wywołania **Zamknij** metody w strumieniu odpowiedzi i **elementu WebResponse**, ale spowoduje tak nie jest szkodliwe.  
  
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
