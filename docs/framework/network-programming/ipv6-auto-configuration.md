---
title: Automatyczna konfiguracja IPv6
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: 31aaebaefa0d2682ee20ae93496aff42ae1633d8
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50170669"
---
# <a name="ipv6-auto-configuration"></a>Automatyczna konfiguracja IPv6
Jeden cel ważne w przypadku protokołu IPv6 jest obsługuje węzeł typu Plug and Play. Oznacza to, że powinno być możliwe do podłączyć węzła do sieci IPv6 i jest automatycznie konfigurowany bez żadnej interwencji człowieka.  
  
## <a name="type-of-auto-configuration"></a>Typ automatycznej konfiguracji  
 Protokół IPv6 obsługuje następujące typy automatycznej konfiguracji:  
  
-   **Stanowe autokonfiguracji**. Ten typ konfiguracji wymaga pewnego poziomu interwencji człowieka, ponieważ wymaga Dynamic Host Configuration Protocol dla IPv6 (DHCPv6) serwera, instalacji i administrowania węzłów. Serwer DHCPv6 przechowuje listę węzłów, których dostarcza mu Informacje o konfiguracji. Udostępnia również informacje o stanie, aby serwer żądał, jak długo każdy adres jest używany, a kiedy może być dostępny do ponownego przypisania.  
  
-   **Bezstanowej autokonfiguracji**. Ten typ konfiguracji jest odpowiednia dla małych i użytkowników indywidualnych. W takim przypadku każdy host Określa jej adresy z zawartości anonse odebranych routera. Przy użyciu standardu IEEE EUI-64, aby zdefiniować część Identyfikatora sieci adresu, jest można założyć unikatowości adres hosta łącze.  
  
 Niezależnie od tego, jak adres jest określana węzeł musi Sprawdź, czy adresu potencjalnych jest unikatowy dla łącza lokalnego. Jest to realizowane przez wysłanie żądanie sąsiadów wiadomość na adres potencjalnych. Jeśli węzeł odbiera żadnej odpowiedzi, wie, czy adres jest już używana, a następnie należy określić inny adres.  
  
## <a name="ipv6-mobility"></a>Mobilność IPv6  
 Powszechne stosowanie urządzeń mobilnych wprowadził nowe wymaganie: urządzenie musi być w stanie dowolnie zmienić lokalizacje w Internecie IPv6 i zachować istniejące połączenia. Do tej funkcji, przenośne węzła jest przypisany adres domowy, w którym ją będą zawsze osiągalni. W momencie przenośnych węzła w domu, łączy się link do strony głównej i używa jej adres domowy. Gdy węzeł przenośny jest witryną, agenta macierzystego, który jest zazwyczaj router, przekazuje wiadomości między węzłem mobilnych i węzłów za pomocą których komunikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Protokół IPv6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Gniazda](../../../docs/framework/network-programming/sockets.md)
