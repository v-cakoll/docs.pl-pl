---
title: 'Instrukcje: Wyślij dane przy użyciu klasy WebRequest'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 456dbdab3070e88fe0bc6572c998ce54e3c19c00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166957"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>Instrukcje: Wyślij dane przy użyciu klasy WebRequest
Poniższa procedura opisuje kroki, aby wysłać dane do serwera. Ta procedura jest często używane dane do strony sieci Web. 
  
## <a name="to-send-data-to-a-host-server"></a>Do przesyłania danych do serwera hosta  
  
1.  Tworzenie <xref:System.Net.WebRequest> wystąpienia, wywołując <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> za pomocą identyfikatora URI zasobu, takiego jak skrypt lub strony ASP.NET, który akceptuje dane. Na przykład: 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")  
    ```  
  
    > [!NOTE]
    > Program .NET Framework zawiera klasy pochodne klasy specyficzne dla protokołu <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klas pochodnych identyfikatorów URI, które zaczynają się od *http:*, *https:*, *ftp:* , a *pliku:*.
    Jeśli musisz set lub odczytu właściwości specyficzne dla protokołu, należy rzutować swoje <xref:System.Net.WebRequest> lub <xref:System.Net.WebResponse> obiektu z typem obiektów specyficznych dla protokołu. Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](programming-pluggable-protocols.md). 
  
2.  Ustaw wszystkie wartości właściwości, które są potrzebne w Twojej `WebRequest` obiektu. Na przykład, aby włączyć uwierzytelnianie, należy ustawić <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> właściwości wystąpienia <xref:System.Net.NetworkCredential> klasy:
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3.  Określ metodę protokołu, który zezwala na dane mają być wysyłane z żądaniem, takich jak HTTP `POST` metody:  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  Ustaw <xref:System.Web.HttpRequest.ContentLength> liczbę bajtów w przypadku dołączania do żądania. Na przykład: 
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  Ustaw <xref:System.Web.HttpRequest.ContentType> właściwość do odpowiedniej wartości. Na przykład:
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  Strumień, że przechowuje dane żądania przez wywołanie metody GET <xref:System.Net.WebRequest.GetRequestStream%2A> metody. Na przykład:
  
    ```csharp  
    Stream dataStream = request.GetRequestStream();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream()  
    ```  
  
7.  Zapisane dane <xref:System.IO.Stream> obiektu zwróconego przez `GetRequestStream` metody. Na przykład:
  
    ```csharp  
    dataStream.Write(byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write(byteArray, 0, byteArray.Length)  
    ```  
  
8.  Zamknij strumień żądań przez wywołanie metody <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody. Na przykład:
  
    ```csharp  
    dataStream.Close();  
    ```  
  
    ```vb  
    dataStream.Close()  
    ```  
  
9. Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>. Ta metoda zwraca obiekt zawierający odpowiedź serwera. Zwrócony `WebResponse` typ obiektu jest określana przez schemat identyfikatora URI żądania. Na przykład:
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
10. Można uzyskać dostęp do właściwości usługi `WebResponse` obiektu lub go rzutować do wystąpienia oparte na protokole można odczytać właściwości specyficzne dla protokołu. 

    Na przykład, aby właściwości dostępu właściwe dla protokołu HTTP <xref:System.Net.HttpWebResponse>, rzutowania swoje `WebResponse` obiekt <xref:System.Net.HttpWebResponse> odwołania. Poniższy przykład kodu pokazuje sposób wyświetlania specyficzne dla protokołu HTTP <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> właściwości wysyłane odpowiedzi:
  
    ```csharp  
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);    
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. Aby uzyskać strumienia zawierające dane odpowiedzi wysyłane przez serwer, należy wywołać <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metody usługi `WebResponse` obiektu. Na przykład:
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
12. Po zapoznaniu się dane z obiektu odpowiedzi, albo zamknij je za pomocą <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody lub zamknij odpowiedzi przesyłania strumieniowego przy użyciu <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody. Jeśli nie zamkniesz odpowiedzi lub strumienia, aplikację można Brak połączenia z serwerem i stają się nie może przetworzyć żądań dodatkowych. Ponieważ `WebResponse.Close` wywołania metody `Stream.Close` jego zamknięciem odpowiedzi nie jest konieczne wywołać `Close` obiektów odpowiedzi i strumienia, mimo że takie postępowania tak nie jest szkodliwy. Na przykład:
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>Przykład  
  
Poniższy przykład kodu pokazuje, jak wysyłać dane do serwera sieci web i odczytywać je w swojej odpowiedzi:  

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a>Zobacz także

- [Tworzenie żądań internetowych](creating-internet-requests.md)
- [Stosowanie strumieni w sieci](using-streams-on-the-network.md)
- [Dostęp do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)
- [Żądanie danych](requesting-data.md)
- [Instrukcje: Żądanie danych przy użyciu klasy WebRequest](how-to-request-data-using-the-webrequest-class.md)
