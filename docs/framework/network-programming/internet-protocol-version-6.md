---
title: Protokół internetowy w wersji 6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 995bc2075a7df5c9a37cc68e812f62c9de2e53c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397120"
---
# <a name="internet-protocol-version-6"></a>Protokół internetowy w wersji 6
Internet Protocol w wersji 6 (IPv6) to nowy zestaw standardowych protokołów warstwy sieciowej Internetu. Protokół IPv6 jest przeznaczona do rozwiązuje wiele problemów w bieżącej wersji pakietu protokołu internetowego (nazywane IPv4) w odniesieniu do adresów wyczerpanie, zabezpieczeń, automatycznej konfiguracji, rozszerzalności i tak dalej. IPv6 rozszerza możliwości Internet umożliwiające nowych typów aplikacji, w tym aplikacje peer-to-peer i przenośnych. Poniżej przedstawiono główne kwestie bieżącego protokołu IPv4:  
  
-   Szybkie wyczerpania przestrzeni adresowej.  
  
     Powodowało to korzystanie z translatorami adresów sieciowych (NAT), który mapowania wielu adresów prywatnych jeden publiczny adres IP. Głównych problemów utworzone przez ten mechanizm przetwarzania koszty i braku łączności end-to-end.  
  
-   Brak obsługi hierarchii.  
  
     Ze względu na jego organizacji związanego z używaniem klasy wstępnie zdefiniowanych IPv4 nie ma wartość true, hierarchicznych pomocy technicznej. Nie jest możliwe struktury adresów IP w taki sposób, aby rzeczywiście mapy topologii sieci. Ta luka ważnych projekt tworzy potrzebę dużych tabel routingu w celu dostarczenia pakietów IPv4 do dowolnej lokalizacji w Internecie.  
  
-   Konfiguracja złożoną siecią.  
  
     Przez protokół IPv4, adresy muszą być przypisane statycznie lub przy użyciu protokołu konfiguracji, takie jak DHCP. W sytuacji idealnej hosty nie musi ufać zarządzanie infrastrukturą DHCP. Zamiast tego czy one może skonfigurować oparte na segmencie sieci, w którym znajdują się.  
  
-   Brak wbudowane uwierzytelnianie i poufności.  
  
     IPv4 nie wymaga obsługi dowolny mechanizm udostępniający uwierzytelniania i szyfrowania w ramach wymiany danych. Spowoduje to zmianę w przypadku adresu IPv6. Zabezpieczenia protokołu internetowego (IPSec) musi być spełniony obsługi protokołu IPv6.  
  
 Nowy pakiet protokołów musi spełniać następujące wymagania podstawowe:  
  
-   Na dużą skalę routingu i adresy z małym obciążeniem.  
  
-   Automatyczna konfiguracja w różnych sytuacjach nawiązującego połączenie.  
  
-   Wbudowane uwierzytelnianie i poufności.  
  
 Aby uzyskać więcej informacji, zobacz [adresowanie IPv6](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [autokonfiguracji IPv6](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Włączanie i wyłączanie IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), i [Porady: modyfikowanie pliku konfiguracji komputera, aby włączyć obsługę protokołu IPv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## <a name="references"></a>Odwołania  
 Poniżej znajdują się wybrane dokumenty RFC, które można znaleźć w witrynie Internet Engineering Task Force ([http://www.ietf.org](http://www.ietf.org/)):  
  
-   RFC 1287, kierunku architektura przyszłych internetowych.  
  
-   RFC 1454, porównanie propozycje następnej wersji adresu IP.  
  
-   RFC 2373, adresu IP w wersji 6 adresowania architektury.  
  
-   RFC 2374, Format kumulowalnego adresu globalnego emisji pojedynczej protokołu IPv6.  
  
 Można również znaleźć informacje dotyczące IPv6 na [obszaru protokołu IPv6 w witrynie Technet](http://go.microsoft.com/fwlink/?LinkID=179658).  
  
## <a name="see-also"></a>Zobacz też  
 [IPv6 Sockets próbki](http://go.microsoft.com/fwlink/?LinkID=179568)  
 [Przykłady programowania sieciowego](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Gniazda](../../../docs/framework/network-programming/sockets.md)
