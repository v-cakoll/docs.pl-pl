---
title: Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość
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
ms.openlocfilehash: d5d368ac282eef8c29729f110d6d5f97b1479b47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538924"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość
Aby upewnić się, że najnowsza zawartość jest zwracana do aplikacji klienckiej, interakcji klienta pamięci podręcznej zasad serwera ponownego sprawdzania poprawności wymagań i zawsze skutkuje najbardziej umiarkowaną zasad pamięci podręcznej. Wszystkie przykłady w tym temacie ilustrują zasad pamięci podręcznej na zasób, który jest buforowany w dniu 1 stycznia i wygasa w dniu 4 stycznia.  
  
 Poniższe przykłady ilustrują zasad pamięci podręcznej, która wynika z interakcji maksymalny wiek (`maxAge`) i minimalna świeżość (`minFresh`) wartości.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 2 dni i `minFresh` nie zostanie określony, zawartość jest ponownie zatwierdzone na 3 stycznia.  
  
-   Jeśli ustawia zasady pamięci podręcznej `maxAge` = 2 dni i `minFresh` = 1 dzień, zgodnie z opisem w `maxAge`, aż do 3 stycznia od nowa jest zawartość. Zgodnie z opisem w `minFresh`, aż do 3 stycznia od nowa jest zawartość. W związku z tym należy ponownie zatwierdzone zawartości, na 3 stycznia.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 2 dni i `minFresh` = 2 dni zgodnie z opisem w `maxAge`, aż do 3 stycznia od nowa jest zawartość. Zgodnie z opisem w `minFresh` zawartość jest świeże aż do 2 stycznia. W związku z tym zawartość musi być sprawdzony ponownie 2 stycznia.  
  
## <a name="see-also"></a>Zobacz także
- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
