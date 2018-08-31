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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 29077a1c0f2b803270adb730e0d810143095e709
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2018
ms.locfileid: "43330883"
---
# <a name="managing-connections"></a>Zarządzanie połączeniami
Aplikacje, które używają protokołu HTTP do łączenia z zasobami danych można używać programu .NET Framework <xref:System.Net.ServicePoint> i <xref:System.Net.ServicePointManager> klasy do zarządzania połączenia z Internetem i aby pomóc im osiągnięcia optymalnej skali i wydajności.  
  
 **ServicePoint** klasa udostępnia aplikacji przy użyciu punktu końcowego, do której aplikacji można podłączyć do dostępu do zasobów internetowych. Każdy **ServicePoint** zawiera informacje, że pomaga zoptymalizować połączenia z serwerem internetowym, udostępniając informacje o optymalizacji między połączeniami, aby zwiększyć wydajność.  
  
 Każdy **ServicePoint** jest określana przez jednolite zasobów identyfikator (URI), a następnie jest dzielony na kategorie zgodnie z fragmentów identyfikator i hosta schemat identyfikatora URI. Na przykład takie same **ServicePoint** wystąpienia zapewni żądań identyfikatory URI `http://www.contoso.com/index.htm` i `http://www.contoso.com/news.htm?date=today` ponieważ mają one ten sam identyfikator schemat (http) i host fragmentów (`www.contoso.com`). Jeśli aplikacja już ma trwałe połączenie z serwerem `www.contoso.com`, używa tego połączenia można pobrać zarówno w przypadku żądań, unikając konieczności tworzenia dwa połączenia.  
  
 **ServicePointManager —** jest klasą statyczną, zarządza tworzeniem i niszczeniem **ServicePoint** wystąpień. **ServicePointManager —** tworzy **ServicePoint** gdy aplikacja żąda zasobu internetowego, który nie znajduje się w kolekcji istniejących **ServicePoint** wystąpienia. **ServicePoint** wystąpienia są niszczone, gdy przekroczyły ich maksymalny czas bezczynności lub liczba istniejących **ServicePoint** wystąpień przekracza maksymalną liczbę **ServicePoint**wystąpień aplikacji. Można kontrolować maksymalny czas bezczynności i maksymalna liczba **ServicePoint** wystąpienia, ustawiając <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> i <xref:System.Net.ServicePointManager.MaxServicePoints%2A> właściwości **ServicePointManager —**.  
  
 Liczba połączeń między klientem i serwerem może mieć znaczący wpływ na przepływność aplikacji. Domyślnie aplikacji za pomocą <xref:System.Net.HttpWebRequest> klasa korzysta z maksymalnie dwóch połączeń trwałych na danym serwerze, ale można ustawić maksymalną liczbę połączeń, na podstawie poszczególnych aplikacji.  
  
> [!NOTE]
>  Specyfikacją HTTP/1.1 ogranicza liczbę połączeń z aplikacji do dwóch połączeń na serwer.  
  
 Optymalną liczbę połączeń, zależy od rzeczywistych warunków, w których jest uruchomiona aplikacja. Zwiększa liczbę połączeń, które są dostępne dla aplikacji może nie mieć wpływ na wydajność aplikacji. Aby określić wpływ więcej połączeń, uruchom testy wydajności różnicując liczbę połączeń. Można zmienić liczbę połączeń używanych przez aplikację, zmieniając statycznej <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> właściwość **ServicePointManager —** klasy podczas inicjowania aplikacji, jak pokazano w następującym przykładzie kodu.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 Zmiana **ServicePointManager.DefaultConnectionLimit** właściwość nie ma wpływu na wcześniej zainicjowane **ServicePoint** wystąpień. Poniższy kod przedstawia zmiany limitu połączeń na istniejącym **ServicePoint** serwera `http://www.contoso.com` na wartość przechowywaną w `newLimit`.  
  
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
 [Grupowanie połączeń](../../../docs/framework/network-programming/connection-grouping.md)  
 [Korzystanie z protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
