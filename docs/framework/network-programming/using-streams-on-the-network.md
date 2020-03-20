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
ms.openlocfilehash: 7d5a2e3eec9b49731a09f6eb41a8d8500a59b45c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180624"
---
# <a name="using-streams-on-the-network"></a>Stosowanie strumieni w sieci
Zasoby sieciowe są reprezentowane w ramach .NET Framework jako strumienie. Traktując strumienie ogólnie, .NET Framework oferuje następujące możliwości:  
  
- Typowy sposób wysyłania i odbierania danych sieci Web. Niezależnie od rzeczywistej zawartości pliku — HTML, XML lub <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> cokolwiek innego — aplikacja będzie używać i <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> wysyłać i odbierać dane.  
  
- Zgodność ze strumieniami w ramach .NET Framework. Strumienie są używane w całej .NET Framework, który ma bogatą infrastrukturę do ich obsługi. Na przykład można zmodyfikować aplikację, która odczytuje dane XML z danych <xref:System.IO.FileStream> do odczytu <xref:System.Net.Sockets.NetworkStream> z zamiast tego, zmieniając tylko kilka wierszy kodu, które inicjują strumień. Główne różnice między **NetworkStream** klasy i innych strumieni są, że <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> **NetworkStream** nie jest dostępny, właściwość zawsze zwraca **false**, i <xref:System.Net.Sockets.NetworkStream.Seek%2A> <xref:System.Net.Sockets.NetworkStream.Position%2A> metody throw a <xref:System.NotSupportedException>.  
  
- Przetwarzanie danych w miarę ich pojawiania się. Strumienie zapewniają dostęp do danych w miarę ich docierania z sieci, zamiast wymuszać, aby aplikacja czekała na pobranie całego zestawu danych.  
  
 Obszar <xref:System.Net.Sockets> nazw zawiera **networkstream** klasy, <xref:System.IO.Stream> która implementuje klasy specjalnie do użytku z zasobami sieciowymi. Klasy w <xref:System.Net.Sockets> obszarze nazw używają **NetworkStream** klasy do reprezentowania strumieni.  
  
 Aby wysłać dane do sieci przy <xref:System.Net.WebRequest.GetRequestStream%2A> użyciu <xref:System.Net.WebRequest>zwróconego strumienia, zadzwoń do swojego pliku . **WebRequest** wyśle nagłówki żądań do serwera; następnie można wysłać dane do zasobu sieciowego, wywołując <xref:System.IO.Stream.BeginWrite%2A>metodę , <xref:System.IO.Stream.EndWrite%2A>lub <xref:System.IO.Stream.Write%2A> metodę zwracany strumień. Niektóre protokoły, takie jak HTTP, mogą wymagać skonfigurowania właściwości specyficznych dla protokołu przed wysłaniem danych. W poniższym przykładzie kodu pokazano, jak ustawić właściwości specyficzne dla protokołu HTTP do wysyłania danych. Przyjęto założenie, `sendData` że zmienna zawiera dane `sendLength` do wysłania i że zmienna jest liczbą bajtów danych do wysłania.  
  
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
  
 Aby odbierać dane z <xref:System.Net.WebResponse.GetResponseStream%2A> sieci, zadzwoń do swojego <xref:System.Net.WebResponse>pliku . Następnie można odczytać dane z zasobu <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A>sieciowego, wywołując metodę , lub <xref:System.IO.Stream.Read%2A> metodę zwracany strumień.  
  
 Korzystając ze strumieni z zasobów sieciowych, należy pamiętać o następujących kwestiach:  
  
- Właściwość **CanSeek** zawsze zwraca **false,** ponieważ **Klasa NetworkStream** nie może zmienić pozycji w strumieniu. **Metody Szukaj** i **Pozycjonurz** **NotSupportedException**.  
  
- Podczas korzystania **z WebRequest** i **WebResponse**, wystąpienia strumienia utworzone przez wywołanie **GetResponseStream** są tylko do odczytu i wystąpienia strumienia utworzone przez wywołanie **GetRequestStream** są tylko do zapisu.  
  
- Użyj <xref:System.IO.StreamReader> klasy, aby ułatwić kodowanie. Poniższy przykład kodu używa **StreamReader** do odczytu strumienia zakodowanego ascii z **WebResponse** (w przykładzie nie pokazuje tworzenia żądania).  
  
- Wywołanie **GetResponse** można zablokować, jeśli zasoby sieciowe nie są dostępne. Należy rozważyć użycie żądania asynchronii <xref:System.Net.WebRequest.BeginGetResponse%2A> <xref:System.Net.WebRequest.EndGetResponse%2A> z i metod.  
  
- Wywołanie **GetRequestStream** można zablokować podczas tworzenia połączenia z serwerem. Należy rozważyć użycie asynchronii żądania dla <xref:System.Net.WebRequest.BeginGetRequestStream%2A> strumienia z i <xref:System.Net.WebRequest.EndGetRequestStream%2A> metod.  
  
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

- [Instrukcje: żądanie danych przy użyciu klasy WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Żądanie danych](requesting-data.md)
