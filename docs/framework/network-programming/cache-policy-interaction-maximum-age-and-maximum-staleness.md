---
title: Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
ms.openlocfilehash: e21cfc28407ba67afdce8d72e5e52c12ab359059
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048838"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a>Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność
Aby upewnić się, że najświeższa zawartość jest zwracana do aplikacji klienckiej, interakcja zasad pamięci podręcznej klienta i wymagania dotyczące ponownego licencjonowania serwera zawsze skutkuje najbardziej konserwatywnymi zasadami pamięci podręcznej. Wszystkie przykłady w tym temacie ilustrują zasady pamięci podręcznej dla zasobu, który jest buforowany w dniu 1 stycznia i wygasa 4 stycznia.  
  
 W poniższych przykładach maksymalna wartość`maxStale`nieaktualności ( )`maxAge`jest używana w połączeniu z maksymalnym wiekiem ( ):  
  
- Jeśli zasady pamięci `maxAge` podręcznej ustawia = 5 dni i nie określa `maxStale` wartość, zgodnie z `maxAge` wartością, zawartość jest użyteczna do 6 stycznia. Jednak zgodnie z wymaganiami serwera ponownego ważności zawartość wygasa 4 stycznia. Ponieważ data wygaśnięcia zawartości jest bardziej konserwatywna (wcześniej), ma pierwszeństwo przed zasadami. `maxAge` W związku z tym zawartość wygasa 4 stycznia i musi zostać ponownie przyznana, mimo że jej maksymalny wiek nie został osiągnięty.  
  
- Jeśli ustawienia `maxAge` zasad pamięci podręcznej `maxStale` = 5 dni `maxAge` i = 3 dni, zgodnie z wartością, zawartość może być użytkowana do 6 stycznia. Zgodnie z `maxStale` wartością, zawartość może być użytkowana do 7 stycznia. W związku z tym zawartość zostanie ponownie oceniona 6 stycznia.  
  
- Jeśli zasady pamięci `maxAge` podręcznej ustawia `maxStale` = 5 dni `maxAge` i = 1 dzień, zgodnie z wartością, zawartość jest użyteczna do 6 stycznia. Zgodnie z `maxStale` wartością, zawartość może być użytkowana do 5 stycznia. W związku z tym zawartość zostanie ponownie oceniona 5 stycznia.  
  
 Gdy maksymalny wiek jest mniejszy niż data wygaśnięcia zawartości, zawsze przeważa bardziej konserwatywne zachowanie buforowania, a maksymalna wartość nieaktualności nie ma wpływu. Poniższe przykłady ilustrują efekt ustawienia maksymalnej nieaktualności (`maxStale`) po osiągnięciu maksymalnego wieku (`maxAge`) przed wygaśnięciem zawartości:  
  
- Jeśli zasady pamięci `maxAge` podręcznej ustawia = 1 `maxStale` dzień i nie określa wartość wartości, zawartość jest ponownie zmieniana 2 stycznia, mimo że nie wygasła.  
  
- Jeśli zasady pamięci `maxAge` podręcznej ustawia `maxStale` = 1 dzień i = 3 dni, zawartość jest ponownie wyegzekwowana 2 stycznia, aby wymusić ustawienie zasad bardziej konserwatywne.  
  
- Jeśli zasady pamięci `maxAge` podręcznej ustawia `maxStale` = 1 dzień i = 1 dzień, zawartość jest ponownie w dniu 2 stycznia.  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](configuring-caching-in-network-applications.md)
- [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
