---
title: 'Instrukcje: żądanie danych przy użyciu klasy WebRequest'
description: Dowiedz się, jak zażądać zasobu, takiego jak strona sieci Web lub plik, z serwera przy użyciu klasy WebRequest w .NET Framework.
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
ms.openlocfilehash: 5dcc1a7dad226288e3f74969b86e2dd457c0eed0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502473"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>Instrukcje: żądanie danych przy użyciu klasy WebRequest

Poniższa procedura zawiera opis czynności, które należy wykonać w celu zażądania zasobu, takiego jak strona sieci Web lub plik, z serwera programu. Zasób musi być identyfikowany za pomocą identyfikatora URI.

## <a name="to-request-data-from-a-host-server"></a>Aby zażądać danych z serwera hosta

1. Utwórz <xref:System.Net.WebRequest> wystąpienie, wywołując <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> Identyfikator URI zasobu. Na przykład:

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
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

3. Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> . Ta metoda zwraca obiekt zawierający odpowiedź serwera. Typ zwracanego <xref:System.Net.WebResponse> obiektu jest określany przez schemat identyfikatora URI żądania. Na przykład:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. Możesz uzyskać dostęp do właściwości `WebResponse` obiektu lub rzutować go do wystąpienia specyficznego dla protokołu, aby odczytywać właściwości specyficzne dla protokołu.

    Na przykład, aby uzyskać dostęp do właściwości specyficznych dla protokołu HTTP <xref:System.Net.HttpWebResponse> , należy rzutować `WebResponse` obiekt na `HttpWebResponse` odwołanie. Poniższy przykład kodu pokazuje, jak wyświetlić Właściwość specyficzną dla protokołu HTTP, która <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> jest wysyłana z odpowiedzią:

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. Aby uzyskać strumień zawierający dane odpowiedzi wysyłane przez serwer, wywołaj <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodę. Na przykład:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. Po odczytaniu danych z obiektu Response należy zamknąć je za pomocą <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody lub zamknąć strumień odpowiedzi przy użyciu <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody. Jeśli nie zamkniesz obiektu Response lub strumienia, aplikacja może wyłączać połączenia z serwerem i nie może przetwarzać dodatkowych żądań. Ponieważ `WebResponse.Close` Metoda wywołuje się `Stream.Close` , gdy zamyka odpowiedź, nie jest konieczne wywoływanie `Close` zarówno obiektów odpowiedzi, jak i strumienia, chociaż nie jest to szkodliwe. Na przykład:

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>Przykład

Poniższy przykład kodu przedstawia sposób tworzenia żądania na serwerze sieci Web i odczytywania danych w odpowiedzi:

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a>Zobacz także

- [Tworzenie żądań internetowych](creating-internet-requests.md)
- [Używanie strumieni w sieci](using-streams-on-the-network.md)
- [Uzyskiwanie dostępu do Internetu za pomocą serwera proxy](accessing-the-internet-through-a-proxy.md)
- [Żądanie danych](requesting-data.md)
- [Instrukcje: wysyłanie danych przy użyciu klasy WebRequest](how-to-send-data-using-the-webrequest-class.md)
