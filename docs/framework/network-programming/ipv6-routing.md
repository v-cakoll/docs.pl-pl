---
title: Routing IPv6
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 93300107710164d755d578633b7fa6651f984987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047789"
---
# <a name="ipv6-routing"></a>Routing IPv6
Elastyczny mechanizm routingu jest zaletą protokołu IPv6. Ze względu na sposób, w jaki identyfikatory sieci IPv4 były i są przydzielane, duże tabele routingu muszą być obsługiwane przez routery, które znajdują się w szkieletach internetowych. Routery te muszą znać wszystkie trasy, aby przesyłać dalej pakiety, które są potencjalnie kierowane do dowolnego węzła w Internecie. Dzięki możliwości agregowania adresów IPv6 umożliwia elastyczne adresowanie i drastycznie zmniejsza rozmiar tabel routingu. W tej nowej architekturze adresowania routery pośrednie muszą śledzić tylko lokalną część swojej sieci, aby odpowiednio przesyłać dalej wiadomości.  
  
## <a name="neighbor-discovery"></a>Odnajdowanie sąsiada  
 Niektóre funkcje dostarczone przez Odnajdywanie sąsiadów to:  
  
- Odnajdowanie routera. Dzięki temu hosty mogą identyfikować routery lokalne.  
  
- Rozdzielczość adresu. Dzięki temu węzły mogą rozpoznawać adres warstwy łącza dla odpowiedniego adresu następnego przeskoku (zastąpienie protokołu rozpoznawania adresów [ARP]).  
  
- Automatyczna konfiguracja adresu. Dzięki temu hosty mogą automatycznie konfigurować adresy lokalne i globalne lokacji.  
  
 Odnajdowanie sąsiadów używa protokołu internetowego komunikatów sterujących dla komunikatów IPv6 (ICMPv6), które zawierają:  
  
- Anons routera. Wysyłane przez router pseudo-okresowe lub w odpowiedzi na żądanie routera. Routery IPv6 używają anonsów routera do reklamowania ich dostępności, prefiksów adresów i innych parametrów.  
  
- Pozyskiwanie routera. Wysłane przez hosta, aby zażądać, aby routery na linku natychmiast wysłać anons routera.  
  
- Nagabywanie sąsiada. Wysyłane przez węzły w celu rozpoznawania adresów, wykrywania zduplikowanych adresów lub sprawdzenia, czy sąsiad jest nadal osiągalny.  
  
- Reklama sąsiada. Wysyłane przez węzły w celu udzielenia odpowiedzi na żądanie sąsiada lub powiadomienia sąsiadów o zmianie adresu warstwy łącza.  
  
- Przekierowanie. Wysyłane przez routery w celu wskazania lepszego adresu następnego przeskoku do określonego miejsca docelowego dla węzła wysyłającego.  
  
## <a name="see-also"></a>Zobacz też

- [Protokół internetowy w wersji 6](internet-protocol-version-6.md)
- [Gniazda](sockets.md)
