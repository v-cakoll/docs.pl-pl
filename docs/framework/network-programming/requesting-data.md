---
title: Żądanie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sending data
- WebRequest class, sending and receiving data
- requesting data from Internet, about requesting data
- WebClient class, sending and receiving data
- network, requesting data
- receiving data
- sending data, about sending data
- response to Internet request, about responding to Internet requests
- data requests
- receiving data, about receiving data
- Internet, requesting data
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 166a076eae69b351248bc67570cdaf50b43ab95c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="requesting-data"></a>Żądanie danych
Tworzenie aplikacji uruchamianych w rozproszonym środowisku operacyjnym współczesnych Internet wymaga wydajne, łatwy w użyciu metody do pobierania danych z zasoby wszystkich typów. Protokoły Plug umożliwiają tworzenie aplikacji korzystających z jednego interfejsu do pobierania danych z wielu protokołów internetowych.  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>Przekazywanie i pobieranie danych z serwera internetowego  
 Proste żądania i odpowiedzi transakcji <xref:System.Net.WebClient> klasy zapewnia najprostszą przekazywanie danych do lub pobieranie danych z serwera internetowego. **WebClient** udostępnia metody, przekazywanie i pobieranie plików, wysyłania i odbierania strumieni i wysyłania buforu danych do serwera i odbierania odpowiedzi. **WebClient** używa <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy, do rzeczywistych połączeń z zasobem internetowym, powiększając wszelkie zarejestrowane protokołu podłączanej jest dostępny do użytku.  
  
 Aplikacje klienckie, które należy podjąć bardziej złożonej transakcji żądanie danych z serwerów za pomocą **WebRequest** klasy i jego obiektów podrzędnych. **WebRequest** hermetyzuje szczegóły połączenia z serwerem, wysyłania żądania i odbierania odpowiedzi. **WebRequest** jest klasą abstrakcyjną, który definiuje zestaw właściwości i metod, które są dostępne dla wszystkich aplikacji, które używają protokołów podłączany. Elementy podrzędne elementu **WebRequest**, takich jak <xref:System.Net.HttpWebRequest>, implementować właściwości i metody zdefiniowane przez **WebRequest** w taki sposób, który jest zgodny z protokołem podstawowej.  
  
 **WebRequest** klasy tworzy wystąpienia oparte na protokole **WebRequest** elementy podrzędne, używając wartości identyfikatora URI przekazane do jego <xref:System.Net.WebRequest.Create%2A> metodę, aby określić określonych-klas pochodnych wystąpienie do utworzenia. Wskazać aplikacje, które **WebRequest** obiekt podrzędny powinien być używany do obsługi żądania, rejestrując konstruktora obiektu podrzędnego z <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody.  
  
 Żądań z zasobem internetowym wywołując <xref:System.Net.WebRequest.GetResponse%2A> metoda **WebRequest**. **GetResponse** metoda tworzy żądanie oparte na protokole z właściwości **WebRequest**, sprawia, że połączenie gniazda TCP lub UDP do serwera i wysyła żądanie. Dla żądania, które wysyłają dane do serwera, takich jak HTTP **Post** lub FTP **Put** żądania, <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> metoda zapewnia strumienia sieci przesyłania danych.  
  
 **GetResponse** metoda zwraca wartość określonego protokołu **WebResponse** odpowiadającego **WebRequest.**  
  
 **WebResponse** klasa również jest klasą abstrakcyjną, która definiuje właściwości i metody, które są dostępne dla wszystkich aplikacji, które używają protokołów podłączany. **WebResponse** obiektów podrzędnych implementacji tych właściwości i metody dla podstawowy protokół. <xref:System.Net.HttpWebResponse> , Na przykład klasa implementuje **WebResponse** klasy dla protokołu HTTP.  
  
 Danych zwróconych przez serwer w odpowiedzi na tę aplikację w Strumień zwrócony przez <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metody. Można użyć tego strumienia, jak każdy inny, jak pokazano w poniższym przykładzie.  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie dla sieci w programie .NET Framework](../../../docs/framework/network-programming/index.md)  
 [Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)  
 [Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
