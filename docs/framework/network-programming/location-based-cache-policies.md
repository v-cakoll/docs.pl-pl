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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047666"
---
# <a name="location-based-cache-policies"></a>Zasady pamięci podręcznej oparte na lokalizacji
Zasady pamięci podręcznej oparte na lokalizacji określają świeżość prawidłowych wpisów w pamięci podręcznej na podstawie miejsca, z którego można pobrać żądany zasób. Zasób w pamięci podręcznej jest prawidłowy, jeśli jest używany, nie narusza wymagań związanych z walidacją określonych przez serwer. Zasady pamięci podręcznej oparte na lokalizacji są tworzone programowo przy <xref:System.Net.Cache.RequestCachePolicy> użyciu <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktora klasy lub. Typ zasad opartych na lokalizacji jest przesyłany do konstruktora przy użyciu <xref:System.Net.Cache.RequestCacheLevel> wartości wyliczenia lub. <xref:System.Net.Cache.HttpRequestCacheLevel> Przykłady kodu tworzące zasady pamięci podręcznej oparte na lokalizacji [można znaleźć w temacie How to: Ustawianie zasad pamięci podręcznej na podstawie lokalizacji dla](how-to-set-a-location-based-cache-policy-for-an-application.md)aplikacji. W poniższych sekcjach opisano każdy typ zasad pamięci podręcznej opartych na lokalizacji dla zasobów protokołu HTTP i https.  
  
## <a name="cache-if-available-policy"></a>Buforuj, jeśli są dostępne zasady  
 Jeśli prawidłowy żądany zasób znajduje się w lokalnej pamięci podręcznej, zostanie użyty zasób w pamięci podręcznej. w przeciwnym razie żądanie dotyczące zasobu jest wysyłane do serwera. Jeśli żądany zasób jest dostępny w dowolnej pamięci podręcznej między klientem a serwerem, żądanie może być spełnione przez pośrednią pamięć podręczną.  
  
## <a name="cache-only-policy"></a>Zasady tylko dla pamięci podręcznej  
 Jeśli prawidłowy żądany zasób znajduje się w lokalnej pamięci podręcznej, zostanie użyty buforowany zasób. Gdy zostanie określony ten poziom zasad pamięci podręcznej, zostanie zgłoszony <xref:System.Net.WebException> wyjątek, jeśli element nie znajduje się w lokalnej pamięci podręcznej.  
  
## <a name="cache-or-next-cache-only-policy"></a>Zasady tylko dla pamięci podręcznej lub następnej pamięci podręcznej  
 Jeśli prawidłowy żądany zasób znajduje się w lokalnej pamięci podręcznej lub pośredniej pamięci podręcznej w sieci lokalnej, używany jest buforowany zasób. W przeciwnym razie jest zgłaszany wyjątek.<xref:System.Net.WebException> W protokole buforowania HTTP jest to osiągane przy użyciu dyrektywy kontroli pamięci podręcznej tylko w przypadku buforowania.  
  
## <a name="no-cache-no-store-policy"></a>Brak zasad przechowywania w pamięci podręcznej  
 Żądany zasób nigdy nie jest używany z żadnej pamięci podręcznej i nigdy nie jest umieszczany w żadnej pamięci podręcznej. Jeśli żądany zasób jest obecny w lokalnej pamięci podręcznej, zostanie usunięty. Ten poziom zasad wskazuje pośrednie pamięci podręczne, które powinny również usunąć zasób. W protokole buforowania HTTP można to osiągnąć za pomocą dyrektywy kontroli pamięci podręcznej no-Store.  
  
## <a name="refresh-policy"></a>Odśwież zasady  
 Żądany zasób może być używany, jeśli jest uzyskiwany z serwera lub znajduje się w pamięci podręcznej innej niż lokalna pamięć podręczna. Aby żądanie było spełnione przez pośrednią pamięć podręczną, ta pamięć podręczna musi ponownie sprawdzić jego zbuforowany wpis z serwerem. W protokole buforowania HTTP można to osiągnąć przy użyciu dyrektywy kontroli pamięci podręcznej max-age = 0 i nagłówka pragma Brak pamięci podręcznej.  
  
## <a name="reload-policy"></a>Załaduj ponownie zasady  
 Żądane zasoby muszą zostać uzyskane z serwera. Odpowiedź może zostać zapisana w lokalnej pamięci podręcznej. W protokole buforowania HTTP jest to osiągane przy użyciu dyrektywy kontroli pamięci podręcznej no-cache i nagłówka pragma bez pamięci podręcznej.  
  
## <a name="revalidate-policy"></a>Ponownie Zweryfikuj zasady  
 Porównuje kopię zasobu w pamięci podręcznej z kopią na serwerze. Jeśli kopia na serwerze jest nowsza, jest używana do zaspokojenia żądania i zastępuje kopię w pamięci podręcznej. Jeśli kopia w pamięci podręcznej jest taka sama jak kopia serwera, używana jest kopia w pamięci podręcznej. W protokole buforowania HTTP uzyskuje się to przy użyciu żądania warunkowego.  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](cache-policy.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](configuring-caching-in-network-applications.md)
- [\<requestCaching >, element (Ustawienia sieci)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
