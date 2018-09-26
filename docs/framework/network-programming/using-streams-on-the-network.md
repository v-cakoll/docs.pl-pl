---
title: Stosowanie strumieni w sieci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, streams
- Networking
- response to Internet request, streams
- network resources, stream capabilities
- receiving data, stream capabilities
- Network Resources
- sending data, stream capabilities
- downloading Internet resources, streams
- streams, capabilities
- Internet, streams
- streams
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1157fd8772546a1e34343bcf05ac40ca8ad592a5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47194027"
---
# <a name="using-streams-on-the-network"></a>Stosowanie strumieni w sieci
Zasoby sieciowe są reprezentowane w .NET Framework jako strumieni. Traktując strumieni ogólną, .NET Framework oferuje następujące możliwości:  
  
-   Typowym sposobem wysyłania i odbierania danych w sieci Web. Niezależnie od rzeczywistej zawartości pliku — HTML, XML lub czymkolwiek — aplikacja będzie używać <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> i <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> do wysyłania i odbierania danych.  
  
-   Zgodność ze strumieniami w programie .NET Framework. Strumienie są używane w .NET Framework, który ma rozbudowane infrastruktury do ich obsługi. Na przykład, można zmodyfikować aplikację, która odczytuje dane XML z <xref:System.IO.FileStream> można odczytać danych z <xref:System.Net.Sockets.NetworkStream> zamiast zmieniając tylko kilka wierszy kodu, które zainicjować strumienia. Główne różnice między **Strumień NetworkStream** klasy i inne strumienie są, **Strumień NetworkStream** nie można wyszukać, <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> właściwość zawsze zwraca **false**i <xref:System.Net.Sockets.NetworkStream.Seek%2A> i <xref:System.Net.Sockets.NetworkStream.Position%2A> metod generują <xref:System.NotSupportedException>.  
  
-   Przetwarzanie danych podczas ich nadejściu. Strumienie zapewniają dostęp do danych niezapisywanie ich w sieci, zamiast wymuszania aplikacji oczekiwania dla całego zestawu danych do pobrania.  
  
 <xref:System.Net.Sockets> Przestrzeń nazw zawiera **Strumień NetworkStream** klasę, która implementuje <xref:System.IO.Stream> klasy specjalnie do użytku z zasobów sieciowych. Klasy w <xref:System.Net.Sockets> przestrzeni nazw korzystają z **Strumień NetworkStream** klasy do reprezentowania strumieni.  
  
 Aby wysyłać dane do sieci przy użyciu zwróconym strumieniu, należy wywołać <xref:System.Net.WebRequest.GetRequestStream%2A> na Twoje <xref:System.Net.WebRequest>. **WebRequest** wyśle nagłówki żądania do serwera; a następnie mogą wysyłać dane do zasobu sieciowego, wywołując <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, lub <xref:System.IO.Stream.Write%2A> metody w zwróconym strumieniu. Niektóre protokoły, takie jak HTTP, może wymagać ustawienia właściwości specyficzne dla protokołu przed wysłaniem danych. Poniższy przykład kodu pokazuje sposób ustawiania właściwości specyficzne dla protokołu HTTP do wysyłania danych. Założono, że zmienna `sendData` zawiera dane do wysłania oraz że zmiennej `sendLength` jest to liczba bajtów danych do wysłania.  
  
```csharp  
HttpWebRequest request =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 Aby odbierać dane z sieci, należy wywołać <xref:System.Net.WebResponse.GetResponseStream%2A> na Twoje <xref:System.Net.WebResponse>. Można następnie odczytywać dane z zasobów sieciowych, wywołując <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, lub <xref:System.IO.Stream.Read%2A> metody w zwróconym strumieniu.  
  
 Podczas za pomocą strumieni z zasobów sieciowych, należy uwzględnić następujące kwestie:  
  
-   **CanSeek** właściwość zawsze zwraca **false** ponieważ **Strumień NetworkStream** klasy nie można zmienić pozycji w strumieniu. **Seek** i **pozycji** metod generują **wyjątek NotSupportedException**.  
  
-   Kiedy używasz **WebRequest** i **elementu WebResponse**, strumienia wystąpienia utworzone przez wywołanie metody **GetResponseStream dla** są przeznaczone tylko do odczytu i przesyłania strumieniowego utworzonych przez wywoływanie wystąpień **GetRequestStream** są przeznaczone tylko do zapisu.  
  
-   Użyj <xref:System.IO.StreamReader> klasie, aby łatwiej kodowania. Poniższy przykład kodu wykorzystuje **StreamReader** do odczytu strumień zakodowany w formacie ASCII od **elementu WebResponse** (przykład wyświetla tworzenia żądania).  
  
-   Wywołanie **metody GetResponse** można zablokować, jeśli zasoby sieciowe nie są dostępne. Należy rozważyć użycie żądania asynchronicznego przy użyciu <xref:System.Net.WebRequest.BeginGetResponse%2A> i <xref:System.Net.WebRequest.EndGetResponse%2A> metody.  
  
-   Wywołanie **GetRequestStream** można zablokować, gdy zostanie utworzone połączenie z serwerem. Należy rozważyć użycie żądania asynchronicznego strumienia z <xref:System.Net.WebRequest.BeginGetRequestStream%2A> i <xref:System.Net.WebRequest.EndGetRequestStream%2A> metody.  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =   
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _   
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: żądanie danych przy użyciu klasy WebRequest](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [Żądanie danych](../../../docs/framework/network-programming/requesting-data.md)
