---
title: "Pamięci podręcznej zasad interakcji — maksymalny wiek i świeżości minimalna"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 75729fc92c6a4bfa0f5ad73b8bbd4b28456f21e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Pamięci podręcznej zasad interakcji — maksymalny wiek i świeżości minimalna
Aby upewnić się, że najnowsza zawartość jest zwracana do aplikacji klienckiej, interakcji klienta pamięci podręcznej zasad serwera ponownego sprawdzania poprawności wymagań i zawsze powoduje najbardziej zachowawcze zasady pamięci podręcznej. Wszystkie przykłady w tym temacie przedstawiono zasady z zasobem, który jest buforowana w dniu 1 stycznia i wygaśnie w dniu 4 stycznia w pamięci podręcznej.  
  
 Poniższe przykłady przedstawiają zasady pamięci podręcznej, będącą wynikiem interakcji maksymalny wiek (`maxAge`) i minimalna świeżości (`minFresh`) wartości.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 2 dni i `minFresh` nie zostanie określony, zawartość jest ponownie sprawdzić poprawności na 3 stycznia.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 2 dni i `minFresh` = 1 dzień, zgodnie z `maxAge`, zawartość jest pierwszą do 3 stycznia. Zgodnie z `minFresh`, aż do 3 stycznia jest nowa zawartość. W związku z tym zawartości musi być sprawdzony ponownie na 3 stycznia.  
  
-   Jeśli zasady pamięci podręcznej ustawia `maxAge` = 2 dni i `minFresh` = 2 dni zgodnie z `maxAge`, zawartość jest pierwszą do 3 stycznia. Zgodnie z `minFresh` do 2 stycznia jest nowa zawartość. W związku z tym zawartości musi być sprawdzony ponownie 2 stycznia.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięci podręcznej dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)  
 [Zasady oparte na lokalizacji pamięci podręcznej](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zasady na podstawie czasu pamięci podręcznej](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurowanie buforowanie w aplikacjach sieci](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [Pamięci podręcznej zasad interakcji — maksymalny wiek i nieaktualności maksymalny](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
