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
ms.openlocfilehash: 2467b289df7a0361b51ad91d4458d32742c42275
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040827"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>Instrukcje: Wyślij dane przy użyciu klasy WebRequest

Poniższa procedura zawiera opis czynności, które należy wykonać w celu wysłania danych do serwera programu. Ta procedura jest często używana do publikowania danych na stronie sieci Web.

## <a name="to-send-data-to-a-host-server"></a>Aby wysłać dane do serwera hosta

1. Utwórz wystąpienie przez wywołanie <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> identyfikatora URI zasobu, takiego jak skrypt lub strona ASP.NET, która akceptuje dane. <xref:System.Net.WebRequest> Na przykład:

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > .NET Framework zawiera klasy specyficzne <xref:System.Net.WebRequest> dla protokołu pochodzące od klas i <xref:System.Net.WebResponse> dla identyfikatorów URI, które zaczynają się od *http:* , *https:* , *FTP:* i *File:* .

    Jeśli konieczne jest ustawienie lub odczytanie właściwości specyficznych dla protokołu, należy rzutować <xref:System.Net.WebRequest> obiekt <xref:System.Net.WebResponse> lub na typ obiektu specyficzny dla protokołu. Aby uzyskać więcej informacji, zobacz [programowanie protokołów](programming-pluggable-protocols.md)podłączanych.

2. Ustaw wartości właściwości, które są potrzebne w `WebRequest` obiekcie. Na przykład aby włączyć uwierzytelnianie, należy ustawić <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> właściwość na wystąpienie <xref:System.Net.NetworkCredential> klasy:

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. Określ metodę protokołu, która zezwala na wysyłanie danych przy użyciu żądania, takiego jak Metoda http `POST` :

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <xref:System.Web.HttpRequest.ContentLength> Ustaw właściwość na liczbę bajtów, które są dołączane do żądania. Na przykład:

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <xref:System.Web.HttpRequest.ContentType> Ustaw właściwość na odpowiednią wartość. Przykład:

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. Pobierz strumień, który przechowuje dane żądania przez wywołanie <xref:System.Net.WebRequest.GetRequestStream%2A> metody. Przykład:

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

8. Zamknij strumień żądań, wywołując <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metodę. Przykład:

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>. Ta metoda zwraca obiekt zawierający odpowiedź serwera. Typ zwracanego `WebResponse` obiektu jest określany przez schemat identyfikatora URI żądania. Przykład:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. Możesz uzyskać dostęp do właściwości `WebResponse` obiektu lub rzutować go do wystąpienia specyficznego dla protokołu, aby odczytywać właściwości specyficzne dla protokołu.

    Na przykład, aby uzyskać dostęp do właściwości <xref:System.Net.HttpWebResponse>specyficznych dla protokołu HTTP, należy `WebResponse` rzutować <xref:System.Net.HttpWebResponse> obiekt na odwołanie. Poniższy przykład kodu pokazuje, jak wyświetlić Właściwość specyficzną <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> dla protokołu HTTP, która jest wysyłana z odpowiedzią:

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

12. Po odczytaniu danych z obiektu Response należy zamknąć je za pomocą <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody lub zamknąć strumień odpowiedzi <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> przy użyciu metody. Jeśli nie zamkniesz odpowiedzi lub strumienia, aplikacja może wyłączać połączenia z serwerem i nie może przetwarzać dodatkowych żądań. Ponieważ metoda wywołuje `Stream.Close` się, gdy zamyka odpowiedź, nie jest konieczne wywoływanie `Close` zarówno obiektów odpowiedzi, jak i strumienia, chociaż nie jest to szkodliwe. `WebResponse.Close` Na przykład:

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
- [Instrukcje: Żądanie danych przy użyciu klasy WebRequest](how-to-request-data-using-the-webrequest-class.md)
