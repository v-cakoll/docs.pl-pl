---
title: Zarządzanie pamięcią podręczną dla aplikacji sieciowych
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 265b4e451ebb76dbabe0d3e0df065504a3891f32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033166"
---
# <a name="cache-management-for-network-applications"></a>Zarządzanie pamięcią podręczną dla aplikacji sieciowych
Ten temat i jego powiązane tematy podrzędne opisują, buforowania dla zasobów pobranych przy użyciu <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, i <xref:System.Net.FtpWebRequest> klasy.  
  
 Pamięć podręczna udostępnia magazyn tymczasowy zasobów, które zostały żądane przez aplikację. Jeśli aplikacja żąda tego samego zasobu więcej niż jeden raz, zasobu mogą być zwracane z pamięci podręcznej, unikając konieczności ponownie żąda od serwera. Buforowanie może poprawić wydajność aplikacji, skracając czas potrzebny na żądany zasób. Buforowanie można także zmniejszyć ruch w sieci dzięki zmniejszeniu liczby rund do serwera. Gdy pamięć podręczna zwiększa wydajność, zwiększa się ryzyko, że zasób powrót do aplikacji jest nieodświeżona, co oznacza, że nie jest taka sama jak zasób, który będzie została wysłana przez serwer pamięci podręcznej nie były używane.  
  
 Buforowanie może umożliwić nieautoryzowanych użytkowników lub procesy, które można odczytać danych poufnych. Uwierzytelniony odpowiedź, która jest buforowana może pobrać z pamięci podręcznej bez autoryzacji dodatkowe. Jeśli włączone jest buforowanie, zmień <xref:System.Net.WebRequest.CachePolicy%2A> do <xref:System.Net.Cache.RequestCacheLevel.BypassCache> lub <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> wyłączenie buforowania dla tego żądania.  
  
 Ze względów bezpieczeństwa buforowanie jest **nie** zalecane w przypadku scenariuszy warstwy środkowej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)  
 Wyjaśnia, jakie zasady pamięci podręcznej jest i jak zdefiniować jedną.  
  
 [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 Definiuje każdego typu zasad na podstawie lokalizacji pamięci podręcznej dostępne dla zasobów Hypertext Transfer Protocol (protokół http i https).  
  
 [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 W tym artykule opisano kryteria, które można dostosować zasady na podstawie czasu pamięci podręcznej.  
  
 [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 W tym artykule opisano, jak programowo utworzyć zasady pamięci podręcznej i żądania, które używają pamięci podręcznej.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Net.Cache>  
 Określa typy i wyliczenia używane do definiowania zasad buforowania dla zasobów pobranych przy użyciu <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, i <xref:System.Net.FtpWebRequest> klasy.
