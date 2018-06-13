---
title: IPv6 Routing
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c3e2662eb444c70d2376a05e44ac84f472f27384
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397809"
---
# <a name="ipv6-routing"></a>IPv6 Routing
Elastyczne mechanizm routingu przynosi IPv6. Ze względu na sposób, w których IPv4 identyfikatory sieci były i są przydzielone, dużych tabel routingu muszą być obsługiwane za routerów, które znajdują się na szkieletowymi Internet. Te routery musi znać wszystkich tras, aby przekazywać pakiety, które są potencjalnie skierowany do dowolnego węzła w Internecie. Zdolność do agregacji adresów IPv6 umożliwia elastyczne adresowania i znacząco zmniejsza rozmiar tabele routingu. W tej nowej architekturze adresowania routerów pośrednich musi śledzić tylko lokalnej części sieci do przekazywania wiadomości odpowiednio.  
  
## <a name="neighbor-discovery"></a>Odnajdowania sąsiadów  
 Niektóre funkcje oferowane przez funkcję odnajdowania sąsiadów są:  
  
-   Odnajdowanie routera. To pozwala hostom na identyfikację routerów lokalnych.  
  
-   Adres rozpoznawania. Dzięki temu węzłów do rozpoznania adresu warstwy linku, aby uzyskać odpowiedni adres następnego przeskoku (wymiana Address Resolution Protocol [ARP]).  
  
-   Adres automatycznej konfiguracji. Dzięki temu hostów automatycznie skonfigurować adresy globalne i lokalne lokacji.  
  
 Odnajdowania sąsiadów używa Internet Control Message Protocol dla IPv6 (ICMPv6) wiadomości, które obejmują:  
  
-   Anons routera. Wysyłane przez router artykule okresowo lub w odpowiedzi na żądanie routera. Routery IPv6 używają anonse routera anonsowanie ich dostępności, prefiksy adresów i innych parametrów.  
  
-   Żądanie routera. Wysyłany przez hosta do żądania routery Link bezpośrednio wysyłać anons routera.  
  
-   Żądanie sąsiadów. Wysyłane przez węzły do rozpoznawania adresów, zduplikowany adres wykrywania, lub sprawdź, czy sąsiada jest nadal dostępny.  
  
-   Anons sąsiadów. Wysyłane przez węzły, aby odpowiedzieć na żądanie sąsiada lub powiadamiania sąsiadów zmiany adresu warstwy linku.  
  
-   Przekierowania. Wysyłane przez routery, aby wskazać lepsze adres następnego przeskoku do określonego miejsca docelowego dla węzła wysyłania.  
  
## <a name="see-also"></a>Zobacz też  
 [Protokół IPv6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Gniazda](../../../docs/framework/network-programming/sockets.md)
