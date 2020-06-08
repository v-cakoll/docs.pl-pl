---
title: Stosowanie strumieni w sieci
description: .NET Framework reprezentuje zasoby sieciowe jako strumienie. Klasa NetworkStream implementuje klasę strumienia do użycia z zasobami sieciowymi.
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
ms.openlocfilehash: f8d35b43c9b46a77bfd0c78f7d0118093b6fe824
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501979"
---
# <a name="using-streams-on-the-network"></a>Stosowanie strumieni w sieci
Zasoby sieciowe są reprezentowane w .NET Framework jako strumienie. Traktując strumienie ogólnie, .NET Framework oferuje następujące możliwości:  
  
- Typowy sposób wysyłania i odbierania danych w sieci Web. Bez względu na rzeczywistą zawartość pliku — HTML, XML lub coś innego — aplikacja będzie używać programu <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> oraz <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> do wysyłania i odbierania danych.  
  
- Zgodność ze strumieniami w .NET Framework. Strumienie są używane w całym .NET Framework, który ma rozbudowaną infrastrukturę do ich obsługi. Na przykład można zmodyfikować aplikację, która odczytuje dane XML z pliku, <xref:System.IO.FileStream> aby odczytywać dane z <xref:System.Net.Sockets.NetworkStream> zamiast tego, zmieniając tylko kilka wierszy kodu, które inicjują strumień. Główne różnice między klasą **NetworkStream** i innymi strumieniami polegają na tym, że **NetworkStream** nie można przeszukiwać, <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> Właściwość zawsze zwraca **wartość false**, a <xref:System.Net.Sockets.NetworkStream.Seek%2A> <xref:System.Net.Sockets.NetworkStream.Position%2A> metody i generują <xref:System.NotSupportedException> .  
  
- Przetwarzanie danych po ich nadejściu. Strumienie zapewniają dostęp do danych w miarę docierania do sieci, a nie wymuszają, aby aplikacja czekała na pobranie całego zestawu danych.  
  
 <xref:System.Net.Sockets>Przestrzeń nazw zawiera klasę **NetworkStream** , która implementuje <xref:System.IO.Stream> klasę specyficzną do użycia z zasobami sieciowymi. Klasy w <xref:System.Net.Sockets> przestrzeni nazw używają klasy **NetworkStream** do reprezentowania strumieni.  
  
 Aby wysłać dane do sieci przy użyciu zwróconego strumienia, wywołaj polecenie <xref:System.Net.WebRequest.GetRequestStream%2A> <xref:System.Net.WebRequest> . **Żądanie WebRequest** wyśle nagłówki żądań do serwera; następnie można wysłać dane do zasobu sieciowego przez wywołanie <xref:System.IO.Stream.BeginWrite%2A> <xref:System.IO.Stream.EndWrite%2A> metody,, lub <xref:System.IO.Stream.Write%2A> w zwróconym strumieniu. Niektóre protokoły, takie jak HTTP, mogą wymagać ustawienia właściwości specyficznych dla protokołu przed wysłaniem danych. Poniższy przykład kodu pokazuje, jak ustawić właściwości specyficzne dla protokołu HTTP na potrzeby wysyłania danych. Przyjęto założenie, że zmienna `sendData` zawiera dane do wysłania, a zmienna `sendLength` to liczba bajtów danych do wysłania.  
  
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
  
 Aby odbierać dane z sieci, wywołaj <xref:System.Net.WebResponse.GetResponseStream%2A> <xref:System.Net.WebResponse> . Następnie można odczytywać dane z zasobu sieciowego przez wywołanie <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A> metody,, lub <xref:System.IO.Stream.Read%2A> w zwróconym strumieniu.  
  
 Korzystając ze strumieni z zasobów sieciowych, należy pamiętać o następujących kwestiach:  
  
- Właściwość **CanSeek** zawsze zwraca **wartość false** , ponieważ Klasa **NetworkStream** nie może zmienić pozycji w strumieniu. Metody **Seek** i **Position** zwracają **NotSupportedException**.  
  
- W przypadku używania **WebRequest** i **WebResponse**wystąpienia strumienia utworzone przez wywołanie **metody GetResponseStream** są tylko do odczytu, a wystąpienia strumienia utworzone przez wywołanie **GetRequestStream** są tylko do zapisu.  
  
- Użyj <xref:System.IO.StreamReader> klasy, aby ułatwić kodowanie. Poniższy przykład kodu używa **StreamReader** , aby odczytać strumień zakodowany w formacie ASCII z **WebResponse** (przykład nie pokazuje tworzenia żądania).  
  
- Wywołanie metody **GetResponse** może blokować, jeśli zasoby sieciowe są niedostępne. Należy rozważyć użycie żądania asynchronicznego z <xref:System.Net.WebRequest.BeginGetResponse%2A> <xref:System.Net.WebRequest.EndGetResponse%2A> metodami i.  
  
- Wywołanie **GetRequestStream** może blokować się podczas tworzenia połączenia z serwerem. Należy rozważyć użycie asynchronicznego żądania dla strumienia przy użyciu <xref:System.Net.WebRequest.BeginGetRequestStream%2A> <xref:System.Net.WebRequest.EndGetRequestStream%2A> metod i.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: żądanie danych przy użyciu klasy WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Żądanie danych](requesting-data.md)
