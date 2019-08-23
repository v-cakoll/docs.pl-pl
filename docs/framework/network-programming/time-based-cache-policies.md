---
title: Zasady pamięci podręcznej oparte na czasie
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
ms.openlocfilehash: 1b3e39deca8b483413d2a2c42dbacbf821b3e42e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942374"
---
# <a name="time-based-cache-policies"></a>Zasady pamięci podręcznej oparte na czasie
Zasady pamięci podręcznej oparte na czasie definiują świeżość buforowanych wpisów przy użyciu czasu pobrania zasobu, nagłówki zwrócone z zasobem i bieżący czas. Konfigurując zasady pamięci podręcznej oparte na czasie, można użyć <xref:System.Net.Cache.HttpRequestCacheLevel.Default> zasad czasu lub utworzyć dostosowane zasady czasu. W przypadku korzystania z domyślnych zasad dotyczących czasu dla zasobów uzyskanych przy użyciu protokołu HTTP (Hypertext Transfer Protocol) dokładne zachowanie pamięci podręcznej zależy od nagłówków zawartych w buforowanej odpowiedzi i według zachowań określonych w sekcjach 13 i 14 specyfikacji RFC 2616. dostępne w witrynie [Internet Engineering Task Force (IETF)](https://www.ietf.org/) . Aby zapoznać się z przykładem kodu, który demonstruje Ustawianie domyślnych zasad opartych na czasie dla [zasobów http, zobacz How to: Ustaw domyślne zasady pamięci podręcznej na podstawie czasu dla](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md)aplikacji. Przykłady kodu, które demonstrują tworzenie i Używanie zasad pamięci podręcznej, można znaleźć [w temacie Konfigurowanie buforowania w aplikacjach sieciowych](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Kryteria umożliwiające ustalenie Aktualności buforowanych wpisów  
 Aby dostosować zasady pamięci podręcznej oparte na czasie, można określić, że do określenia Aktualności buforowanych wpisów są używane co najmniej jedno z następujących kryteriów:  
  
- Maksymalny wiek  
  
- Maksymalna nieaktualność  
  
- Minimalna wartość Aktualności  
  
- Data synchronizacji pamięci podręcznej  
  
> [!NOTE]
> Przy użyciu domyślnych zasad pamięci podręcznej nie należy mylić z ustawieniem domyślnych zasad pamięci podręcznej dla aplikacji. Domyślne zasady oparte na czasie są określonymi zasadami, które mogą być używane na poziomie żądania lub aplikacji. Domyślne zasady pamięci podręcznej dla aplikacji to zasady (oparte na lokalizacji lub czasie), które obowiązują, gdy w żądaniu nie ustawiono żadnych zasad. Aby uzyskać szczegółowe informacje na temat ustawiania domyślnych zasad pamięci podręcznej <xref:System.Net.WebRequest.DefaultCachePolicy%2A>dla aplikacji, zobacz.  
  
### <a name="maximum-age"></a>Maksymalny wiek  
 Kryterium maksymalnego okresu ważności określa ilość czasu, przez który można użyć buforowanej kopii zasobu. Jeśli buforowana kopia zasobu jest starsza niż określona ilość czasu, należy ponownie sprawdzić poprawność zasobu, sprawdzając jego zawartość na serwerze. Jeśli maksymalny wiek zezwoli na użycie zasobu po jego wygaśnięciu, te kryteria nie będą honorowane, chyba że zostanie określona maksymalna wartość nieodświeżona.  
  
### <a name="maximum-staleness"></a>Maksymalna nieaktualność  
 Maksymalne kryterium zasad nieodświeżoności określa czas po wygaśnięciu zawartości, która może być używana w pamięci podręcznej. Jest to jedyne kryterium zasad pamięci podręcznej, które zezwala na używanie zasobów po ich wygaśnięciu.  
  
### <a name="minimum-freshness"></a>Minimalna wartość Aktualności  
 Minimalne kryterium zasad Aktualności określa czas przed wygaśnięciem zawartości, która może zostać użyta w pamięci podręcznej. Ta zasada ma wpływ na wygaśnięcie wpisu pamięci podręcznej przed jego datą wygaśnięcia; w związku z tym minimalne ustawienia Aktualności i maksymalnego przestarzałości wykluczają się wzajemnie.  
  
## <a name="cache-synchronization-date"></a>Data synchronizacji pamięci podręcznej  
 Kryterium zasad daty synchronizacji pamięci podręcznej określa, kiedy należy ponownie sprawdzić poprawność kopii zasobu w pamięci podręcznej, sprawdzając ją pod kątem zawartości na serwerze. Jeśli zawartość została zmieniona od momentu zbuforowania elementu, jest pobierana z serwera, przechowywany w pamięci podręcznej i zwracany do aplikacji. Jeśli zawartość nie uległa zmianie, jej sygnatura czasowa jest aktualizowana, a aplikacja pobiera zawartość z pamięci podręcznej.  
  
 Data synchronizacji pamięci podręcznej pozwala określić datę bezwzględną w przypadku konieczności ponownego zweryfikowania zawartości w pamięci podręcznej. Jeśli nowy wpis pamięci podręcznej został ostatnio ponownie sprawdzony przed datą synchronizacji pamięci podręcznej, ponowna Walidacja na serwerze nadal występuje. Jeśli wpis pamięci podręcznej został ponownie zweryfikowany po dacie synchronizacji pamięci podręcznej i nie ma żadnych dodatkowych wymagań dotyczących Aktualności lub ponownego sprawdzania poprawności serwera, który unieważnia wpis w pamięci podręcznej, jest używany wpis z tej pamięci. Jeśli Data synchronizacji pamięci podręcznej jest ustawiona na datę przyszłą, wpis zostanie ponownie zweryfikowany za każdym razem, gdy żądanie zostanie wysłane do momentu, aż upłynie Data synchronizacji pamięci podręcznej.  
  
 Poniższe tematy zawierają informacje dotyczące skutków połączenia kryteriów zasad pamięci podręcznej na podstawie czasu:  
  
- [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
- [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [\<requestCaching >, element (Ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
