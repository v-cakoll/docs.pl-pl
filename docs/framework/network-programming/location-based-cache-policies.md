---
title: Zasady pamięci podręcznej oparte na lokalizacji
ms.date: 03/30/2017
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0344bbfc02a66a6f2ec9dace126bfae6811860be
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176506"
---
# <a name="location-based-cache-policies"></a>Zasady pamięci podręcznej oparte na lokalizacji
Zasady pamięci podręcznej na podstawie lokalizacji definiuje aktualność prawidłowe pamięci podręcznej wpisy podstawę, z którego można pobrać żądanego zasobu. Zasób pamięci podręcznej jest nieprawidłowa w przypadku korzystania z niego nie naruszają określony serwer ponownego sprawdzania poprawności wymagań. Zasady oparte na lokalizacji pamięci podręcznej jest tworzona programowo przy użyciu <xref:System.Net.Cache.RequestCachePolicy> lub <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktora klasy. Typ zasad na podstawie lokalizacji jest przekazywana do konstruktora przy użyciu <xref:System.Net.Cache.RequestCacheLevel> lub <xref:System.Net.Cache.HttpRequestCacheLevel> wartość wyliczenia. Aby uzyskać przykłady kodu, które utworzyć zasady oparte na lokalizacji pamięci podręcznej, zobacz [porady: Określanie zasad pamięci podręcznej na podstawie lokalizacji dla aplikacji](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md). W poniższych sekcjach opisano każdego typu zasad na podstawie lokalizacji pamięci podręcznej dla zasobów Hypertext Transfer Protocol (protokół http i https).  
  
## <a name="cache-if-available-policy"></a>Jeśli jest dostępna w pamięci podręcznej zasad  
 Jeśli w lokalnej pamięci podręcznej prawidłowe żądanego zasobu, zasób pamięci podręcznej jest używany; w przeciwnym razie żądanie dla zasobu są wysyłane do serwera. Jeśli żądany zasób jest dostępny w dowolnym pamięci podręcznej między klientem a serwerem, żądania mogą być spełnione przez pośrednich pamięci podręcznej.  
  
## <a name="cache-only-policy"></a>Zasad wymagających używania tylko pamięci podręcznej  
 Jeśli prawidłowy żądany zasób znajduje się w lokalnej pamięci podręcznej, jest używany zasób pamięci podręcznej. Jeśli nie określono tego poziomu zasad pamięci podręcznej, <xref:System.Net.WebException> wyjątek jest generowany, jeśli element nie znajduje się w lokalnej pamięci podręcznej.  
  
## <a name="cache-or-next-cache-only-policy"></a>W pamięci podręcznej, lub obok pamięci podręcznej tylko zasad  
 Jeśli prawidłowy żądany zasób znajduje się w lokalnej pamięci podręcznej lub pośredniego pamięci podręcznej w sieci lokalnej, zasób pamięci podręcznej jest używany. W przeciwnym razie <xref:System.Net.WebException> jest zgłaszany wyjątek. W protokole HTTP, Protokół buforowania jest to osiągane przy użyciu dyrektywy sterowania tylko jeśli-zapisanych w pamięci podręcznej z pamięci podręcznej.  
  
## <a name="no-cache-no-store-policy"></a>Brak Brak pamięci podręcznej Store zasad  
 Żądany zasób nie jest nigdy używane z dowolnym pamięci podręcznej i nigdy nie znajduje się w dowolnym pamięci podręcznej. Jeśli żądany zasób znajduje się w lokalnej pamięci podręcznej, zostaną usunięte. Ten poziom zasad wskazuje celu pośrednich pamięci podręcznych, należy również usunąć zasób. W protokole HTTP, Protokół buforowania jest to osiągane przy użyciu dyrektywy kontroli pamięci podręcznej nie-store.  
  
## <a name="refresh-policy"></a>Odświeżanie zasad  
 Żądany zasób może służyć, jeśli zostanie uzyskany z serwera lub znalezionych w pamięci podręcznej w innych niż lokalnej pamięci podręcznej. Zanim żądanie może być spełnione przez pośrednich pamięci podręcznej, czy pamięć podręczna musi przechowywać jego wpis pamięci podręcznej z serwerem. W protokole HTTP, Protokół buforowania, jest to osiągane przy użyciu max-age = dyrektywa kontroli pamięci podręcznej 0 i nagłówek dyrektywy nie-cache.  
  
## <a name="reload-policy"></a>Załaduj ponownie zasad  
 Żądanych zasobów musi pochodzić z serwera. Odpowiedzi mogą zostać zapisane w lokalnej pamięci podręcznej. W protokole HTTP, Protokół buforowania można to osiągnąć przy użyciu dyrektywy sterowania nie pamięci podręcznej w pamięci podręcznej i nagłówek dyrektywy nie-cache.  
  
## <a name="revalidate-policy"></a>Ponownie sprawdź poprawność zasad  
 Porównuje kopię zasobu w pamięci podręcznej z kopią na serwerze. Jeśli kopią na serwerze jest nowszy, jest on używany do spełnienia żądania i zastępuje kopię w pamięci podręcznej. Jeśli kopia w pamięci podręcznej jest taka sama jak kopii serwerowej, buforowana kopia jest używany. W protokole HTTP, Protokół buforowania można to osiągnąć za pomocą warunkowego żądania.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)  
 [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching — >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
