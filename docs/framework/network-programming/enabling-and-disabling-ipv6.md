---
title: Włączanie i wyłączanie protokołu IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 66c802dd5feb865faf7469cb7da04fbffcb4a2d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048560"
---
# <a name="enabling-and-disabling-ipv6"></a>Włączanie i wyłączanie protokołu IPv6
Aby użyć protokołu IPv6, upewnij się, że używasz wersji systemu operacyjnego obsługującego protokół IPv6 i upewnij się, że system operacyjny i klasy sieciowe są poprawnie skonfigurowane.  
  
## <a name="configuration-steps"></a>Kroki konfiguracji  
 W poniższej tabeli wymieniono różne konfiguracje  
  
|System operacyjny IPv6 włączone?|Klasy sieciowe z włączoną funkcją IPv6?|Opis|  
|-------------------------------------|---------------------------------------|-----------------|  
|Nie|Nie|Można przeanalizować adresy IPv6.|  
|Nie|Tak|Można przeanalizować adresy IPv6.|  
|Tak|Nie|Można przeanalizować adresy IPv6 i rozpoznać adresy IPv6 przy użyciu metod rozpoznawania nazw, które nie są oznaczone jako przestarzałe.|  
|Tak|Tak|Można przeanalizować i rozpoznać adresy IPv6 przy użyciu wszystkich metod, w tym te oznaczone przestarzałe.|  
  
 Należy pamiętać, że aby włączyć obsługę IPv6 dla wszystkich klas w System.Net obszarze nazw, należy zmodyfikować plik konfiguracji komputera lub plik konfiguracyjny dla aplikacji. Plik konfiguracyjny aplikacji ma pierwszeństwo przed plikiem konfiguracji komputera.  
  
 Na przykład jak zmodyfikować plik konfiguracyjny komputera, *machine.config*, aby włączyć obsługę Protokołu Ipv6 zobacz, [Jak: Zmodyfikować plik konfiguracyjny komputera, aby włączyć obsługę Protokołu Ipv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md). Upewnij się również, że obsługa IPv6 jest włączona dla systemu operacyjnego.  
  
 Program .NET Framework ma przełącznik konfiguracji ustawiony w pliku konfiguracyjnym w następujący sposób  
  
```xml  
<system.net>  
  ...  
  <settings>  
    ...  
    <ipv6 enabled="true"/>  
    ...  
  </settings>  
  ...  
</system.net>  
```  
  
 W przypadku programu .NET Framework w wersji 1.1 i wcześniejszych wartość przełącznika <xref:System.Net.Dns?displayProperty=nameWithType> konfiguracji **obsługującego protokół ipv6** określa, czy członkowie klasy zwracają adresy IPv6.  
  
 W przypadku programu .NET Framework w wersji 2.0 lub nowszej, jeśli system Windows obsługuje protokół IPv6, członkowie <xref:System.Net.Dns?displayProperty=nameWithType> klasy (na przykład <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda) zwracają adresy IPv6 z jednym ograniczeniem. Przestarzałe <xref:System.Net.Dns?displayProperty=nameWithType> elementy członkowskie systemu <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> DNS (na przykład metoda) odczytują i rozpoznają wartość w pliku konfiguracyjnym dla ustawienia obsługującego protokół ipv6.  
  
## <a name="see-also"></a>Zobacz też

- [Protokół internetowy w wersji 6](internet-protocol-version-6.md)
- [Gniazda](sockets.md)
- [Schemat ustawień sieci](../configure-apps/file-schema/network/index.md)
- [\<element> ipv6 (ustawienia sieciowe)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
