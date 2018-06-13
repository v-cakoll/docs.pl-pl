---
title: Włączanie i wyłączanie IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b018d646816bda96945a440a890da20b81b1cbbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393935"
---
# <a name="enabling-and-disabling-ipv6"></a>Włączanie i wyłączanie IPv6
Aby korzystać z protokołu IPv6, upewnij się, że używasz wersji systemu operacyjnego, który obsługuje protokół IPv6 i upewnij się, że system operacyjny i klasy sieciowe są prawidłowo skonfigurowane.  
  
## <a name="configuration-steps"></a>Kroki konfiguracji  
 W poniższej tabeli wymieniono różne konfiguracje  
  
|System operacyjny jest włączony protokół IPv6?|Sieci klasy włączony protokół IPv6?|Opis|  
|-------------------------------------|---------------------------------------|-----------------|  
|Nie|Nie|Można analizować adresów IPv6.|  
|Nie|Tak|Można analizować adresów IPv6.|  
|Tak|Nie|Można przeanalizować adresy IPv6 i rozpoznawania adresów IPv6 za pomocą metody rozpoznawania nazw nie oznaczony jako przestarzały.|  
|Tak|Tak|Można przeanalizować i rozpoznawania adresów IPv6 za pomocą wszystkie metody, łącznie z tymi oznaczony jako przestarzały.|  
  
 Należy pamiętać, że można włączyć obsługi protokołu IPv6 dla wszystkich klas w przestrzeni nazw System.Net, należy zmodyfikować plik konfiguracji komputera lub w pliku konfiguracyjnym aplikacji. Plik konfiguracji aplikacji ma pierwszeństwo nad pliku konfiguracji komputera.  
  
 Przykład sposobu modyfikowania pliku konfiguracji komputera *machine.config*, aby włączyć protokół Ipv6 pomocy technicznej, zobacz temat [porady: modyfikowanie pliku konfiguracji komputera do włączenia obsługi protokołu Ipv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md). Upewnij się również, że obsługa protokołu IPv6 jest włączona dla systemu operacyjnego.  
  
 .NET Framework ma przełącznik konfiguracji w następujący sposób ustawione w pliku konfiguracji  
  
```xml  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 Dla programu .NET Framework w wersji 1.1 i starszych wersjach wartość **ipv6 włączone** przełącznik konfiguracji określa czy członkami <xref:System.Net.Dns?displayProperty=nameWithType> klasy Zwróć adresy IPv6.  
  
 Dla programu .NET Framework w wersji 2.0 lub nowszej, jeśli system Windows obsługuje protokół IPv6, a następnie członkami <xref:System.Net.Dns?displayProperty=nameWithType> klasy, (na przykład <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> — metoda), którą będzie zwracać adresów IPv6 z jednym z ograniczeń. Przestarzali członkowie DNS <xref:System.Net.Dns?displayProperty=nameWithType> (na przykład <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metody) odczytuje i rozpoznać wartości w pliku konfiguracji dla ustawienia włączony protokół ipv6.  
  
## <a name="see-also"></a>Zobacz też  
 [Protokół IPv6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Gniazda](../../../docs/framework/network-programming/sockets.md)  
 [Schemat ustawień sieci](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<IPv6 > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
