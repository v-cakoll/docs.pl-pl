---
title: "Zasady na podstawie czasu pamięci podręcznej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f712f223ef5787e50ef6a0c26949ff99c13dee33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="time-based-cache-policies"></a>Zasady na podstawie czasu pamięci podręcznej
Zasady na podstawie czasu pamięci podręcznej definiuje świeżości wpisów pamięci podręcznej, za pomocą czas, który został pobrany zasobów, nagłówki zwrócony z zasobem, a bieżącą godziną. Podczas ustawiania zasad na podstawie czasu pamięci podręcznej, można użyć <xref:System.Net.Cache.HttpRequestCacheLevel.Default> oparte na czasie zasady lub tworzenie niestandardowych zasad na podstawie czasu. Używając domyślne zasady na podstawie czasu dla zasobów uzyskany przy użyciu protokołu HTTP (Hypertext Transfer), zachowanie dokładne pamięci podręcznej jest określany przez nagłówki zawarte w buforowanej odpowiedzi i zachowania określone w sekcjach 13 i 14 RFC 2616 dostępne pod adresem [http://www.ietf.org](http://www.ietf.org/). Na przykład kodu pokazuje ustawienie domyślne zasady oparte na czasie HTTP zasobów, zobacz [porady: ustawienie zasad pamięci podręcznej Default Time-Based dla aplikacji](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md). Aby uzyskać przykłady kodu, które przedstawiają Tworzenie zasad i korzystanie z pamięci podręcznej, zobacz [Konfigurowanie buforowanie w aplikacjach sieci](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Kryteria, aby określić świeżości wpisów pamięci podręcznej  
 Aby dostosować zasady na podstawie czasu pamięci podręcznej, można określić co najmniej jedna z następujących kryteriów służyć do określenia świeżości wpisów pamięci podręcznej:  
  
-   Maksymalny wiek  
  
-   Maksymalna nieaktualności  
  
-   Minimalna świeżości  
  
-   Data synchronizacji pamięci podręcznej  
  
> [!NOTE]
>  Za pomocą domyślnych zasad na podstawie czasu pamięci podręcznej nie należy mylić z ustawienia domyślne zasady pamięci podręcznej dla aplikacji. Domyślne zasady oparte na czasie jest określone zasady, które mogą być używane na poziomie żądania lub aplikacji. Domyślne zasady pamięci podręcznej dla aplikacji są to zasady (na podstawie lokalizacji lub na podstawie czasu), które obowiązuje, gdy żadne zasady nie jest ustawiona na żądanie. Aby uzyskać więcej informacji na temat ustawiania domyślnych zasad pamięci podręcznej dla aplikacji, zobacz <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.  
  
### <a name="maximum-age"></a>Maksymalny wiek  
 Maksymalny wiek kryterium zasady określa ilość czasu, można użyć w pamięci podręcznej kopię zasobu. Jeśli buforowaną kopię zasobu jest starsza niż określony czas, zasób musi mieć przywróconą ważność, sprawdzając zawartości na serwerze. Jeśli maksymalny wiek umożliwiałyby zasobów do użycia, gdy wygaśnie, te kryteria. nie jest honorowana, chyba że jest także określona wartość maksymalna nieaktualności.  
  
### <a name="maximum-staleness"></a>Maksymalna nieaktualności  
 Maksymalna nieaktualności kryterium zasad określa czas, po wygaśnięciu zawartości z pamięci podręcznej kopię zasobu można używać. Jest to tylko kryterium pamięci podręcznej zasad zezwala na zasobów do użycia po ich ważność wygasła.  
  
### <a name="minimum-freshness"></a>Minimalna świeżości  
 Minimalna świeżości kryterium zasad określa czas wygaśnięcia zawartości z pamięci podręcznej kopię zasobu można używać. Ta zasada ma wpływ powoduje wpis pamięci podręcznej wygasa przed datą wygaśnięcia; w związku z tym świeżości minimalna i maksymalna nieaktualności ustawienia wzajemnie się wykluczają.  
  
## <a name="cache-synchronization-date"></a>Data synchronizacji pamięci podręcznej  
 Kryterium zasady pamięci podręcznej synchronizacji daty Określa, kiedy w pamięci podręcznej kopię zasobu musi mieć przywróconą ważność przez zaewidencjonowanie go w zawartości na serwerze. Jeśli zawartość została zmieniona, ponieważ element był buforowany, jest pobierany z serwera, przechowywane w pamięci podręcznej i zwrócony do aplikacji. Jeśli zawartość nie została zmieniona, jego sygnatury czasowej jest aktualizowana, a aplikacja pobiera zawartość z pamięci podręcznej.  
  
 Data synchronizacji pamięci podręcznej umożliwia określenie Data bezwzględna, gdy musi ponownie sprawdzić poprawności zawartości z pamięci podręcznej. Jeśli wpis świeża pamięć podręczna ostatnich został sprawdzony ponownie wcześniejsza od daty synchronizacji pamięci podręcznej, ponowna Walidacja z serwerem jest nadal występuje. Jeśli wpis pamięci podręcznej został sprawdzony ponownie po dacie synchronizacji pamięci podręcznej, nie ma żadnych dodatkowych świeżości lub wymagania ponownego sprawdzania poprawności serwera, które unieważnienie buforowany wpis wpis z pamięci podręcznej jest używany. Data synchronizacji pamięci podręcznej zostanie ustawiona na datę w przyszłości, wpis jest sprawdzony ponownie za każdym razem, dopóki nie przekazuje Data synchronizacji pamięci podręcznej.  
  
 Informacje o skutkach łączenia kryteria zasad na podstawie czasu pamięci podręcznej można znaleźć w następujących tematach:  
  
-   [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)  
 [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
