---
title: 'Porady: dane przy użyciu klasy WebRequest żądania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e02ad4772d3ba84a2735a2e146a9979862d75989
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-request-data-using-the-webrequest-class"></a>Porady: dane przy użyciu klasy WebRequest żądania
W poniższej procedurze opisano kroki używane do żądania zasobów z serwera, na przykład, strony sieci Web lub pliku. Zasób musi być identyfikowany przez identyfikator URI.  
  
### <a name="to-request-data-from-a-host-server"></a>Żądanie danych z serwera hosta  
  
1.  Utwórz <xref:System.Net.WebRequest> wystąpienia przez wywołanie metody <xref:System.Net.WebRequest.Create%2A> o identyfikatorze URI zasobu.  
  
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
  
     W większości przypadków **WebRequest** klasy są wystarczające, aby odbierać dane. Jednak jeśli należy ustawić właściwości specyficzne dla protokołu, należy rzutować **WebRequest** typowi specyficzne dla protokołu. Na przykład do właściwości dostępu specyficzne dla protokołu HTTP <xref:System.Net.HttpWebRequest>, rzutowanie **WebRequest** do **HttpWebRequest** odwołania. W poniższym przykładzie przedstawiono sposób ustawiania specyficzne dla protokołu HTTP <xref:System.Net.HttpWebRequest.UserAgent%2A> właściwości.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Aby wysłać żądania do serwera, należy wywołać <xref:System.Net.HttpWebRequest.GetResponse%2A>. Rzeczywisty typ zwróconego **WebResponse** obiektu jest określane przez schemat żądanego identyfikatora URI.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  Po zakończeniu <xref:System.Net.WebResponse> obiektu, należy go zamknąć, wywołując <xref:System.Net.WebResponse.Close%2A> metody. Alternatywnie, jeśli z obiektu odpowiedzi stają się coraz w strumieniu odpowiedzi, można zamknąć strumienia przez wywołanie metody <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody. Jeśli nie zamkniesz odpowiedzi lub strumienia, aplikacja może zabraknie połączenia z serwerem i stają się nie może przetworzyć żądania dodatkowe.  
  
4.  Można uzyskać dostęp do właściwości **WebResponse** lub Zastosuj rzutowanie **WebResponse** do wystąpienia Protokołem do odczytu właściwości specyficzne dla protokołu. Na przykład do właściwości dostępu specyficzne dla protokołu HTTP <xref:System.Net.HttpWebResponse>, rzutowanie **WebResponse** do **HttpWebResponse** odwołania. Poniższy przykład kodu pokazuje, jak można wyświetlić informacje o stanie wysyłane z odpowiedzią.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  Aby uzyskać strumienia zawierające dane odpowiedzi wysyłane przez serwer, należy użyć <xref:System.Net.HttpWebResponse.GetResponseStream%2A> metody **WebResponse**.  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  Po odczytaniu danych z odpowiedzi, należy albo zamknąć przy użyciu strumienia odpowiedzi **Stream.Close** metody lub zamknij odpowiedzi, za pomocą **WebResponse.Close** metody. Nie jest konieczne do wywołania **Zamknij** metody w strumieniu odpowiedzi i **WebResponse**, ale spowoduje to nie jest szkodliwe. **WebResponse.Close** wywołania **Stream.Close** podczas zamykania odpowiedzi.  
  
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
    public class WebRequestGetExample  
    {  
        public static void Main()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create(  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader(dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd();  
            // Display the content.  
            Console.WriteLine(responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close();  
            response.Close();  
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
    Public Class WebRequestGetExample  
  
        Public Shared Sub Main()  
            ' Create a request for the URL.   
            Dim request As WebRequest = _  
              WebRequest.Create("http://www.contoso.com/default.html")  
            ' If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            Dim dataStream As Stream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams and the response.  
            reader.Close()  
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
 [Instrukcje: przesyłanie danych przy użyciu klasy WebRequest](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
