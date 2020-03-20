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
ms.openlocfilehash: e6896452fce89f69b40f1d03332355df72d93211
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047666"
---
# <a name="location-based-cache-policies"></a>Zasady pamięci podręcznej oparte na lokalizacji
Zasady pamięci podręcznej oparte na lokalizacji definiują świeżość prawidłowych wpisów w pamięci podręcznej na podstawie tego, skąd można zabrać żądany zasób. Buforowany zasób jest prawidłowy, jeśli użycie go nie narusza wymagań ponownego walidacji określonych przez serwer. Zasady pamięci podręcznej oparte na lokalizacji są <xref:System.Net.Cache.RequestCachePolicy> <xref:System.Net.Cache.HttpRequestCachePolicy> tworzone programowo przy użyciu konstruktora lub klasy. Typ zasad opartych na lokalizacji jest przekazywany do konstruktora <xref:System.Net.Cache.RequestCacheLevel> przy użyciu wartości lub <xref:System.Net.Cache.HttpRequestCacheLevel> wyliczenia. Aby zapoznać się z przykładami kodu, które tworzą zasady pamięci podręcznej oparte na lokalizacji, zobacz [Jak: Ustawianie zasad pamięci podręcznej opartej na lokalizacji dla aplikacji](how-to-set-a-location-based-cache-policy-for-an-application.md). W poniższych sekcjach wyjaśniono każdy typ zasad pamięci podręcznej opartych na lokalizacji dla zasobów protokołu transferu hipertekstu (http i https).  
  
## <a name="cache-if-available-policy"></a>Zasady pamięci podręcznej, jeśli są dostępne  
 Jeśli prawidłowy żądany zasób znajduje się w lokalnej pamięci podręcznej, używany jest zasób buforowany; w przeciwnym razie żądanie zasobu jest wysyłane do serwera. Jeśli żądany zasób jest dostępny w dowolnej pamięci podręcznej między klientem a serwerem, żądanie może zostać spełnione przez pośrednią pamięć podręczną.  
  
## <a name="cache-only-policy"></a>Zasady tylko do pamięci podręcznej  
 Jeśli prawidłowy żądany zasób znajduje się w lokalnej pamięci podręcznej, używany jest zasób buforowany. Po określeniu tego poziomu <xref:System.Net.WebException> zasad pamięci podręcznej wyjątek jest zgłaszany, jeśli element nie znajduje się w lokalnej pamięci podręcznej.  
  
## <a name="cache-or-next-cache-only-policy"></a>Zasady tylko do pamięci podręcznej lub następnej pamięci podręcznej  
 Jeśli prawidłowy żądany zasób znajduje się w lokalnej pamięci podręcznej lub w pośredniej pamięci podręcznej w sieci lokalnej, używany jest zasób buforowany. W przeciwnym <xref:System.Net.WebException> razie wyjątek. W protokole buforowania HTTP jest to osiągane przy użyciu dyrektywy kontroli pamięci podręcznej only-if-cached.  
  
## <a name="no-cache-no-store-policy"></a>Brak pamięci podręcznej bez zasad sklepu  
 Żądany zasób nigdy nie jest używany z dowolnej pamięci podręcznej i nigdy nie jest umieszczany w żadnej pamięci podręcznej. Jeśli żądany zasób jest obecny w lokalnej pamięci podręcznej, jest usuwany. Ten poziom zasad wskazuje pośrednie pamięci podręczne, które powinny również usunąć zasób. W protokole buforowania HTTP jest to osiągane przy użyciu dyrektywy kontroli pamięci podręcznej bez magazynu.  
  
## <a name="refresh-policy"></a>Zasady odświeżania  
 Żądanego zasobu można użyć, jeśli jest on uzyskiwany z serwera lub znajduje się w pamięci podręcznej innej niż lokalna pamięć podręczna. Zanim żądanie może być spełnione przez pośrednią pamięć podręczną, ta pamięć podręczna musi ponownie ocenić jego buforowany wpis z serwerem. W protokole buforowania HTTP jest to osiągane przy użyciu dyrektywy kontroli max-age = 0 pamięci podręcznej i nagłówka Pragma bez pamięci podręcznej.  
  
## <a name="reload-policy"></a>Zasady ponownego ładowania  
 Żądane zasoby muszą być uzyskane z serwera. Odpowiedź może być zapisana w lokalnej pamięci podręcznej. W protokole buforowania HTTP jest to osiągane przy użyciu dyrektywy kontroli pamięci podręcznej bez pamięci podręcznej i nagłówka Pragma bez pamięci podręcznej.  
  
## <a name="revalidate-policy"></a>Ponowne unieważnienia zasad  
 Porównuje kopię zasobu w pamięci podręcznej z kopią na serwerze. Jeśli kopia na serwerze jest nowsza, jest używana do spełnienia żądania i zastępuje kopię w pamięci podręcznej. Jeśli kopia w pamięci podręcznej jest taka sama jak kopia serwera, używana jest kopia buforowana. W protokole buforowania HTTP jest to osiągane przy użyciu żądania warunkowego.  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](cache-policy.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](configuring-caching-in-network-applications.md)
- [\<requestCaching> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
