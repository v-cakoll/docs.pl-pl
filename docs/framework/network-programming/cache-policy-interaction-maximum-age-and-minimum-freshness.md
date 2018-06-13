---
title: Pamięci podręcznej zasad interakcji — maksymalny wiek i świeżości minimalna
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d88ef1e736a16dddf156a1bc0e42f06d128d2c57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394169"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Pamięci podręcznej zasad interakcji — maksymalny wiek i świeżości minimalna
Aby upewnić się, że najnowsza zawartość jest zwracana do aplikacji klienckiej, interakcji klienta pamięci podręcznej zasad serwera ponownego sprawdzania poprawności wymagań i zawsze powoduje najbardziej zachowawcze zasady pamięci podręcznej. Wszystkie przykłady w tym temacie przedstawiono zasady z zasobem, który jest buforowana w dniu 1 stycznia i wygaśnie w dniu 4 stycznia w pamięci podręcznej.  
  
 Poniższe przykłady przedstawiają zasady pamięci podręcznej, będącą wynikiem interakcji maksymalny wiek (`maxAge`) i minimalna świeżości (`minFresh`) wartości.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 2 dni i `minFresh` nie zostanie określony, zawartość jest ponownie sprawdzić poprawności na 3 stycznia.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 2 dni i `minFresh` = 1 dzień, zgodnie z `maxAge`, zawartość jest pierwszą do 3 stycznia. Zgodnie z `minFresh`, aż do 3 stycznia jest nowa zawartość. W związku z tym zawartości musi być sprawdzony ponownie na 3 stycznia.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 2 dni i `minFresh` = 2 dni zgodnie z `maxAge`, zawartość jest pierwszą do 3 stycznia. Zgodnie z `minFresh` do 2 stycznia jest nowa zawartość. W związku z tym zawartości musi być sprawdzony ponownie 2 stycznia.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)  
 [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
