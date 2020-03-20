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
ms.openlocfilehash: 1f367caf7656a83597b6262a5746686df15d33b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047314"
---
# <a name="requesting-data"></a>Żądanie danych
Tworzenie aplikacji, które działają w rozproszonym środowisku operacyjnym dzisiejszego Internetu wymaga wydajnej, łatwej w użyciu metody pobierania danych z zasobów wszystkich typów. Protokoły podłączane umożliwiają tworzenie aplikacji korzystających z jednego interfejsu do pobierania danych z wielu protokołów internetowych.  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>Przekazywanie i pobieranie danych z serwera internetowego  
 W przypadku prostych transakcji żądań i odpowiedzi <xref:System.Net.WebClient> klasa zapewnia najprostszą metodę przekazywania danych do lub pobierania danych z serwera internetowego. **WebClient** udostępnia metody przekazywania i pobierania plików, wysyłania i odbierania strumieni oraz wysyłania buforu danych do serwera i odbierania odpowiedzi. **WebClient** używa <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klas do tworzenia rzeczywistych połączeń z zasobem internetowym, więc każdy zarejestrowany protokół pluggable jest dostępny do użycia.  
  
 Aplikacje klienckie, które muszą dokonać bardziej złożonych transakcji żądają danych z serwerów przy użyciu **klasy WebRequest** i jej elementów podrzędnych. **WebRequest** hermetyzuje szczegóły łączenia się z serwerem, wysyłania żądania i odbierania odpowiedzi. **WebRequest** to klasa abstrakcyjna, która definiuje zestaw właściwości i metod, które są dostępne dla wszystkich aplikacji, które używają protokołów podłączanych. Elementy podrzędne **WebRequest** <xref:System.Net.HttpWebRequest>, takie jak , implementują właściwości i metody zdefiniowane przez **WebRequest** w sposób zgodny z podstawowym protokołem.  
  
 **Klasa WebRequest** tworzy specyficzne dla protokołu wystąpienia elementów podrzędnych **WebRequest,** przy <xref:System.Net.WebRequest.Create%2A> użyciu wartości identyfikatora URI przekazany do jego metody w celu określenia określonego wystąpienia klasy pochodnej do utworzenia. Aplikacje wskazują, które **WebRequest** element podrzędny powinien być używany do <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> obsługi żądania, rejestrując konstruktora podrzędnego z metodą.  
  
 Żądanie jest dokonywane do zasobu <xref:System.Net.WebRequest.GetResponse%2A> internetowego, wywołując metodę w **WebRequest**. **Metoda GetResponse** konstruuje żądanie specyficzne dla protokołu z właściwości **WebRequest**, sprawia, że TCP lub UDP gniazdo połączenia z serwerem i wysyła żądanie. W przypadku żądań, które wysyłają dane do serwera, takich <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> jak http **post** lub ftp **put** żądań, metoda zapewnia strumień sieciowy, w którym do wysyłania danych.  
  
 **Metoda GetResponse** zwraca **webresponse** specyficzne dla protokołu, który pasuje **do WebRequest.**  
  
 **Klasa WebResponse** jest również klasą abstrakcyjną, która definiuje właściwości i metody, które są dostępne dla wszystkich aplikacji korzystających z protokołów podłączanych. **Elementy podrzędne WebResponse** implementują te właściwości i metody dla protokołu źródłowego. Klasa, <xref:System.Net.HttpWebResponse> na przykład, implementuje **WebResponse** klasy http.  
  
 Dane zwracane przez serwer są prezentowane do aplikacji <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> w strumieniu zwrócone przez metodę. Można użyć tego strumienia, jak każdy inny, jak pokazano w poniższym przykładzie.  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie dla sieci w programie .NET Framework](index.md)
- [Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
