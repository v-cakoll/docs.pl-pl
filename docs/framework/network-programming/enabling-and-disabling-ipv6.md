---
title: Włączanie i wyłączanie protokołu IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 66c802dd5feb865faf7469cb7da04fbffcb4a2d6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048560"
---
# <a name="enabling-and-disabling-ipv6"></a>Włączanie i wyłączanie protokołu IPv6
Aby korzystać z protokołu IPv6, należy się upewnić, że uruchomiono wersję systemu operacyjnego, która obsługuje protokół IPv6, i upewnić się, że system operacyjny i klasy sieciowe są prawidłowo skonfigurowane.  
  
## <a name="configuration-steps"></a>Kroki konfiguracji  
 W poniższej tabeli wymieniono różne konfiguracje  
  
|System operacyjny IPv6 — włączony?|Czy są włączone klasy sieci IPv6?|Opis|  
|-------------------------------------|---------------------------------------|-----------------|  
|Nie|Nie|Może analizować adresy IPv6.|  
|Nie|Tak|Może analizować adresy IPv6.|  
|Tak|Nie|Może analizować adresy IPv6 i rozwiązywać adresy IPv6 przy użyciu metod rozpoznawania nazw nieoznaczonych jako przestarzałe.|  
|Tak|Tak|Można analizować i rozwiązywać adresy IPv6 przy użyciu wszystkich metod, w tym tych, które zostały oznaczone jako przestarzałe.|  
  
 Należy pamiętać, że aby włączyć obsługę protokołu IPv6 dla wszystkich klas w przestrzeni nazw System.Net, należy zmodyfikować plik konfiguracji komputera lub plik konfiguracyjny aplikacji. Plik konfiguracyjny aplikacji ma pierwszeństwo przed plikiem konfiguracji komputera.  
  
 Aby zapoznać się z przykładem sposobu modyfikowania pliku konfiguracji komputera, *Machine. config*w celu włączenia obsługi protokołu IPv6, [Zobacz: Zmodyfikuj plik konfiguracji komputera, aby włączyć obsługę](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)protokołu IPv6. Upewnij się również, że obsługa protokołu IPv6 jest włączona dla systemu operacyjnego.  
  
 .NET Framework ma ustawiony przełącznik konfiguracji w pliku konfiguracji w następujący sposób  
  
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
  
 W przypadku .NET Framework w wersji 1,1 i wcześniejszych wartość przełącznika konfiguracja **obsługująca protokół IPv6** określa, czy elementy członkowskie <xref:System.Net.Dns?displayProperty=nameWithType> klasy zwracają adresy IPv6.  
  
 W przypadku .NET Framework w wersji 2,0 lub nowszej, jeśli system Windows obsługuje protokół IPv6, <xref:System.Net.Dns?displayProperty=nameWithType> wówczas elementy członkowskie klasy (na przykład <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> Metoda) będą zwracały adresy IPv6 z jednym ograniczeniem. Przestarzałe elementy członkowskie DNS <xref:System.Net.Dns?displayProperty=nameWithType> (na przykład <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> Metoda) odczytają i rozpoznają wartość w pliku konfiguracyjnym dla ustawienia włączony protokół IPv6.  
  
## <a name="see-also"></a>Zobacz także

- [Protokół IPv6](internet-protocol-version-6.md)
- [Gniazda](sockets.md)
- [Schemat ustawień sieci](../configure-apps/file-schema/network/index.md)
- [\<> IPv6, element (Ustawienia sieci)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
