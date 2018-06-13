---
title: Zasady oparte na lokalizacji pamięci podręcznej
ms.date: 03/30/2017
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b4109cef8d527d397903854e05a2204a3e551938
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394517"
---
# <a name="location-based-cache-policies"></a>Zasady oparte na lokalizacji pamięci podręcznej
Zasady oparte na lokalizacji pamięci podręcznej definiuje świeżości prawidłowych wpisów pamięci podręcznej podstawę, z którego można pobrać żądanego zasobu. Zasób pamięci podręcznej jest nieprawidłowy w przypadku korzystania z niego nie narusza wymagania określony serwer ponownego sprawdzania poprawności. Zasady oparte na lokalizacji pamięci podręcznej jest tworzona programowo przy użyciu <xref:System.Net.Cache.RequestCachePolicy> lub <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktora klasy. Typ zasad na podstawie lokalizacji jest przekazywany do konstruktora przy użyciu <xref:System.Net.Cache.RequestCacheLevel> lub <xref:System.Net.Cache.HttpRequestCacheLevel> wartości wyliczenia. Przykłady kodu, które utworzyć zasady oparte na lokalizacji pamięci podręcznej można znaleźć [porady: ustawienia zasad oparte na lokalizacji pamięci podręcznej aplikacji](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md). W poniższych sekcjach opisano każdego typu zasad na podstawie lokalizacji pamięci podręcznej dla zasobów Hypertext Transfer Protocol (protokół http i https).  
  
## <a name="cache-if-available-policy"></a>Pamięci podręcznej, jeśli jest dostępna zasad  
 Jeśli prawidłowe żądany zasób znajduje się w lokalnej pamięci podręcznej, używane jest buforowanych zasobów; w przeciwnym razie żądanie zasobu jest wysyłane do serwera. Jeśli żądany zasób jest dostępny w dowolnym pamięci podręcznej między klientem a serwerem, przez pośredniego pamięci podręcznej można spełnić żądania.  
  
## <a name="cache-only-policy"></a>Zasady tylko w pamięci podręcznej  
 Jeśli prawidłowe żądany zasób znajduje się w lokalnej pamięci podręcznej, zasobów pamięci podręcznej jest używany. W przypadku tego poziomu zasad pamięci podręcznej <xref:System.Net.WebException> jest zgłaszany wyjątek, jeśli element nie znajduje się w lokalnej pamięci podręcznej.  
  
## <a name="cache-or-next-cache-only-policy"></a>Pamięci podręcznej lub obok pamięci podręcznej tylko zasady  
 Jeśli prawidłowe żądany zasób znajduje się w lokalnej pamięci podręcznej lub pośredniego pamięci podręcznej w sieci lokalnej, zasobów pamięci podręcznej jest używany. W przeciwnym razie <xref:System.Net.WebException> wyjątku. W protokole HTTP, Protokół buforowania można to osiągnąć przy użyciu dyrektywy sterowania tylko jeśli-zapisanych w pamięci podręcznej pamięci podręcznej.  
  
## <a name="no-cache-no-store-policy"></a>Zasady przechowywania nie nie pamięci podręcznej  
 Żądany zasób nie jest nigdy używane z dowolnym pamięci podręcznej i nigdy nie znajduje się w dowolnym pamięci podręcznej. Jeśli żądany zasób znajduje się w lokalnej pamięci podręcznej, zostanie ono usunięte. Do pośredniego pamięci podręcznych tego poziomu zasad wskazuje, czy należy również usunąć zasób. W protokole HTTP, Protokół buforowania można to osiągnąć przy użyciu dyrektywy sterowania nie magazynu pamięci podręcznej.  
  
## <a name="refresh-policy"></a>Odświeżanie zasad  
 Jeśli jest uzyskiwana z serwera, lub znalezionych w pamięci podręcznej w innych niż lokalnej pamięci podręcznej można żądanego zasobu. Przed przez pośredniego pamięci podręcznej można spełnić żądania, tej pamięci podręcznej musi ponownie sprawdź poprawność jego wpis pamięci podręcznej z serwerem. W protokole HTTP, Protokół buforowania, jest to osiągane przy użyciu maksymalny wiek = dyrektywy sterowania 0 pamięci podręcznej i nagłówek Pragma nie-cache.  
  
## <a name="reload-policy"></a>Załaduj ponownie zasad  
 Żądane zasoby muszą być pobrane z serwera. Odpowiedź mogły zostać zapisane w lokalnej pamięci podręcznej. W protokole HTTP, Protokół buforowania można to osiągnąć przy użyciu pamięci podręcznej w pamięci podręcznej nie dyrektywy sterowania i nagłówek Pragma pamięci podręcznej nie.  
  
## <a name="revalidate-policy"></a>Ponownie sprawdź poprawność zasad  
 Porównuje kopię zasobu w pamięci podręcznej z kopią na serwerze. Jeśli na serwerze jest nowsza, służy do spełnienia żądania i zastępuje kopię w pamięci podręcznej. Jeśli w pamięci podręcznej jest taka sama jak kopii na serwerze, kopia pamięci podręcznej jest używany. W protokole HTTP, Protokół buforowania można to osiągnąć przy użyciu żądania warunkowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)  
 [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
