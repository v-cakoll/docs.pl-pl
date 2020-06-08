---
title: Automatyczna konfiguracja IPv6
description: Dowiedz się, jak protokół IPv6 obsługuje Plug and Play węzła, gdzie węzeł dołącza do sieci IPv6 i jest skonfigurowany bez interwencji człowieka.
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: 9d65bc453478ac4679556e931b1758c18cfedcf3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502330"
---
# <a name="ipv6-auto-configuration"></a>Automatyczna konfiguracja IPv6
Jednym z ważnych celów związanych z protokołem IPv6 jest obsługa węzłów Plug and Play. Oznacza to, że powinno być możliwe podłączenie węzła do sieci IPv6 i jego automatyczne skonfigurowanie bez interwencji człowieka.  
  
## <a name="type-of-auto-configuration"></a>Typ automatycznej konfiguracji  
 Protokół IPv6 obsługuje następujące typy automatycznej konfiguracji:  
  
- **Stanowa Autokonfiguracja**. Ten typ konfiguracji wymaga pewnego poziomu interwencji człowieka, ponieważ wymaga serwera Dynamic Host Configuration Protocol dla protokołu IPv6 (DHCPv6) do instalacji i administrowania węzłami. Serwer DHCPv6 przechowuje listę węzłów, do których dostarcza informacje o konfiguracji. Przechowuje również informacje o stanie, aby serwer wiedział, jak długo każdy z nich jest używany, i kiedy może być dostępny do ponownego przypisania.  
  
- **Bezstanowa Autokonfiguracja**. Ten typ konfiguracji jest odpowiedni dla małych organizacji i osób. W takim przypadku każdy host określa jego adresy z zawartości odebranych anonsów routera. Przy użyciu standardu IEEE EUI-64 w celu zdefiniowania części identyfikatora sieci należy zastanowić się, że adres hosta jest unikatowy.  
  
 Niezależnie od sposobu ustalenia adresu, węzeł musi sprawdzić, czy jego potencjalny adres jest unikatowy dla linku lokalnego. Jest to realizowane przez wysłanie komunikatu o zażądaniu sąsiada do potencjalnego adresu. Jeśli węzeł odbierze odpowiedź, wie, że adres jest już używany i musi określić inny adres.  
  
## <a name="ipv6-mobility"></a>Mobilność IPv6  
 W przypadku urządzeń przenośnych wprowadzono nowe wymaganie: urządzenie musi być w stanie arbitralnie zmienić lokalizacje w Internecie IPv6 i nadal obsługiwać istniejące połączenia. Aby zapewnić tę funkcję, do węzła mobilnego jest przypisywany adres domowy, pod którym zawsze można się połączyć. Gdy węzeł mobilny znajduje się w domu, nawiązuje połączenie z linkiem głównym i używa jego adresu domowego. Gdy węzeł mobilny znajduje się poza domem, głównym agentem, który jest zazwyczaj routerem, przekazuje komunikaty między węzłem przenośnym i węzłami, z którymi się komunikują.  
  
## <a name="see-also"></a>Zobacz także

- [Protokół internetowy w wersji 6](internet-protocol-version-6.md)
- [Gniazda](sockets.md)
