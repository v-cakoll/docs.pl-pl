---
title: 'Jak: Wysyłanie danych przy użyciu WebRequest klasy'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 2467b289df7a0361b51ad91d4458d32742c42275
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70040827"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>Jak: Wysyłanie danych przy użyciu WebRequest klasy

W poniższej procedurze opisano kroki wysyłania danych do serwera. Ta procedura jest często używana do publikowania danych na stronie sieci Web.

## <a name="to-send-data-to-a-host-server"></a>Aby wysłać dane do serwera hosta

1. Utwórz <xref:System.Net.WebRequest> wystąpienie, wywołując <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> z identyfikatorem URI zasobu, takiego jak skrypt lub strona ASP.NET, która akceptuje dane. Przykład:

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > .NET Framework zawiera klasy specyficzne dla <xref:System.Net.WebRequest> protokołu <xref:System.Net.WebResponse> pochodzące z i klasy dla identyfikatorów URI, które zaczynają się od *http:*, *https:*, *ftp:*, i *plik:*.

    Jeśli chcesz ustawić lub odczytać właściwości specyficzne dla protokołu, <xref:System.Net.WebResponse> należy rzutować lub <xref:System.Net.WebRequest> obiekt do typu obiektu specyficznego dla protokołu. Aby uzyskać więcej informacji, zobacz [Programowanie protokołów podłączanych](programming-pluggable-protocols.md).

2. Ustaw wszystkie wartości właściwości, `WebRequest` które są potrzebne w obiekcie. Na przykład, aby włączyć <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> uwierzytelnianie, ustaw <xref:System.Net.NetworkCredential> właściwość na wystąpienie klasy:

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. Określ metodę protokołu, która umożliwia przesyłanie danych za `POST` pomocą żądania, na przykład metodę HTTP:

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. Ustaw <xref:System.Web.HttpRequest.ContentLength> właściwość na liczbę bajtów, które zawierasz z żądaniem. Przykład:

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. Ustaw <xref:System.Web.HttpRequest.ContentType> właściwość na odpowiednią wartość. Przykład:

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. Pobierz strumień, który przechowuje <xref:System.Net.WebRequest.GetRequestStream%2A> dane żądania, wywołując metodę. Przykład:

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. Zapisz dane do <xref:System.IO.Stream> obiektu zwróconego `GetRequestStream` przez metodę. Przykład:

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. Zamknij strumień żądania, <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> wywołując metodę. Przykład:

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. Wyślij żądanie do serwera, <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>dzwoniąc . Ta metoda zwraca obiekt zawierający odpowiedź serwera. Typ `WebResponse` zwracanego obiektu jest określany przez schemat identyfikatora URI żądania. Przykład:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. Można uzyskać dostęp do `WebResponse` właściwości obiektu lub przerzucić go do wystąpienia specyficznego dla protokołu, aby odczytać właściwości specyficzne dla protokołu.

    Na przykład, aby uzyskać dostęp do <xref:System.Net.HttpWebResponse>właściwości `WebResponse` specyficznych <xref:System.Net.HttpWebResponse> dla protokołu HTTP , rzutuj obiekt na odwołanie. W poniższym przykładzie kodu pokazano, <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> jak wyświetlić właściwość specyficzną dla protokołu HTTP wysłaną z odpowiedzią:

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. Aby uzyskać strumień zawierający dane odpowiedzi wysyłane <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> przez serwer, wywołaj metodę obiektu. `WebResponse` Przykład:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. Po przeczytaniu danych z obiektu odpowiedzi zamknij go <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> za pomocą metody lub zamknij <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> strumień odpowiedzi za pomocą metody. Jeśli nie zamkniesz odpowiedzi lub strumienia, aplikacja może zabraknąć połączeń z serwerem i nie będzie w stanie przetworzyć dodatkowych żądań. Ponieważ `WebResponse.Close` metoda `Stream.Close` wywołuje, gdy zamyka odpowiedź, nie jest `Close` konieczne wywołanie zarówno odpowiedzi i strumienia obiektów, chociaż w ten sposób nie jest szkodliwe. Przykład:

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak wysyłać dane do serwera sieci web i odczytywać dane w odpowiedzi:

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a>Zobacz też

- [Tworzenie żądań internetowych](creating-internet-requests.md)
- [Korzystanie ze strumieni w sieci](using-streams-on-the-network.md)
- [Uzyskiwanie dostępu do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)
- [Żądanie danych](requesting-data.md)
- [Jak: Żądanie danych przy użyciu WebRequest klasy](how-to-request-data-using-the-webrequest-class.md)
