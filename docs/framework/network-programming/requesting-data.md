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
ms.openlocfilehash: 4e93b9395e92ff4c1c153f53e0f40ff18c12416a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641947"
---
# <a name="requesting-data"></a>Żądanie danych
Tworzenie aplikacji działających w rozproszonym środowisku operacyjnym Internet współczesnych wymaga wydajne i łatwy w użyciu metody pobierania danych z wszystkich typów zasobów. Podłączanych protokołów umożliwiają tworzenie aplikacji korzystających z jednego interfejsu do pobierania danych z wielu protokołów internetowych.  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>Przekazywanie i pobieranie danych z serwera internetowego  
 Dla prostego żądania i odpowiedzi transakcji <xref:System.Net.WebClient> klasy zapewnia najprostszą przekazywanie danych do lub pobieranie danych z serwera internetowego. **Usługa WebClient** zawiera metody służące do przekazywania i pobierania plików, wysyłania i odbierania strumieni i wysyłania bufor danych do serwera i odbierania odpowiedzi. **Usługa WebClient** używa <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy, aby tworzyć rzeczywiste połączenia z zasobem internetowym, co zarejestrowany dowolny protokół podłączania jest dostępny do użytku.  
  
 Aplikacje klienckie, które muszą stosować bardziej złożone dane żądania transakcji z serwerów za pomocą **WebRequest** klasy i jego obiektów podrzędnych. **WebRequest** hermetyzuje szczegóły połączenia z serwerem, wysyłania żądania i odbierania odpowiedzi. **WebRequest** jest klasą abstrakcyjną, który definiuje zestaw właściwości i metod, które są dostępne dla wszystkich aplikacji, które za pomocą podłączanych protokołów. Elementy podrzędne **WebRequest**, takich jak <xref:System.Net.HttpWebRequest>, implementować właściwości i metody zdefiniowane przez **WebRequest** w sposób, który jest zgodny z podstawowym protokole.  
  
 **WebRequest** klasy tworzy wystąpienia oparte na protokole **WebRequest** elementy podrzędne, używając wartości identyfikatora URI przekazywany do jego <xref:System.Net.WebRequest.Create%2A> metodę pozwala ustalić określonej klasy pochodnej wystąpienie do utworzenia. Wskazać aplikacje, które **WebRequest** podrzędny powinien być używany do obsługi żądania, rejestrując elementów podrzędnych konstruktora z <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody.  
  
 Żądania z zasobem internetowym, wywołując <xref:System.Net.WebRequest.GetResponse%2A> metody **WebRequest**. **Metody GetResponse** metoda konstrukcje żądania związane z protokołem we właściwościach **WebRequest**sprawia, że połączenie gniazda TCP lub UDP do serwera i wysyła żądanie. Dla żądań, które wysyłają dane do serwera, takich jak HTTP **wpis** lub FTP **umieścić** żądania, <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> metoda zapewnia strumienia sieci, w której chcesz wysłać dane.  
  
 **Metody GetResponse** metoda zwraca związane z protokołem **elementu WebResponse** odpowiadający **WebRequest.**  
  
 **Elementu WebResponse** klasy jest również klasę abstrakcyjną, która definiuje właściwości i metody, które są dostępne dla wszystkich aplikacji, które za pomocą podłączanych protokołów. **Elementu WebResponse** elementów potomnych zaimplementować te właściwości i metody dla podstawowych protokołów. <xref:System.Net.HttpWebResponse> Klasy, na przykład implementuje **elementu WebResponse** klasy do obsługi protokołu HTTP.  
  
 Dane zwrócone przez serwer jest prezentowana w aplikacji w Strumień zwrócony przez <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metody. Można użyć tego strumienia, jak każdy inny, jak pokazano w poniższym przykładzie.  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie dla sieci w programie .NET Framework](../../../docs/framework/network-programming/index.md)
- [Instrukcje: Żądanie strony internetowej i pobieranie wyników jako Stream](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [Instrukcje: Pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
