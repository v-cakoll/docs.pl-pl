---
title: 'Instrukcje: Żądanie danych przy użyciu klasy WebRequest'
ms.date: 03/21/2019
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
ms.openlocfilehash: 0a2d60a31b1875d948e07615e1613e2b163c15b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171057"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>Instrukcje: Żądanie danych przy użyciu klasy WebRequest
Poniższa procedura opisuje kroki, aby zażądać zasobu, np. strony sieci Web lub plik z serwera. Zasób musi być identyfikowany przez identyfikator URI.  
  
## <a name="to-request-data-from-a-host-server"></a>Żądanie danych z serwera hosta  
  
1.  Tworzenie <xref:System.Net.WebRequest> wystąpienia, wywołując <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> za pomocą identyfikatora URI zasobu. Na przykład: 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/default.html");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/default.html")  
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
  
3.  Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>. Ta metoda zwraca obiekt zawierający odpowiedź serwera. Zwrócony <xref:System.Net.WebResponse> typ obiektu jest określana przez schemat identyfikatora URI żądania. Na przykład:
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
4.  Można uzyskać dostęp do właściwości usługi `WebResponse` obiektu lub go rzutować do wystąpienia oparte na protokole można odczytać właściwości specyficzne dla protokołu. 

    Na przykład, aby właściwości dostępu właściwe dla protokołu HTTP <xref:System.Net.HttpWebResponse>, rzutowania swoje `WebResponse` obiekt `HttpWebResponse` odwołania. Poniższy przykład kodu pokazuje sposób wyświetlania specyficzne dla protokołu HTTP <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> właściwości wysyłane odpowiedzi:
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  Aby uzyskać strumienia zawierające dane odpowiedzi wysyłane przez serwer, należy wywołać <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metody. Na przykład:  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  Po zapoznaniu się dane z obiektu odpowiedzi, albo zamknij je za pomocą <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody lub zamknij odpowiedzi przesyłania strumieniowego przy użyciu <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody. Jeśli nie zamkniesz obiekt odpowiedzi lub strumienia, aplikację można Brak połączenia z serwerem i stają się nie może przetworzyć żądań dodatkowych. Ponieważ `WebResponse.Close` wywołania metody `Stream.Close` jego zamknięciem odpowiedzi nie jest konieczne wywołać `Close` obiektów odpowiedzi i strumienia, mimo że takie postępowania tak nie jest szkodliwy. Na przykład:
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>Przykład  

Poniższy przykład kodu pokazuje, jak utworzyć żądanie do serwera sieci web i odczytywać je w swojej odpowiedzi:  
  
[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a>Zobacz także

- [Tworzenie żądań internetowych](creating-internet-requests.md)
- [Stosowanie strumieni w sieci](using-streams-on-the-network.md)
- [Dostęp do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)
- [Żądanie danych](requesting-data.md)
- [Instrukcje: Wyślij dane przy użyciu klasy WebRequest](how-to-send-data-using-the-webrequest-class.md)
