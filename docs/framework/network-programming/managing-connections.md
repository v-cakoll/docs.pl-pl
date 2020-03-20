---
title: Zarządzanie połączeniami
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
ms.openlocfilehash: 11c17c6893800fce8bbff8f49b3a207c161bcdfa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047649"
---
# <a name="managing-connections"></a>Zarządzanie połączeniami
Aplikacje, które używają protokołu HTTP do łączenia <xref:System.Net.ServicePoint> się <xref:System.Net.ServicePointManager> z zasobami danych, mogą używać programów i klas programu .NET Framework do zarządzania połączeniami z Internetem i pomagania im w osiągnięciu optymalnej skali i wydajności.  
  
 **ServicePoint** Klasa udostępnia aplikacji z punktu końcowego, do którego aplikacja może łączyć się z dostępem do zasobów internetowych. Każdy **program ServicePoint** zawiera informacje ułatwiające optymalizację połączeń z serwerem internetowym przez udostępnianie informacji o optymalizacji między połączeniami w celu zwiększenia wydajności.  
  
 Każdy **ServicePoint** jest identyfikowany przez jednolity identyfikator zasobu (URI) i jest klasyfikowany zgodnie z identyfikatorem schematu i fragmentami hosta identyfikatora URI. Na przykład to samo **wystąpienie programu ServicePoint** `http://www.contoso.com/index.htm` dostarczałoby żądań do identyfikatorów URI i `http://www.contoso.com/news.htm?date=today` ponieważ`www.contoso.com`mają one ten sam identyfikator schematu (http) i fragmenty hosta ( ). Jeśli aplikacja ma już trwałe połączenie `www.contoso.com`z serwerem, używa tego połączenia do pobierania obu żądań, unikając konieczności tworzenia dwóch połączeń.  
  
 **ServicePointManager** jest klasą statyczną, która zarządza tworzeniem i niszczeniem wystąpień **programu ServicePoint.** **ServicePointManager** tworzy **ServicePoint,** gdy aplikacja żąda zasobu internetowego, który nie znajduje się w kolekcji istniejących wystąpień **programu ServicePoint.** **Wystąpienia programu ServicePoint** są niszczone po przekroczeniu maksymalnego czasu bezczynności lub gdy liczba istniejących wystąpień **programu ServicePoint** przekracza maksymalną liczbę wystąpień **programu ServicePoint** dla aplikacji. Można kontrolować zarówno domyślny maksymalny czas bezczynności, jak i maksymalną <xref:System.Net.ServicePointManager.MaxServicePoints%2A> liczbę wystąpień **programu ServicePoint,** ustawiając <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> właściwości programu **ServicePointManager**.  
  
 Liczba połączeń między klientem a serwerem może mieć dramatyczny wpływ na przepływność aplikacji. Domyślnie aplikacja używająca <xref:System.Net.HttpWebRequest> klasy używa maksymalnie dwóch połączeń trwałych do danego serwera, ale można ustawić maksymalną liczbę połączeń dla danej aplikacji.  
  
> [!NOTE]
> Specyfikacja HTTP/1.1 ogranicza liczbę połączeń z aplikacji do dwóch połączeń na serwer.  
  
 Optymalna liczba połączeń zależy od rzeczywistych warunków, w których aplikacja jest uruchamiana. Zwiększenie liczby połączeń dostępnych dla aplikacji może nie wpłynąć na wydajność aplikacji. Aby określić wpływ większej liczby połączeń, należy przeprowadzić testy wydajności, zmieniając liczbę połączeń. Można zmienić liczbę połączeń, które aplikacja używa, zmieniając <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> właściwość statyczną w **ServicePointManager** klasy podczas inicjowania aplikacji, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 Zmiana właściwości **ServicePointManager.DefaultConnectionLimit** nie ma wpływu na wcześniej zainicjowane wystąpienia **programu ServicePoint.** Poniższy kod pokazuje zmianę limitu połączeń w istniejącym `http://www.contoso.com` programie **ServicePoint** dla serwera na wartość przechowywaną w `newLimit`programie .  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Grupowanie połączeń](connection-grouping.md)
- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
