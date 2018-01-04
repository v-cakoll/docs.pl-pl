---
title: "Pamięci podręcznej zasad interakcji — maksymalny wiek i nieaktualności maksymalny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2fc28f120b76e51cd285f9b7d6a446f4835113a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a>Pamięci podręcznej zasad interakcji — maksymalny wiek i nieaktualności maksymalny
Aby upewnić się, że najnowsza zawartość jest zwracana do aplikacji klienckiej, interakcji klienta pamięci podręcznej zasad serwera ponownego sprawdzania poprawności wymagań i zawsze powoduje najbardziej zachowawcze zasady pamięci podręcznej. Wszystkie przykłady w tym temacie przedstawiono zasady z zasobem, który jest buforowana w dniu 1 stycznia i wygaśnie w dniu 4 stycznia w pamięci podręcznej.  
  
 W poniższych przykładach, wartość maksymalna nieaktualności (`maxStale`) jest używany w połączeniu z maksymalny wiek (`maxAge`):  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 5 dni, a nie określa `maxStale` wartość, według `maxAge` wartość, zawartość będzie można używać do 6 stycznia. Jednak zgodnie z wymaganiami ponownego sprawdzania poprawności serwera, zawartość wygasa w styczniu 4. Ponieważ data wygaśnięcia zawartości jest bardziej zachowawcze (wcześniej), ma pierwszeństwo przed `maxAge` zasad. W związku z tym zawartość wygaśnie w dniu 4 stycznia i musi ponownie sprawdzić poprawności nawet, jeśli nie został osiągnięty maksymalny wiek.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 5 dni i `maxStale` = 3 dni, zgodnie z `maxAge` wartości, zawartość będzie można używać do 6 stycznia. Zgodnie z `maxStale` wartości, zawartość będzie można używać do 7 stycznia. W związku z tym zawartość pobiera sprawdzony ponownie na styczeń 6.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 5 dni i `maxStale` = 1 dzień, zgodnie z `maxAge` wartości, zawartość będzie można używać do 6 stycznia. Zgodnie z `maxStale` wartości, zawartość będzie można używać do 5 stycznia. W związku z tym zawartość pobiera sprawdzony ponownie na styczeń 5.  
  
 Maksymalny wiek jest wcześniejsza niż data wygaśnięcia zawartości, zachowanie buforowania w bardziej zachowawcze zawsze obowiązują, a wartość maksymalna nieaktualności nie ma znaczenia. Poniższe przykłady przedstawiają wpływu ustawienia nieaktualności maksymalną (`maxStale`) wartość przy maksymalny wiek (`maxAge`) zostanie osiągnięty wygaśnięcia zawartości:  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 1 dzień, a nie określa wartości `maxStale` wartość, zawartość jest ponownie sprawdzić poprawności 2 stycznia, nawet jeśli nie wygasł.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 1 dzień i `maxStale` = 3 dni, zawartość jest ponownie sprawdzić poprawności 2 stycznia do wymuszania bardziej zachowawcze ustawienie zasad.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 1 dzień i `maxStale` = 1 dzień, zawartość jest ponownie sprawdzić poprawności 2 stycznia.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)  
 [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
