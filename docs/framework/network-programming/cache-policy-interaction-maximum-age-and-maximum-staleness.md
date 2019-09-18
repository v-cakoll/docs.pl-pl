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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048838"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a>Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność
Aby zapewnić, że najnowsza zawartość jest zwracana do aplikacji klienckiej, interakcja z zasadami pamięci podręcznej klienta i wymagania dotyczące ponownego sprawdzania poprawności serwera zawsze będą mieć najważniejsze zasady pamięci podręcznej. We wszystkich przykładach w tym temacie przedstawiono zasady pamięci podręcznej dla zasobu, który jest buforowany 1 stycznia i wygasa 4 stycznia.  
  
 W poniższych przykładach maksymalna wartość nieodświeżona (`maxStale`) jest używana w połączeniu z maksymalnym wiekiem (`maxAge`):  
  
- Jeśli zasady pamięci podręcznej są ustawione `maxAge` na 5 dni i nie `maxStale` określają wartości `maxAge` , zgodnie z wartością, zawartość będzie można użyć do 6 stycznia. Jednak zgodnie z wymaganiami dotyczącymi weryfikacji serwera zawartość wygasa 4 stycznia. Ponieważ data wygaśnięcia zawartości jest bardziej ostrożna (wcześniej), ma pierwszeństwo przed `maxAge` zasadami. W związku z tym zawartość wygasa 4 stycznia i należy ponownie sprawdzić poprawność, nawet jeśli nie osiągnięto maksymalnego wieku.  
  
- Jeśli zasady pamięci podręcznej określają `maxAge` 5 dni i `maxStale` = 3 dni `maxAge` , zgodnie z wartością, zawartość będzie można użyć do 6 stycznia. `maxStale` Według wartości, zawartość jest użyteczna do 7 stycznia. W związku z tym zawartość zostanie ponownie sprawdzona w dniu 6 stycznia.  
  
- Jeśli zasady pamięci podręcznej określają `maxAge` 5 dni i `maxStale` = 1 dzień `maxAge` , zgodnie z wartością, zawartość będzie można użyć do 6 stycznia. `maxStale` Według wartości, zawartość jest użyteczna do 5 stycznia. W związku z tym zawartość zostanie ponownie zweryfikowana 5 stycznia.  
  
 Gdy maksymalny wiek jest krótszy niż data wygaśnięcia zawartości, bardziej ostrożne zachowanie buforowania jest zawsze przeważane, a maksymalna wartość starej wartości nie ma żadnego wpływu. Poniższe przykłady ilustrują efekt ustawienia maksymalnej wartości starej (`maxStale`) w przypadku osiągnięcia maksymalnego wieku (`maxAge`) przed wygaśnięciem zawartości:  
  
- Jeśli zasady pamięci podręcznej są ustawione `maxAge` na 1 dzień i nie określają `maxStale` wartości, zawartość jest ponownie weryfikowana w dniu 2 stycznia, nawet jeśli nie wygasła.  
  
- Jeśli zasady pamięci podręcznej określają `maxAge` 1 dzień i `maxStale` = 3 dni, zawartość jest ponownie weryfikowana w dniu 2 stycznia, aby wymusić bardziej niewykonalne ustawienie zasad.  
  
- Jeśli zasady pamięci podręcznej określają `maxAge` 1 dzień i `maxStale` = 1 dzień, zawartość jest ponownie weryfikowana 2 stycznia.  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](configuring-caching-in-network-applications.md)
- [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
