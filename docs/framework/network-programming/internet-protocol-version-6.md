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
ms.openlocfilehash: 2c9b3b1c647d74444fed01e38b65c1b2fe8364c6
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185626"
---
# <a name="internet-protocol-version-6"></a>Protokół internetowy w wersji 6
Protokołu internetowego w wersji 6 (IPv6) to nowy zestaw standardowych protokołów służący do warstwy sieci Internet. Protokół IPv6 pozwala rozwiązać wiele problemów w bieżącej wersji pakietu Internet Protocol (nazywane IPv4) w odniesieniu do adresów wyczerpanie, zabezpieczeń, konfiguracji automatycznego, rozszerzalność i tak dalej. Protokół IPv6 rozszerza możliwości Internetu, aby włączyć nowych rodzajów aplikacji, w tym aplikacji peer-to-peer i na urządzeniach przenośnych. Oto główne kwestie bieżącego protokołu IPv4:  
  
-   Szybkie wyczerpania przestrzeni adresowej.  
  
     Doprowadziło to do korzystania z translatorami adresów sieciowych (NAT), które mapowania wielu adresów prywatnych do jednego publicznego adresu IP. Głównych problemów, które są tworzone przez ten mechanizm przetwarzania kosztów i braku łączności end-to-end.  
  
-   Brak obsługi hierarchii.  
  
     Ze względu na swojej organizacji związane klasę wstępnie zdefiniowanych IPv4 brakuje true obsługi hierarchicznych. Nie jest możliwe struktury adresów IP w taki sposób, że naprawdę mapy topologii sieci. Ta luka kluczowe znaczenie podczas projektowania tworzy potrzebę dużych tabel routingu w celu dostarczenia pakietów IPv4 do dowolnej lokalizacji w Internecie.  
  
-   Konfiguracja sieci złożonych.  
  
     Za pomocą protokołu IPv4, adresy muszą być statycznie przypisane lub przy użyciu protokołu konfiguracji, takie jak DHCP. W sytuacji idealnej hosty nie musi opierać się na zarządzanie infrastrukturą DHCP. Zamiast tego będzie one możliwość skonfigurowania oparte na segmencie sieci, w którym znajdują się.  
  
-   Brak wbudowanego uwierzytelniania i poufnością.  
  
     IPv4 nie wymaga obsługi dla dowolnego mechanizm, który zapewnia uwierzytelniania i szyfrowania w ramach wymiany danych. Spowoduje to zmianę przy użyciu protokołu IPv6. Zabezpieczenia protokołu internetowego (IPSec) jest wymaganie obsługi protokołu IPv6.  
  
 Nowy pakiet protokołów musi spełniać następujące wymagania podstawowe:  
  
-   Na dużą skalę usługa routing i adresowanie z niskie obciążenie.  
  
-   Automatyczna konfiguracja w różnych sytuacjach nawiązującego połączenie.  
  
-   Wbudowane uwierzytelnianie i poufnością.  
  
 Aby uzyskać więcej informacji, zobacz [adresowanie IPv6](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [automatyczna konfiguracja IPv6](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Włączanie i wyłączanie protokołu IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), i [Porady: modyfikowanie pliku konfiguracji komputera, aby włączyć obsługę protokołu IPv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## <a name="references"></a>Odwołania  
 Poniżej przedstawiono wybrane dokumenty RFC, które znajdują się w witrynie Internet Engineering Task Force ([http://www.ietf.org](http://www.ietf.org/)):  
  
-   RFC 1287, kierunku architektura przyszłych internetowych.  
  
-   RFC 1454, porównanie propozycje następnej wersji adresu IP.  
  
-   RFC 2373, adresów IP w wersji 6 adresowania architektury.  
  
-   RFC 2374, Format się agregowaniu globalnego adresu emisji pojedynczej protokołu IPv6.  
  
 Można również znaleźć informacje dotyczące protokołu IPv6 na [obszaru protokołu IPv6 w witrynie Technet](https://go.microsoft.com/fwlink/?LinkID=179658).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe gniazda IPv6](https://msdn.microsoft.com/library/ms180981(v=vs.85).aspx)  
 [Przykłady programowania sieciowego](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Gniazda](../../../docs/framework/network-programming/sockets.md)
