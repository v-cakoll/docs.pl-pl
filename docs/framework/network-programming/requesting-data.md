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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047314"
---
# <a name="requesting-data"></a>Żądanie danych
Tworzenie aplikacji działających w rozproszonym środowisku operacyjnym dzisiejszej sieci Internet wymaga wydajnej, łatwej w użyciu metody do pobierania danych z zasobów wszystkich typów. Protokoły podłączane umożliwiają tworzenie aplikacji korzystających z jednego interfejsu do pobierania danych z wielu protokołów internetowych.  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>Przekazywanie i pobieranie danych z serwera internetowego  
 W przypadku prostych transakcji <xref:System.Net.WebClient> żądań i odpowiedzi Klasa zapewnia najłatwą metodę przekazywania danych do lub pobierania danych z serwera internetowego. **Klient WebClient** oferuje metody przekazywania i pobierania plików, wysyłania i otrzymywania strumieni oraz wysyłania bufora danych do serwera i otrzymywania odpowiedzi. **Klient WebClient** używa <xref:System.Net.WebRequest> klas <xref:System.Net.WebResponse> i, aby nawiązać rzeczywiste połączenia z zasobem internetowym, tak aby wszystkie zarejestrowane protokoły podłączane były dostępne do użycia.  
  
 Aplikacje klienckie, które muszą wykonywać bardziej złożone transakcje żądania danych z serwerów przy użyciu klasy **WebRequest** i jej obiektów podrzędnych. **Żądanie WebRequest** hermetyzuje szczegóły dotyczące łączenia się z serwerem, wysyłania żądania i otrzymywania odpowiedzi. **WebRequest** to Klasa abstrakcyjna, która definiuje zestaw właściwości i metod, które są dostępne dla wszystkich aplikacji, które korzystają z protokołów podłączanych. Elementy podrzędne **żądania WebRequest**, takie jak <xref:System.Net.HttpWebRequest>, implementują właściwości i metody zdefiniowane przez **WebRequest** w sposób, który jest zgodny z bazowym protokołem.  
  
 Klasa **WebRequest** tworzy wystąpienia obiektów podrzędnych **żądania WebRequest** zależnych od protokołu przy użyciu wartości identyfikatora URI <xref:System.Net.WebRequest.Create%2A> przesłanej do metody, aby określić konkretne wystąpienie klasy pochodnej do utworzenia. Aplikacje wskazują, które elementy podrzędne **żądania WebRequest** mają być używane do obsługi żądania przez zarejestrowanie konstruktora elementu podrzędnego za pomocą <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody.  
  
 Do zasobu internetowego jest wykonywane żądanie wywołujące <xref:System.Net.WebRequest.GetResponse%2A> metodę w **żądaniu WebRequest**. Metoda **GetResponse** konstruuje żądanie specyficzne dla protokołu ze wszystkich właściwości **żądania WebRequest**, sprawia, że połączenie TCP lub UDP gniazda z serwerem i wysyła żądanie. W przypadku żądań wysyłających dane do serwera, takich jak <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> żądania HTTP **post** lub FTP **Put** , Metoda zawiera strumień sieciowy, do którego mają być wysyłane dane.  
  
 Metoda **GetResponse** zwraca **WebResponse** specyficzny dla protokołu, który jest zgodny z **żądaniem WebRequest.**  
  
 Klasa **WebResponse** jest również klasą abstrakcyjną, która definiuje właściwości i metody, które są dostępne dla wszystkich aplikacji, które korzystają z protokołów podłączanych. Elementy podrzędne **WebResponse** implementują te właściwości i metody dla bazowego protokołu. Klasa, na przykład implementuje klasę WebResponse dla protokołu HTTP. <xref:System.Net.HttpWebResponse>  
  
 Dane zwrócone przez serwer są prezentowane aplikacji w strumieniu zwracanym przez <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodę. Tego strumienia można użyć jak dowolnego innego, jak pokazano w poniższym przykładzie.  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie dla sieci w programie .NET Framework](index.md)
- [Instrukcje: Zażądaj strony sieci Web i Pobierz wyniki jako strumień](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [Instrukcje: Pobieranie WebResponse specyficznych dla protokołu, które pasują do żądania sieci](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
