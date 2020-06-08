---
title: 'Instrukcje: wysyłanie danych przy użyciu klasy WebRequest'
description: Dowiedz się, jak wysyłać dane do serwera przy użyciu klasy WebRequest w .NET Framework. Ta procedura jest często używana do publikowania danych na stronie sieci Web.
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 4b353250fec778ee8b352f13de6d7faaf15c13ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502447"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>Instrukcje: wysyłanie danych przy użyciu klasy WebRequest

Poniższa procedura zawiera opis czynności, które należy wykonać w celu wysłania danych do serwera programu. Ta procedura jest często używana do publikowania danych na stronie sieci Web.

## <a name="to-send-data-to-a-host-server"></a>Aby wysłać dane do serwera hosta

1. Utwórz <xref:System.Net.WebRequest> wystąpienie przez wywołanie <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> identyfikatora URI zasobu, takiego jak skrypt lub strona ASP.NET, która akceptuje dane. Na przykład:

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > .NET Framework zawiera klasy specyficzne dla protokołu pochodzące od <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> klas i dla identyfikatorów URI, które zaczynają się od *http:*, *https:*, *FTP:* i *File:*.

    Jeśli konieczne jest ustawienie lub odczytanie właściwości specyficznych dla protokołu, należy rzutować <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> obiekt lub na typ obiektu specyficzny dla protokołu. Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](programming-pluggable-protocols.md).

2. Ustaw wartości właściwości, które są potrzebne w `WebRequest` obiekcie. Na przykład aby włączyć uwierzytelnianie, należy ustawić <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> Właściwość na wystąpienie <xref:System.Net.NetworkCredential> klasy:

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. Określ metodę protokołu, która zezwala na wysyłanie danych przy użyciu żądania, takiego jak `POST` Metoda http:

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. Ustaw <xref:System.Web.HttpRequest.ContentLength> Właściwość na liczbę bajtów, które są dołączane do żądania. Na przykład:

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. Ustaw <xref:System.Web.HttpRequest.ContentType> Właściwość na odpowiednią wartość. Na przykład:

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. Pobierz strumień, który przechowuje dane żądania przez wywołanie <xref:System.Net.WebRequest.GetRequestStream%2A> metody. Na przykład:

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. Zapisz dane do <xref:System.IO.Stream> obiektu zwróconego przez `GetRequestStream` metodę. Na przykład:

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. Zamknij strumień żądań, wywołując <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metodę. Na przykład:

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> . Ta metoda zwraca obiekt zawierający odpowiedź serwera. Typ zwracanego `WebResponse` obiektu jest określany przez schemat identyfikatora URI żądania. Na przykład:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. Możesz uzyskać dostęp do właściwości `WebResponse` obiektu lub rzutować go do wystąpienia specyficznego dla protokołu, aby odczytywać właściwości specyficzne dla protokołu.

    Na przykład, aby uzyskać dostęp do właściwości specyficznych dla protokołu HTTP <xref:System.Net.HttpWebResponse> , należy rzutować `WebResponse` obiekt na <xref:System.Net.HttpWebResponse> odwołanie. Poniższy przykład kodu pokazuje, jak wyświetlić Właściwość specyficzną dla protokołu HTTP, która <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> jest wysyłana z odpowiedzią:

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. Aby uzyskać strumień zawierający dane odpowiedzi wysyłane przez serwer, wywołaj <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodę `WebResponse` obiektu. Na przykład:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. Po odczytaniu danych z obiektu Response należy zamknąć je za pomocą <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody lub zamknąć strumień odpowiedzi przy użyciu <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody. Jeśli nie zamkniesz odpowiedzi lub strumienia, aplikacja może wyłączać połączenia z serwerem i nie może przetwarzać dodatkowych żądań. Ponieważ `WebResponse.Close` Metoda wywołuje się `Stream.Close` , gdy zamyka odpowiedź, nie jest konieczne wywoływanie `Close` zarówno obiektów odpowiedzi, jak i strumienia, chociaż nie jest to szkodliwe. Na przykład:

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób wysyłania danych do serwera sieci Web i odczytywania danych w odpowiedzi:

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a>Zobacz także

- [Tworzenie żądań internetowych](creating-internet-requests.md)
- [Używanie strumieni w sieci](using-streams-on-the-network.md)
- [Uzyskiwanie dostępu do Internetu za pomocą serwera proxy](accessing-the-internet-through-a-proxy.md)
- [Żądanie danych](requesting-data.md)
- [Instrukcje: żądanie danych przy użyciu klasy WebRequest](how-to-request-data-using-the-webrequest-class.md)
