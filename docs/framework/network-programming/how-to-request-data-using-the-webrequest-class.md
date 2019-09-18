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
ms.openlocfilehash: e670a2a503ce704eff847e9e0b3ee340ab52fe62
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048166"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>Instrukcje: Żądanie danych przy użyciu klasy WebRequest

Poniższa procedura zawiera opis czynności, które należy wykonać w celu zażądania zasobu, takiego jak strona sieci Web lub plik, z serwera programu. Zasób musi być identyfikowany za pomocą identyfikatora URI.

## <a name="to-request-data-from-a-host-server"></a>Aby zażądać danych z serwera hosta

1. Utwórz wystąpienie, wywołując <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> identyfikator URI zasobu. <xref:System.Net.WebRequest> Na przykład:

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
    ```

    > [!NOTE]
    > .NET Framework zawiera klasy specyficzne <xref:System.Net.WebRequest> dla protokołu pochodzące od klas i <xref:System.Net.WebResponse> dla identyfikatorów URI, które zaczynają się od *http:* , *https:* , *FTP:* i *File:* .

    Jeśli konieczne jest ustawienie lub odczytanie właściwości specyficznych dla protokołu, należy rzutować <xref:System.Net.WebRequest> obiekt <xref:System.Net.WebResponse> lub na typ obiektu specyficzny dla protokołu. Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](programming-pluggable-protocols.md).

2. Ustaw wartości właściwości, które są potrzebne w `WebRequest` obiekcie. Na przykład aby włączyć uwierzytelnianie, należy ustawić <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> właściwość na wystąpienie <xref:System.Net.NetworkCredential> klasy:

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. Wyślij żądanie do serwera przez wywołanie metody <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>. Ta metoda zwraca obiekt zawierający odpowiedź serwera. Typ zwracanego <xref:System.Net.WebResponse> obiektu jest określany przez schemat identyfikatora URI żądania. Na przykład:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. Możesz uzyskać dostęp do właściwości `WebResponse` obiektu lub rzutować go do wystąpienia specyficznego dla protokołu, aby odczytywać właściwości specyficzne dla protokołu.

    Na przykład, aby uzyskać dostęp do właściwości <xref:System.Net.HttpWebResponse>specyficznych dla protokołu HTTP, należy `WebResponse` rzutować `HttpWebResponse` obiekt na odwołanie. Poniższy przykład kodu pokazuje, jak wyświetlić Właściwość specyficzną <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> dla protokołu HTTP, która jest wysyłana z odpowiedzią:

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

6. Po odczytaniu danych z obiektu Response należy zamknąć je za pomocą <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody lub zamknąć strumień odpowiedzi <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> przy użyciu metody. Jeśli nie zamkniesz obiektu Response lub strumienia, aplikacja może wyłączać połączenia z serwerem i nie może przetwarzać dodatkowych żądań. Ponieważ metoda wywołuje `Stream.Close` się, gdy zamyka odpowiedź, nie jest konieczne wywoływanie `Close` zarówno obiektów odpowiedzi, jak i strumienia, chociaż nie jest to szkodliwe. `WebResponse.Close` Na przykład:

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
- [Instrukcje: Wyślij dane przy użyciu klasy WebRequest](how-to-send-data-using-the-webrequest-class.md)
