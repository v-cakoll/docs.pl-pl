---
title: Routing IPv6
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 93300107710164d755d578633b7fa6651f984987
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047789"
---
# <a name="ipv6-routing"></a>Routing IPv6
Elastyczny mechanizm routingu to korzyść z protokołu IPv6. Ze względu na sposób, w jaki identyfikatory sieci IPv4 zostały i są przydzielone, należy zachować duże tabele routingu na routerach, które są podłączone do Internetu. Te routery muszą znać wszystkie trasy w celu przekazywania pakietów, które mogą być kierowane do dowolnego węzła w Internecie. Dzięki możliwości agregowania adresów protokół IPv6 umożliwia elastyczne adresowanie, a radykalnie zmniejsza rozmiar tabel routingu. W tej nowej architekturze, routery pośrednie muszą śledzić tylko lokalną część swojej sieci, aby zapewnić odpowiednie przesyłanie komunikatów.  
  
## <a name="neighbor-discovery"></a>Odnajdywanie sąsiadów  
 Niektóre funkcje dostępne w ramach odnajdywania sąsiadów są następujące:  
  
- Odnajdywanie routerów. Pozwala to hostom na identyfikację routerów lokalnych.  
  
- Rozpoznawanie adresów. Pozwala to węzłom na rozpoznanie adresu warstwy łącza dla odpowiedniego adresu następnego przeskoku (zastępowanie protokołu ARP).  
  
- Automatycznej konfiguracji adresu. Pozwala to hostom na automatyczne konfigurowanie adresów lokalnych i globalnych lokacji.  
  
 Funkcja odnajdywania sąsiadów korzysta z protokołu komunikatów sterowania Internetem dla protokołu IPv6 (ICMPv6), które obejmują:  
  
- Anons routera. Wysyłany przez router na zasadzie okresowo lub w odpowiedzi na żądanie routera. Routery IPv6 używają anonsów routera do anonsowania dostępności, prefiksów adresów i innych parametrów.  
  
- Żądanie routera. Wysyłany przez hosta w celu uzyskania natychmiastowego wysłania anonsu routera.  
  
- Żądanie sąsiada. Wysyłany przez węzły do rozpoznawania adresów, wykrywania zduplikowanych adresów lub do sprawdzenia, czy sąsiad jest nadal dostępny.  
  
- Anons sąsiada. Wysyłany przez węzły odpowiadające na żądanie sąsiada lub do powiadamiania sąsiadów o zmianie adresu warstwy łącza.  
  
- Przekierowania. Wysyłany przez routery, aby wskazać lepszy adres następnego przeskoku do określonego miejsca docelowego dla węzła wysyłającego.  
  
## <a name="see-also"></a>Zobacz także

- [Protokół IPv6](internet-protocol-version-6.md)
- [Gniazda](sockets.md)
