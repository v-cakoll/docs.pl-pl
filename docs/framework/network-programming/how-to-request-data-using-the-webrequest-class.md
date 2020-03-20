---
title: 'Jak: Żądanie danych przy użyciu WebRequest klasy'
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
ms.openlocfilehash: e670a2a503ce704eff847e9e0b3ee340ab52fe62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048166"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>Jak: Żądanie danych przy użyciu WebRequest klasy

W poniższej procedurze opisano kroki żądania zasobu, takiego jak strona sieci Web lub plik, z serwera. Zasób musi być identyfikowany przez identyfikator URI.

## <a name="to-request-data-from-a-host-server"></a>Aby zażądać danych z serwera hosta

1. Utwórz <xref:System.Net.WebRequest> wystąpienie, wywołując <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> z identyfikatorem URI zasobu. Przykład:

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
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

3. Wyślij żądanie do serwera, <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>dzwoniąc . Ta metoda zwraca obiekt zawierający odpowiedź serwera. Typ <xref:System.Net.WebResponse> zwracanego obiektu jest określany przez schemat identyfikatora URI żądania. Przykład:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. Można uzyskać dostęp do `WebResponse` właściwości obiektu lub przerzucić go do wystąpienia specyficznego dla protokołu, aby odczytać właściwości specyficzne dla protokołu.

    Na przykład, aby uzyskać dostęp do <xref:System.Net.HttpWebResponse>właściwości `WebResponse` specyficznych `HttpWebResponse` dla protokołu HTTP , rzutuj obiekt na odwołanie. W poniższym przykładzie kodu pokazano, <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> jak wyświetlić właściwość specyficzną dla protokołu HTTP wysłaną z odpowiedzią:

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. Aby uzyskać strumień zawierający dane odpowiedzi wysyłane <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> przez serwer, należy wywołać metodę. Przykład:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. Po przeczytaniu danych z obiektu odpowiedzi zamknij go <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> za pomocą metody lub zamknij <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> strumień odpowiedzi za pomocą metody. Jeśli nie zamkniesz obiektu odpowiedzi lub strumienia, aplikacja może zabraknąć połączeń z serwerem i nie będzie w stanie przetworzyć dodatkowych żądań. Ponieważ `WebResponse.Close` metoda `Stream.Close` wywołuje, gdy zamyka odpowiedź, nie jest `Close` konieczne wywołanie zarówno odpowiedzi i strumienia obiektów, chociaż w ten sposób nie jest szkodliwe. Przykład:

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak utworzyć żądanie do serwera sieci web i odczytać dane w odpowiedzi:

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a>Zobacz też

- [Tworzenie żądań internetowych](creating-internet-requests.md)
- [Korzystanie ze strumieni w sieci](using-streams-on-the-network.md)
- [Uzyskiwanie dostępu do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)
- [Żądanie danych](requesting-data.md)
- [Jak: Wysyłanie danych przy użyciu WebRequest klasy](how-to-send-data-using-the-webrequest-class.md)
