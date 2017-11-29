---
title: "W sieci za pomocą strumieni"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f9e011b304a7f6c7d0d07761677c0368efcfcf4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-streams-on-the-network"></a>W sieci za pomocą strumieni
Zasoby sieciowe są reprezentowane w programie .NET Framework jako strumieni. Traktując strumieni objęty, .NET Framework oferuje następujące możliwości:  
  
-   Typowym sposobem wysyłania i odbierania danych w sieci Web. Niezależnie od rzeczywistej zawartości pliku — HTML, XML lub jakikolwiek inny — aplikacja będzie korzystać z <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> i <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> do wysyłania i odbierania danych.  
  
-   Zgodność ze strumieni w programie .NET Framework. Strumienie są używane w .NET Framework, który ma rozbudowane infrastruktury dla ich obsługę. Na przykład można zmodyfikować aplikację, która odczytuje dane XML z <xref:System.IO.FileStream> można odczytać danych z <xref:System.Net.Sockets.NetworkStream> zamiast zmieniając tylko kilka wierszy kodu inicjowania strumienia. Główne różnice między **Strumień NetworkStream** klasy i innych strumieni są, który **Strumień NetworkStream** nie można wyszukać, <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> właściwość zawsze zwraca **false**i <xref:System.Net.Sockets.NetworkStream.Seek%2A> i <xref:System.Net.Sockets.NetworkStream.Position%2A> throw metody <xref:System.NotSupportedException>.  
  
-   Przetwarzanie danych, ponieważ nadejściu. Strumienie zapewniają dostęp do danych, odbieraną z sieci, zamiast wymuszania aplikacji oczekiwania cały zestaw danych do pobrania.  
  
 <xref:System.Net.Sockets> Przestrzeń nazw zawiera **Strumień NetworkStream** klasa implementująca <xref:System.IO.Stream> specjalnie do użycia z zasobów sieciowych. Klasy w <xref:System.Net.Sockets> przestrzeni nazw, użyj **Strumień NetworkStream** klasy do reprezentowania strumieni.  
  
 Aby wysyłać dane do sieci przy użyciu strumienia zwrócone, należy wywołać <xref:System.Net.WebRequest.GetRequestStream%2A> na Twojej <xref:System.Net.WebRequest>. **WebRequest** wyśle nagłówki żądania do serwera; a następnie może wysyłać dane do zasobu sieciowego, wywołując <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, lub <xref:System.IO.Stream.Write%2A> metody w zwróconym strumieniu. Niektóre protokołów, takich jak HTTP, może wymagać można ustawić właściwości specyficzne dla protokołu przed wysłaniem danych. Poniższy przykładowy kod przedstawia sposób ustawiania właściwości specyficzne dla protokołu HTTP do wysłania danych. Przy założeniu, że zmienna `sendData` zawiera dane do wysłania, a zmienna `sendLength` jest to liczba bajtów danych do wysyłania.  
  
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
  
 Aby odbierać dane z sieci, należy wywołać <xref:System.Net.WebResponse.GetResponseStream%2A> na Twojej <xref:System.Net.WebResponse>. Można następnie odczytywać dane z zasobów sieciowych, wywołując <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, lub <xref:System.IO.Stream.Read%2A> metody w zwróconym strumieniu.  
  
 Korzystając z strumieni z zasobów sieciowych, należy pamiętać następujące kwestie:  
  
-   **CanSeek** właściwość zawsze zwraca **false** ponieważ **Strumień NetworkStream** klasy nie można zmienić pozycją w strumieniu. **Wyszukiwania** i **pozycji** metod generują **notsupportedexception —**.  
  
-   Jeśli używasz **WebRequest** i **WebResponse**, strumienia wystąpienia utworzone przez wywołanie metody **GetResponseStream** są tylko do odczytu i wystąpienia utworzone przez wywołanie metody strumienia **GetRequestStream** są tylko do zapisu.  
  
-   Użyj <xref:System.IO.StreamReader> klasie, aby łatwiej kodowania. Poniższy przykład kodu wykorzystuje **StreamReader** odczytać kodowany w formacie ASCII strumienia z **WebResponse** (przykładzie nie są wyświetlane tworzenia żądania).  
  
-   Wywołanie **GetResponse** można zablokować, jeśli zasoby sieciowe nie są dostępne. Należy rozważyć użycie asynchroniczne żądanie z <xref:System.Net.WebRequest.BeginGetResponse%2A> i <xref:System.Net.WebRequest.EndGetResponse%2A> metody.  
  
-   Wywołanie **GetRequestStream** zablokować podczas tworzenia połączenia z serwerem. Należy rozważyć użycie asynchroniczne żądanie dla tego strumienia z <xref:System.Net.WebRequest.BeginGetRequestStream%2A> i <xref:System.Net.WebRequest.EndGetRequestStream%2A> metody.  
  
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
 [Porady: dane przy użyciu klasy WebRequest żądania](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [Żądanie danych](../../../docs/framework/network-programming/requesting-data.md)
