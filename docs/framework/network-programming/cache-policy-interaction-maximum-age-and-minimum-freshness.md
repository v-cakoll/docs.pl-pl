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
ms.openlocfilehash: 2ec958cc035ac62086cdd3e2844811accc181d47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048819"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość
Aby upewnić się, że najświeższa zawartość jest zwracana do aplikacji klienckiej, interakcja zasad pamięci podręcznej klienta i wymagania dotyczące ponownego licencjonowania serwera zawsze skutkuje najbardziej konserwatywnymi zasadami pamięci podręcznej. Wszystkie przykłady w tym temacie ilustrują zasady pamięci podręcznej dla zasobu, który jest buforowany w dniu 1 stycznia i wygasa 4 stycznia.  
  
 Poniższe przykłady ilustrują zasady pamięci podręcznej wynikające`maxAge`z interakcji maksymalnego`minFresh`wieku ( ) i minimalnej świeżości ( ) wartości.  
  
- Jeśli zasady pamięci `maxAge` podręcznej ustawia `minFresh` = 2 dni i nie jest określony, zawartość jest ponownie 3 stycznia.  
  
- Jeśli ustawia się `maxAge` zasady pamięci `minFresh` podręcznej = 2 `maxAge`dni i = 1 dzień, zgodnie z , zawartość jest świeża do 3 stycznia. Według `minFresh`, zawartość jest świeża do 3 stycznia. W związku z tym zawartość musi zostać ponownie oceniona w dniu 3 stycznia.  
  
- Jeśli ustawia się `maxAge` zasady pamięci `minFresh` podręcznej = 2 `maxAge`dni i = 2 dni, zgodnie z , zawartość jest świeża do 3 stycznia. Według `minFresh` treści jest świeże do 2 stycznia. W związku z tym zawartość musi zostać ponownie oceniona w dniu 2 stycznia.  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](configuring-caching-in-network-applications.md)
- [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
