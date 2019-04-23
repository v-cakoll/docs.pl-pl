---
title: Włączanie i wyłączanie protokołu IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 73dee0cb57674c8a2fa4ba2246162870ab1e3a10
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083689"
---
# <a name="enabling-and-disabling-ipv6"></a>Włączanie i wyłączanie protokołu IPv6
Aby skorzystać z protokołu IPv6, upewnij się, że używasz wersji systemu operacyjnego, który obsługuje protokół IPv6, a następnie upewnij się, że system operacyjny i klasy sieciowe są poprawnie skonfigurowane.  
  
## <a name="configuration-steps"></a>Kroki konfiguracji  
 W poniższej tabeli wymieniono różne konfiguracje  
  
|System operacyjny jest włączony protokół IPv6?|Sieć klasy włączony protokół IPv6?|Opis|  
|-------------------------------------|---------------------------------------|-----------------|  
|Nie|Nie|Można analizować adresów IPv6.|  
|Nie|Tak|Można analizować adresów IPv6.|  
|Yes|Nie|Można przeanalizować adresy IPv6 i rozpoznać adresów IPv6 za pomocą metody rozpoznawania nazw, nie oznaczony jako przestarzały.|  
|Tak|Tak|Można przeanalizować i rozpoznać adresów IPv6 za pomocą wszystkich metod, łącznie z tymi oznaczony jako przestarzały.|  
  
 Należy pamiętać, że aby włączyć obsługę protokołu IPv6 dla wszystkich klas w przestrzeni nazw System.Net, należy zmodyfikować plik konfiguracji komputera lub w pliku konfiguracyjnym aplikacji. Plik konfiguracyjny aplikacji ma priorytet nad plikiem konfiguracyjnym komputera.  
  
 Aby uzyskać przykład sposobu modyfikowania pliku konfiguracji komputera *machine.config*, aby włączyć Ipv6 pomocy technicznej, zobacz temat [jak: Zmodyfikuj plik konfiguracji komputera, aby włączyć obsługę protokołu Ipv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md). Ponadto upewnij się, że włączono obsługę protokołu IPv6, systemu operacyjnego.  
  
 .NET Framework ma przełącznik konfiguracji ustawione w pliku konfiguracji w następujący sposób  
  
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
  
 Dla programu .NET Framework w wersji 1.1 i starszych wartość **włączony protokół ipv6** konfiguracji przełącznik określa czy członkowie <xref:System.Net.Dns?displayProperty=nameWithType> klasy zwracać adresów IPv6.  
  
 Dla programu .NET Framework w wersji 2.0 lub nowszej, jeśli Windows obsługuje protokół IPv6, a następnie elementy członkowskie <xref:System.Net.Dns?displayProperty=nameWithType> klasy, (na przykład <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda), będzie zwracać adresów IPv6 z jednym z ograniczeń. Przestarzali członkowie DNS <xref:System.Net.Dns?displayProperty=nameWithType> (na przykład <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) odczytuje i rozpoznać wartości w pliku konfiguracji dla ustawienia włączony protokół ipv6.  
  
## <a name="see-also"></a>Zobacz także

- [Protokół IPv6](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [Gniazda](../../../docs/framework/network-programming/sockets.md)
- [Schemat ustawień sieci](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [\<Protokół IPv6 >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
