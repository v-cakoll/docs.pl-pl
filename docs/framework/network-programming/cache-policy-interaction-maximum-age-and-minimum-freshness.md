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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048819"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość
Aby zapewnić, że najnowsza zawartość jest zwracana do aplikacji klienckiej, interakcja z zasadami pamięci podręcznej klienta i wymagania dotyczące ponownego sprawdzania poprawności serwera zawsze będą mieć najważniejsze zasady pamięci podręcznej. We wszystkich przykładach w tym temacie przedstawiono zasady pamięci podręcznej dla zasobu, który jest buforowany 1 stycznia i wygasa 4 stycznia.  
  
 Poniższe przykłady ilustrują zasady pamięci podręcznej, które wynikają z interakcji maksymalnego wieku`maxAge`() i minimalnej wartości Aktualności`minFresh`().  
  
- Jeśli zestawy `maxAge` zasad pamięci podręcznej = 2 `minFresh` dni i nie są określone, zawartość zostanie ponownie sprawdzona w dniu 3 stycznia.  
  
- Jeśli zasady pamięci podręcznej są ustawione `maxAge` na 2 dni i `minFresh` = 1 `maxAge`dzień, zgodnie z, zawartość jest odświeżana do 3 stycznia. Zgodnie z, zawartość jest odświeżana do 3 stycznia. `minFresh` W związku z tym należy ponownie sprawdzić zawartość w dniu 3 stycznia.  
  
- Jeśli zasady pamięci podręcznej są ustawione `maxAge` na 2 dni i `minFresh` = 2 dni zgodnie `maxAge`z, zawartość jest odświeżana do 3 stycznia. `minFresh` Zgodnie z zawartością jest świeża do 2 stycznia. W związku z tym zawartość musi zostać ponownie sprawdzona w dniu 2 stycznia.  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](configuring-caching-in-network-applications.md)
- [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
