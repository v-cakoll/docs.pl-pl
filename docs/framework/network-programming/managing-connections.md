---
title: Zarządzanie połączeniami
description: Dowiedz się, w jaki sposób aplikacje używające protokołu HTTP dla zasobów danych mogą używać klas .NET Framework ServicePoint i ServicePointManager do zarządzania połączeniami.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, connections
- HTTP, classes for connecting
- requesting data from Internet, connections
- sending data, connections
- receiving data, connections
- ServicePoint class, about ServicePoint class
- response to Internet request, connections
- connections [.NET Framework], classes
- network resources, connections
- downloading Internet resources, connections
- ServicePointManager class, about ServicePointManager class
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
ms.openlocfilehash: 124dff1b104e323b929d13f73cf17d740e747c32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502291"
---
# <a name="managing-connections"></a>Zarządzanie połączeniami
Aplikacje korzystające z protokołu HTTP do łączenia się z zasobami danych mogą używać .NET Framework <xref:System.Net.ServicePoint> i <xref:System.Net.ServicePointManager> klas do zarządzania połączeniami z Internetem, aby ułatwić im osiągnięcie optymalnej skali i wydajności.  
  
 Klasa **ServicePoint** zapewnia aplikację z punktem końcowym, do którego aplikacja może połączyć się z dostępem do zasobów internetowych. Każdy **ServicePoint** zawiera informacje pomagające zoptymalizować połączenia z serwerem internetowym przez udostępnienie informacji o optymalizacji między połączeniami w celu zwiększenia wydajności.  
  
 Każdy **ServicePoint** jest identyfikowany przez Uniform Resource Identifier (URI) i jest kategoryzowany według identyfikatora schematu i fragmentów hosta identyfikatora URI. Na przykład to samo wystąpienie **ServicePoint** będzie dostarczać żądania do identyfikatorów URI `http://www.contoso.com/index.htm` , `http://www.contoso.com/news.htm?date=today` ponieważ mają one ten sam identyfikator schematu (http) i fragmenty hosta ( `www.contoso.com` ). Jeśli aplikacja ma już stałe połączenie z serwerem `www.contoso.com` , używa tego połączenia do pobierania obu żądań, unikając konieczności tworzenia dwóch połączeń.  
  
 **ServicePointManager** jest klasą statyczną, która zarządza tworzeniem i zniszczeniem wystąpień **ServicePoint** . **ServicePointManager** tworzy **ServicePoint** , gdy aplikacja żąda zasobu internetowego, który nie znajduje się w kolekcji istniejących wystąpień **ServicePoint** . Wystąpienia **ServicePoint** są niszczone po przekroczeniu maksymalnego czasu bezczynności lub liczby istniejących wystąpień **ServicePoint** przekraczających maksymalną liczbę wystąpień **ServicePoint** dla aplikacji. Można kontrolować zarówno domyślny maksymalny czas bezczynności, jak i maksymalną liczbę wystąpień **ServicePoint** przez ustawienie <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> <xref:System.Net.ServicePointManager.MaxServicePoints%2A> właściwości i w **ServicePointManager**.  
  
 Liczba połączeń między klientem a serwerem może mieć znaczący wpływ na przepływność aplikacji. Domyślnie aplikacja używająca <xref:System.Net.HttpWebRequest> klasy używa maksymalnie dwóch trwałych połączeń z danym serwerem, ale można ustawić maksymalną liczbę połączeń dla poszczególnych aplikacji.  
  
> [!NOTE]
> Specyfikacja protokołu HTTP/1.1 ogranicza liczbę połączeń z aplikacji do dwóch połączeń na serwer.  
  
 Optymalna liczba połączeń zależy od rzeczywistych warunków, w których działa aplikacja. Zwiększenie liczby połączeń dostępnych dla aplikacji może nie wpływać na wydajność aplikacji. Aby określić wpływ większej liczby połączeń, należy uruchomić testy wydajnościowe, zmieniając liczbę połączeń. Można zmienić liczbę połączeń używanych przez aplikację, zmieniając właściwość statyczną <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> w klasie **ServicePointManager** podczas inicjowania aplikacji, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 Zmiana właściwości **ServicePointManager. DefaultConnectionLimit** nie wpływa na wcześniej zainicjowane wystąpienia **ServicePoint** . Poniższy kod ilustruje zmianę limitu połączeń na istniejącym **ServicePoint** dla serwera `http://www.contoso.com` na wartość przechowywaną w systemie `newLimit` .  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## <a name="see-also"></a>Zobacz także

- [Grupowanie połączeń](connection-grouping.md)
- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
