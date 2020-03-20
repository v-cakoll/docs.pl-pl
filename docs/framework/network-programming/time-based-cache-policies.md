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
ms.openlocfilehash: 0edde8e716d5ce3b1444e994234def5835341475
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047126"
---
# <a name="time-based-cache-policies"></a>Zasady pamięci podręcznej oparte na czasie
Zasady pamięci podręcznej oparte na czasie definiuje świeżość wpisów w pamięci podręcznej przy użyciu czasu, w której zasób został pobrany, nagłówki zwrócone z zasobem i bieżący czas. Podczas ustawiania zasad pamięci podręcznej opartych <xref:System.Net.Cache.HttpRequestCacheLevel.Default> na czasie można użyć zasad opartych na czasie lub utworzyć dostosowane zasady oparte na czasie. W przypadku korzystania z domyślnych zasad opartych na czasie dla zasobów uzyskanych przy użyciu protokołu HTTP (Hypertext Transfer Protocol) dokładne zachowanie pamięci podręcznej zależy od nagłówków zawartych w buforowanej odpowiedzi oraz zachowań określonych w sekcjach 13 i 14 RFC 2616, dostępnych w witrynie [internetowej Internet Engineering Task Force (IETF).](https://www.ietf.org/) Przykładowy kod przedstawiający ustawienie domyślnej zasady opartej na czasie dla zasobów HTTP można znaleźć w temacie [Jak: Ustawianie domyślnych zasad pamięci podręcznej opartych na czasie dla aplikacji](how-to-set-the-default-time-based-cache-policy-for-an-application.md). Aby zapoznać się z przykładami kodu, które pokazują tworzenie i używanie zasad pamięci podręcznej, zobacz [Konfigurowanie buforowania w aplikacjach sieciowych](configuring-caching-in-network-applications.md).  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Kryteria określania świeżości wpisów buforowanych  
 Aby dostosować zasady pamięci podręcznej oparte na czasie, można określić, że co najmniej jedno z następujących kryteriów ma być używane do określania świeżości wpisów w pamięci podręcznej:  
  
- Maksymalny wiek  
  
- Maksymalna nieaktualność  
  
- Minimalna świeżość  
  
- Data synchronizacji pamięci podręcznej  
  
> [!NOTE]
> Przy użyciu domyślnych zasad pamięci podręcznej opartych na czasie nie należy mylić z ustawieniem domyślnej zasady pamięci podręcznej dla aplikacji. Domyślna zasada oparta na czasie to określona zasada, która może być używana na poziomie żądania lub aplikacji. Domyślne zasady pamięci podręcznej dla aplikacji to zasady (oparte na lokalizacji lub oparte na czasie), które są obowiązywać, gdy nie ustawiono żadnych zasad w żądaniu. Aby uzyskać szczegółowe informacje na temat ustawiania domyślnych zasad pamięci podręcznej dla aplikacji, zobacz <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.  
  
### <a name="maximum-age"></a>Maksymalny wiek  
 Kryterium zasad maksymalnego wieku określa czas, przez jaki może być używana buforowana kopia zasobu. Jeśli buforowana kopia zasobu jest starsza niż określony czas, zasób musi zostać ponownie zweryfikowany, sprawdzając go względem zawartości na serwerze. Jeśli maksymalny wiek pozwoli zasób do użycia po jego wygaśnięciu, kryteria te nie jest honorowane, chyba że określono również maksymalną wartość nieaktualność.  
  
### <a name="maximum-staleness"></a>Maksymalna nieaktualność  
 Kryterium zasad maksymalnego nieaktualności określa czas po wygaśnięciu zawartości, przez który można użyć buforowanej kopii zasobu. Jest to jedyne kryterium zasad pamięci podręcznej, które zezwala na zasoby do użycia po ich wygaśnięciu.  
  
### <a name="minimum-freshness"></a>Minimalna świeżość  
 Kryterium zasad minimalnej świeżości określa czas przed wygaśnięciem zawartości, przez który można użyć buforowanej kopii zasobu. Ta zasada powoduje, że wpis pamięci podręcznej wygaśnie przed datą wygaśnięcia; w związku z tym minimalne ustawienia świeżości i maksymalnego nieaktualności wzajemnie się wykluczają.  
  
## <a name="cache-synchronization-date"></a>Data synchronizacji pamięci podręcznej  
 Kryterium zasad daty synchronizacji pamięci podręcznej określa, kiedy buforowana kopia zasobu musi zostać ponownie zweryfikowana, sprawdzając ją względem zawartości na serwerze. Jeśli zawartość uległa zmianie od czasu buforowania elementu, jest pobierana z serwera, przechowywana w pamięci podręcznej i zwracana do aplikacji. Jeśli zawartość nie uległa zmianie, jej sygnatura czasowa jest aktualizowana, a aplikacja pobiera zawartość w pamięci podręcznej.  
  
 Data synchronizacji pamięci podręcznej umożliwia określenie daty bezwzględnej, gdy zawartość buforowana musi zostać ponownie oceniona. Jeśli nowy wpis pamięci podręcznej został ostatnio ponownie oceniony przed datą synchronizacji pamięci podręcznej, ponowneuwsznajenie wersji z serwerem nadal występuje. Jeśli wpis pamięci podręcznej został ponownie oceniony po dacie synchronizacji pamięci podręcznej i nie ma żadnych dodatkowych wymagań dotyczących świeżości lub ponownego zmieniania ważności serwera, które unieważniają wpis w pamięci podręcznej, jest używany wpis z pamięci podręcznej. Jeśli data synchronizacji pamięci podręcznej jest ustawiona na przyszłą datę, wpis jest ponownie zmieniany za każdym razem, gdy jest wymagany, dopóki nie przejdzie data synchronizacji pamięci podręcznej.  
  
 Następujące tematy zawierają informacje o skutkach łączenia kryteriów zasad pamięci podręcznej opartych na czasie:  
  
- [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność](cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
- [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość](cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
- [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](configuring-caching-in-network-applications.md)
- [\<requestCaching> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
