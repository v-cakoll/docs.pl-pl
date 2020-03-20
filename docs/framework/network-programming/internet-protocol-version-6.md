---
title: Protokół IPv6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: 367db4fa4e585d6066009dbd1afacb154829319a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047880"
---
# <a name="internet-protocol-version-6"></a>Protokół IPv6
Protokół internetowy w wersji 6 (IPv6) to nowy zestaw standardowych protokołów dla warstwy sieciowej Internetu. Protokół IPv6 został zaprojektowany w celu rozwiązania wielu problemów bieżącej wersji pakietu protokołu internetowego (znanego jako IPv4) w odniesieniu do wyczerpania adresów, zabezpieczeń, automatycznej konfiguracji, rozszerzalności i tak dalej. IPv6 rozszerza możliwości Internetu, aby włączyć nowe rodzaje aplikacji, w tym aplikacje peer-to-peer i mobilne. Poniżej przedstawiono główne problemy bieżącego protokołu IPv4:  
  
- Szybkie wyczerpywanie się przestrzeni adresowej.  
  
     Doprowadziło to do użycia translatorów adresów sieciowych (NAT), które mapują wiele adresów prywatnych na jeden publiczny adres IP. Główne problemy spowodowane przez ten mechanizm są przetwarzanie narzutów i brak łączności end-to-end.  
  
- Brak wsparcia hierarchii.  
  
     Ze względu na jego nieodłączne wstępnie zdefiniowane organizacji klasy IPv4 brakuje prawdziwej obsługi hierarchicznej. Nie można uporządkować adresów IP w sposób, który naprawdę mapuje topologię sieci. Ta kluczowa wada projektowa powoduje konieczność dostarczania pakietów IPv4 do dowolnej lokalizacji w Internecie przez duże tabele routingu.  
  
- Złożona konfiguracja sieci.  
  
     W przypadku protokołu IPv4 adresy muszą być przypisywane statycznie lub przy użyciu protokołu konfiguracyjnego, takiego jak DHCP. W idealnej sytuacji hosty nie musiałyby polegać na administrowaniu infrastrukturą DHCP. Zamiast tego będą mogli skonfigurować się na podstawie segmentu sieci, w którym się znajdują.  
  
- Brak wbudowanego uwierzytelniania i poufności.  
  
     IPv4 nie wymaga obsługi żadnego mechanizmu, który zapewnia uwierzytelnianie lub szyfrowanie wymienianych danych. To się zmienia w IPv6. Zabezpieczenia protokołu INTERNETOWEGO (IPSec) to wymóg obsługi protokołu IPv6.  
  
 Nowy pakiet protokołów musi spełniać następujące podstawowe wymagania:  
  
- Routing na dużą skalę i adresowanie z niskim obciążeniem.  
  
- Automatyczna konfiguracja dla różnych sytuacji łączenia.  
  
- Wbudowane uwierzytelnianie i poufność.  
  
 Aby uzyskać więcej informacji, zobacz [Adresowanie IPv6](ipv6-addressing.md), [Routing IPv6,](ipv6-routing.md) [Automatyczna konfiguracja IPv6](ipv6-auto-configuration.md), [Włączanie i wyłączanie IPv6](enabling-and-disabling-ipv6.md)oraz [Jak: Modyfikowanie pliku konfiguracyjnego komputera w celu włączenia obsługi IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## <a name="references"></a>Dokumentacja  
 Poniżej znajdują się wybrane dokumenty RFC, które można znaleźć w witrynie internetowej [Internet Engineering Task Force (IETF):](https://www.ietf.org/)  
  
- RFC 1287, Ku przyszłości Architektura Internetu.  
  
- RFC 1454, Porównanie propozycji dla następnej wersji IP.  
  
- RFC 2373, architektura adresowania IP w wersji 6.  
  
- RFC 2374 — agregowany globalny format emisji pojedynczej IPv6.  
  
 Informacje związane z protokółem IPv6 można również znaleźć na [stronie IP w wersji 6 (IPv6).](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29)  
  
## <a name="see-also"></a>Zobacz też

- [Przykład gniazd IPv6](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [Przykłady programowania sieciowego](network-programming-samples.md)
- [Gniazda](sockets.md)
