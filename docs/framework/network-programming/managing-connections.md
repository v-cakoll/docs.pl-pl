---
title: "Zarządzanie połączeniami"
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
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f3a8900aca9ebfa14fbf49d4d3634bc486793c0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="managing-connections"></a>Zarządzanie połączeniami
Aplikacje, które łączą się z zasobami danych przy użyciu protokołu HTTP można używać programu .NET Framework <xref:System.Net.ServicePoint> i <xref:System.Net.ServicePointManager> klasy można zarządzać połączenia z Internetem i pomóc im uzyskać optymalne skalowalność i wydajność.  
  
 **ServicePoint** klasa udostępnia aplikacji z punktem końcowym, z którym aplikacji może nawiązać połączenie dostępu do zasobów Internetu. Każdy **ServicePoint** zawiera informacje, że pomaga zoptymalizować połączenia na internetowym serwerze za pomocą udostępniania informacji optymalizacji między połączenia w celu zwiększenia wydajności.  
  
 Każdy **ServicePoint** są identyfikowane przez zasób identyfikator URI (Uniform) i uporządkowane według fragmenty identyfikator i hosta schemat identyfikatora URI. Na przykład taką **ServicePoint** wystąpienia zapewni żądań http://www.contoso.com/index.htm identyfikatorów URI i http://www.contoso.com/news.htm?date=today, ponieważ mają one tego samego identyfikatora schemat (http) i host fragmenty (www.contoso.com). Jeśli aplikacja już ma trwałe połączenie www.contoso.com serwera, używa tego połączenia do pobrania obu żądania, dzięki czemu nie trzeba tworzyć dwa połączenia.  
  
 **Element ServicePointManager** jest statycznej klasy, która zarządza tworzeniem i zniszczenie **ServicePoint** wystąpień. **ServicePointManager —** tworzy **ServicePoint** gdy aplikacja żąda zasobu internetowego, który nie znajduje się w kolekcji istniejących **ServicePoint** wystąpienia. **ServicePoint** zostaną zniszczone wystąpień, gdy przekraczają maksymalny czas bezczynności lub liczba istniejących **ServicePoint** wystąpień przekracza maksymalną liczbę **ServicePoint**wystąpień dla aplikacji. Użytkownik może kontrolować zarówno maksymalny czas bezczynności i maksymalną liczbę **ServicePoint** wystąpień przez ustawienie <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> i <xref:System.Net.ServicePointManager.MaxServicePoints%2A> właściwości **ServicePointManager —**.  
  
 Liczba połączeń między klientem a serwerem może mieć znaczący wpływ na wydajność aplikacji. Domyślnie aplikacji przy użyciu <xref:System.Net.HttpWebRequest> klasa korzysta z maksymalnie dwóch połączeń trwałych do danego serwera, ale można ustawić maksymalną liczbę połączeń na podstawie określonych aplikacji.  
  
> [!NOTE]
>  Specyfikacja protokołu HTTP/1.1 ogranicza liczbę połączeń z aplikacji do dwóch połączeń na serwer.  
  
 Optymalna liczba połączeń zależy od rzeczywistych warunkach, w których jest uruchomiona aplikacja. Zwiększa liczbę połączeń, które są dostępne dla aplikacji nie mogą wpływać na wydajność aplikacji. Aby określić wpływ więcej połączeń, Uruchamianie testów wydajnościowych różnicując liczbę połączeń. Można zmienić liczbę połączeń używanych przez aplikację, zmieniając statycznych <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> właściwość **ServicePointManager —** klasy w czasie inicjowania aplikacji, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 Zmiana **ServicePointManager.DefaultConnectionLimit** właściwości nie wpływa na wcześniej zainicjowana **ServicePoint** wystąpień. Poniższy kod ilustruje, Zmiana limitu połączeń na istniejącym **ServicePoint** dla http://www.contoso.com serwera do wartości przechowywanej w `newLimit`.  
  
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
 [Grupowanie połączenia](../../../docs/framework/network-programming/connection-grouping.md)  
 [Przy użyciu protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
