---
title: Protokół IPv6
description: Dowiedz się więcej na temat protokołu IPv6 i różnice między protokołem IPv4. Aplikacje .NET Framework obsługują protokół IPv6, ale mogą wymagać konfiguracji.
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: dd8b0b26e449fba7479d2678aff25ed49e721a90
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502395"
---
# <a name="internet-protocol-version-6"></a>Protokół IPv6
Protokół Internet Protocol w wersji 6 (IPv6) to nowy zestaw standardowych protokołów dla warstwy sieciowej Internetu. Protokół IPv6 jest przeznaczony do rozwiązywania wielu problemów z bieżącą wersją internetowego zestawu protokołów (znanego jako IPv4) w odniesieniu do niszczenia, zabezpieczeń, automatycznej konfiguracji, rozszerzalności i tak dalej. Protokół IPv6 rozszerza możliwości Internetu w celu umożliwienia korzystania z nowych rodzajów aplikacji, w tym aplikacji równorzędnych i mobilnych. Poniżej przedstawiono główne problemy dotyczące bieżącego protokołu IPv4:  
  
- Szybka wyczerpanie przestrzeni adresowej.  
  
     Spowodowało to wykorzystanie translatorów adresów sieciowych (NAT), które mapują wiele adresów prywatnych na jeden publiczny adres IP. Główne problemy stworzone przez ten mechanizm polegają na przetwarzaniu obciążeń i braku kompleksowej łączności.  
  
- Brak obsługi hierarchii.  
  
     Ze względu na własną wstępnie zdefiniowaną organizację, w protokole IPv4 brakuje prawdziwej obsługi hierarchicznej. Nie jest możliwe tworzenie struktury adresów IP w sposób, który naprawdę mapuje topologię sieci. Ta istotna Luka w projekcie tworzy potrzeby dla dużych tabel routingu do dostarczania pakietów IPv4 do dowolnej lokalizacji w Internecie.  
  
- Złożona konfiguracja sieci.  
  
     W przypadku protokołu IPv4 adresy muszą być przypisane statycznie lub przy użyciu protokołu konfiguracji, takiego jak DHCP. W idealnej sytuacji hosty nie muszą polegać na administrowaniu infrastrukturą DHCP. Zamiast tego mogą być one konfigurowane na podstawie segmentu sieci, w którym się znajdują.  
  
- Brak wbudowanego uwierzytelniania i poufności.  
  
     Protokół IPv4 nie wymaga obsługi żadnego mechanizmu, który zapewnia uwierzytelnianie lub szyfrowanie danych wymienianych. Te zmiany są wprowadzane przy użyciu protokołu IPv6. Zabezpieczenia protokołu internetowego (IPSec) są wymagane do obsługi protokołu IPv6.  
  
 Nowy pakiet protokołów musi spełniać następujące podstawowe wymagania:  
  
- Routing i adresowanie na dużą skalę z niskim obciążeniem.  
  
- Autokonfiguracja w różnych sytuacjach łączących.  
  
- Wbudowane uwierzytelnianie i poufność.  
  
 Aby uzyskać więcej informacji, zobacz [adresowanie IPv6](ipv6-addressing.md), [Routing IPv6](ipv6-routing.md), [Autokonfiguracja IPv6](ipv6-auto-configuration.md), [Włączanie i wyłączanie protokołu IPv6](enabling-and-disabling-ipv6.md)oraz [instrukcje: Modyfikowanie pliku konfiguracji komputera w celu włączenia obsługi protokołu IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## <a name="references"></a>Odwołania  
 Poniżej przedstawiono wybrane dokumenty RFC, które można znaleźć w witrynie internetowej [Internet Engineering Task Force (IETF)](https://www.ietf.org/) :  
  
- RFC 1287 w kierunku przyszłej architektury Internetu.  
  
- RFC 1454, porównanie propozycji dla następnej wersji adresu IP.  
  
- Architektura adresowania RFC 2373, IP w wersji 6.  
  
- RFC 2374 — format adresu globalnego emisji pojedynczej IPv6.  
  
 Informacje dotyczące protokołu IPv6 można także znaleźć w [wersji 6 protokołu IP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).  
  
## <a name="see-also"></a>Zobacz także

- [Przykład protokołu IPv6 Sockets](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [Przykłady programowania sieciowego](network-programming-samples.md)
- [Gniazda](sockets.md)
