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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c512f03cd3c0cfc4463e54538f12898fbbf45f7e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090347"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a>Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność
Aby upewnić się, że najnowsza zawartość jest zwracana do aplikacji klienckiej, interakcji klienta pamięci podręcznej zasad serwera ponownego sprawdzania poprawności wymagań i zawsze skutkuje najbardziej umiarkowaną zasad pamięci podręcznej. Wszystkie przykłady w tym temacie ilustrują zasad pamięci podręcznej na zasób, który jest buforowany w dniu 1 stycznia i wygasa w dniu 4 stycznia.  
  
 W poniższych przykładach, wartość maksymalna nieaktualność (`maxStale`) jest używany w połączeniu z maksymalny wiek (`maxAge`):  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 5 dni, a nie określa `maxStale` wartość, zgodnie z `maxAge` wartości, zawartość będzie można używać do momentu 6 stycznia. Jednak zgodnie z wymaganiami ponownego sprawdzania poprawności serwera, treść wygasa w dniu 4 stycznia. Ponieważ daty wygaśnięcia zawartości jest bardziej konserwatywnego (wcześniej), ma pierwszeństwo przed `maxAge` zasad. W związku z tym zawartość wygasa w dniu 4 stycznia i musi zostać ponownie sprawdzić poprawności nazwy, nawet jeśli nie został osiągnięty maksymalny wiek.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 5 dni i `maxStale` = 3 dni, zgodnie z opisem w `maxAge` wartości, zawartość będzie można używać do momentu 6 stycznia. Zgodnie z opisem w `maxStale` wartości, zawartość będzie można używać do 7 stycznia. W związku z tym zawartość pobiera sprawdzony ponownie na 6 stycznia.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 5 dni i `maxStale` = 1 dzień, zgodnie z opisem w `maxAge` wartości, zawartość będzie można używać do momentu 6 stycznia. Zgodnie z opisem w `maxStale` wartości, zawartość będzie można używać do 5 stycznia. W związku z tym zawartość zostanie sprawdzony ponownie na 5 stycznia.  
  
 Gdy maksymalny wiek jest wcześniejsza niż data wygaśnięcia zawartości, bardziej konserwatywnego zachowanie buforowania zawsze istniejącej, a wartość maksymalna nieaktualność nie ma wpływu. Poniższe przykłady ilustrują wpływu ustawienia Maksymalna nieaktualność (`maxStale`) wartość, gdy maksymalny wiek (`maxAge`) zostanie osiągnięty zanim wygaśnięcia zawartości:  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 1 dzień, a nie określa wartość dla `maxStale` wartości, zawartość jest ponownie sprawdzić poprawności nazwy 2 stycznia, nawet jeśli nie wygasł.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 1 dzień i `maxStale` = 3 dni, zawartość jest ponownie sprawdzić poprawności nazwy 2 stycznia do wymuszania bardziej konserwatywnego ustawienie zasad.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 1 dzień i `maxStale` = 1 dzień, zawartość jest ponownie sprawdzić poprawności nazwy 2 stycznia.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)  
 [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
