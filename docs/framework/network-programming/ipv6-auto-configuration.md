---
title: Automatyczna konfiguracja IPv6
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 530d772f905937681a9d06625e1bcf0c1b78c922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393432"
---
# <a name="ipv6-auto-configuration"></a>Automatyczna konfiguracja IPv6
Co ważne celu dla protokołu IPv6 jest obsługuje węzła typu Plug and Play. Oznacza to, że powinno być możliwe Podłącz węzła do sieci IPv6 i została ona skonfigurowana automatycznie bez interwencji człowieka.  
  
## <a name="type-of-auto-configuration"></a>Typ automatycznej konfiguracji  
 Protokół IPv6 obsługuje następujące typy automatycznej konfiguracji:  
  
-   **Stanowe automatycznej konfiguracji**. Ten typ konfiguracji wymaga pewnego poziomu udziału człowieka, ponieważ wymaga Dynamic Host Configuration Protocol dla IPv6 (DHCPv6) serwera dla instalacji i administracji węzłów. Serwer DHCPv6 przechowuje listę węzłów, do których podaje informacje o konfiguracji. Zachowuje również informacje o stanie, aby serwer żądał, jak długo każdy adres jest używany, a gdy mogą być dostępne do ponownego przypisania.  
  
-   **Bezstanowej konfiguracji automatycznej**. Ten typ konfiguracji jest odpowiednie dla małych organizacje i pojedyncze osoby. W takim przypadku każdy host Określa jej adresy z zawartości anonsów routera odebrane. Aby zdefiniować identyfikator sieci części adresu przy użyciu standardu IEEE EUI-64, jest można założyć unikatowości adres hosta łącze.  
  
 Niezależnie od tego, jak określić adres węzła należy sprawdzić, czy adres potencjalnych jest unikatowy dla łącza lokalnego. Jest to, wysyłając żądanie sąsiada wiadomość na adres potencjalnych. Jeśli węzeł odbiera odpowiedzi, wie to, czy adres jest już w użyciu, a następnie określić inny adres.  
  
## <a name="ipv6-mobility"></a>Mobilność IPv6  
 Mnożenie urządzeń przenośnych została wprowadzona nowe wymaganie: urządzenie musi mieć możliwość arbitralnie zmiana lokalizacji w Internecie IPv6 i zachować istniejące połączenia. Do tej funkcji, przenośnych węzła jest przypisany adres domowy, w którym go zawsze można połączyć się z. Jeśli węzeł przenośny w domu, łączy się link do strony głównej i używa adresu macierzystego. Gdy węzeł przenośny jest witryną, agenta macierzystego, który jest zazwyczaj router, przekazuje wiadomości między węzeł przenośny i węzłów, z którymi jest komunikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Protokół IPv6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Gniazda](../../../docs/framework/network-programming/sockets.md)
