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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d24fa2ece34d20a3d9e8d6f971eebae5da0f496e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198088"
---
# <a name="time-based-cache-policies"></a>Zasady pamięci podręcznej oparte na czasie
Zasady pamięci podręcznej na podstawie czasu definiuje aktualność pozycji z pamięci podręcznej przy użyciu czas pobrania zasobu nagłówki zwrócony z zasobem, a bieżąca godzina. Podczas ustawiania zasad pamięci podręcznej na podstawie czasu, można użyć <xref:System.Net.Cache.HttpRequestCacheLevel.Default> oparte na czasie zasady lub tworzenie niestandardowych zasad opartych na czasie. W przypadku używania zasad na podstawie czasu domyślnego dla zasobów pobranych przy użyciu protokołu HTTP (Hypertext Transfer), zachowanie dokładnie pamięci podręcznej jest określana przez nagłówki dołączone w odpowiedzi z pamięci podręcznej i zachowań określonych w sekcjach 13 i 14 dokumencie RFC 2616 dostępne pod adresem [ http://www.ietf.org ](http://www.ietf.org/). Aby uzyskać przykładowy kod, który demonstruje, ustawiania zasad na podstawie czasu domyślnego dla zasobów HTTP, zobacz [porady: Określanie zasad pamięci podręcznej Default Time-Based aplikacji](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md). Aby uzyskać przykłady kodu, które pokazują tworzenie i używanie zasad buforowania, zobacz [Konfigurowanie buforowanie w aplikacjach sieci](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Kryteria, aby określić świeżości pozycji z pamięci podręcznej  
 Dostosowywanie zasad pamięci podręcznej na podstawie czasu, można określić, że co najmniej jeden z następujących kryteriów umożliwiają określenia aktualność pozycji z pamięci podręcznej:  
  
-   Maksymalny wiek  
  
-   Maksymalna nieaktualność  
  
-   Minimalna świeżość  
  
-   Data synchronizacji pamięci podręcznej  
  
> [!NOTE]
>  Za pomocą zasad pamięci podręcznej na podstawie czasu domyślnego nie należy mylić z ustawienie domyślnych zasad pamięci podręcznej dla aplikacji. Domyślne zasady oparte na czasie jest określonych zasad, które mogą być używane na poziomie żądania lub aplikacji. Domyślne zasady pamięci podręcznej dla aplikacji jest zasady (na podstawie lokalizacji lub na podstawie czasu), które działa, gdy żądania są ustawione żadne zasady. Aby uzyskać więcej informacji na temat ustawiania domyślnych zasad pamięci podręcznej dla aplikacji, zobacz <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.  
  
### <a name="maximum-age"></a>Maksymalny wiek  
 Maksymalny wiek kryterium zasad określa ilość czasu, może być używane w pamięci podręcznej kopię zasobu. Jeśli pamięci podręcznej kopię zasobu jest starsza niż określony czas, zasobu musi mieć przywróconą ważność, sprawdzając względem zawartości na serwerze. Jeśli maksymalny wiek pozwoliłoby zasobu, który ma być używany, gdy wygaśnie, tych kryteriów nie jest honorowane, chyba że zostanie także podana wartość maksymalna nieaktualność.  
  
### <a name="maximum-staleness"></a>Maksymalna nieaktualność  
 Maksymalna nieaktualność kryterium zasad określa czas, po wygaśnięciu zawartości pamięci podręcznej kopię zasobu może służyć. Jest to tylko kryterium zasad pamięci podręcznej, które pozwala na zasoby, które ma być używany, gdy już wygasną.  
  
### <a name="minimum-freshness"></a>Minimalna świeżość  
 Minimalna świeżość kryterium zasad określa czas wygaśnięcia zawartości pamięci podręcznej kopię zasobu może służyć. Ta zasada obowiązuje stanie sprawić, że wpis pamięci podręcznej wygaśnie przed datą wygaśnięcia; w związku z tym ustawienia Maksymalna nieaktualność i minimalna świeżość wzajemnie się wykluczają.  
  
## <a name="cache-synchronization-date"></a>Data synchronizacji pamięci podręcznej  
 Kryterium zasad pamięci podręcznej synchronizacji daty Określa, kiedy w pamięci podręcznej kopię zasobu musi mieć przywróconą ważność przez zaewidencjonowanie go w zawartości na serwerze. Jeśli zawartość została zmieniona, ponieważ element był buforowany, pobrany z serwera, przechowywane w pamięci podręcznej i zwrócone do aplikacji. Jeśli zawartość nie została zmieniona, jego sygnatura czasowa jest aktualizowana, a aplikacja pobiera zawartość z pamięci podręcznej.  
  
 Data synchronizacji pamięci podręcznej umożliwia określenie Data bezwzględna po zawartości z pamięci podręcznej musi być sprawdzony ponownie. Jeśli wpis świeża pamięć podręczna ostatnich został sprawdzony ponownie przed datą synchronizacji pamięci podręcznej, ponownego sprawdzania poprawności na serwerze jest nadal występuje. Jeśli wpis pamięci podręcznej został sprawdzony ponownie po dacie synchronizacji pamięci podręcznej, nie ma żadnych dodatkowych świeżości lub wymagania ponowną weryfikację serwera, które unieważniają wpisu pamięci podręcznej zapisu z pamięci podręcznej jest używany. Data synchronizacji pamięci podręcznej jest ustawiony na datę wypadającą w przyszłości, wpis jest sprawdzony ponownie za każdym razem, gdy żądanie, dopóki nie przekazuje Data synchronizacji pamięci podręcznej.  
  
 Informacje o skutkach łączenia kryteriów zasad pamięci podręcznej na podstawie czasu można znaleźć w następujących tematach:  
  
-   [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)  
 [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching — >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
