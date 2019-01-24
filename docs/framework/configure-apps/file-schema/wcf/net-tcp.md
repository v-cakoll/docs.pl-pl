---
title: '&lt;net.tcp&gt;'
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 7df24d816b4eed8ceed542e14261413fbe7651a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728729"
---
# <a name="ltnettcpgt"></a>&lt;net.tcp&gt;
Określa ustawienia konfiguracji sieci. TCP usługi udostępniania portów, która umożliwia wielu procesom współużytkowanie tego samego portu TCP.  
  
 \<system.serviceModel.activation>  
\<net.tcp>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="Integer"
             maxPendingAccepts="Integer"
             maxPendingConnections="Integer"
             receiveTimeout="TimeSpan"
             teredoEnabled="Boolean">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only)-->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`listenBacklog`|Liczba całkowita określająca maksymalną liczbę oczekujących połączeń, które są akceptowane z udostępnionego połączenia, ale jeszcze nie są wysyłane do usługi Windows Communication Foundation (WCF). Wartość domyślna wynosi 10.|  
|`maxPendingAccepts`|Liczba całkowita określająca maksymalną liczbę oczekujących współbieżnych wątków na punkcie końcowym nasłuchiwania dla usługi udostępniania. Wartość domyślna to 2.|  
|`MaxPendingConnections`|Maksymalna liczba połączeń, które mogą mieć odbiornika, oczekuje na zatwierdzenie przez aplikację. Po przekroczeniu tej wartości limitu przydziału na nowe połączenia przychodzące są odrzucane zamiast oczekuje na zatwierdzenie. Połączenie funkcji, takich jak zabezpieczenia komunikatów może spowodować klienta otworzyć więcej niż jedno połączenie. Administratorzy usługi należy uwzględnić w przypadku tych dodatkowych połączeń, podczas ustawiania tej wartości limitu przydziału. Wartość domyślna wynosi 10.|  
|`receiveTimeout`|Element `TimeSpan` , który określa limit czasu dla odczytu danych z ramek i wykonania przekazania połączenia z połączeń podkreślonych. Wartość domyślna to "00: 00:10".|  
|`teredoEnabled`|Wartość logiczna wskazująca, czy port udostępnianej usługi używa usługi Microsoft Teredo aby nasłuchiwać portów TCP w imieniu usług WCF. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<allowAccounts>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybutu, aby określić konta użytkowników dla procesów, które prowadzą hosting usług WCF i przyznano im dostęp do połączenia z usługą udostępniania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost.exe.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat współużytkowania portów, zobacz [współużytkowania portów Net.TCP](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md). Aby dowiedzieć się, jak skonfigurować port udostępnianej usługi, zobacz [konfigurowania usługi udostępniania portów Net.TCP](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [Współużytkowanie portów w składniku Net.TCP](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Konfigurowanie usługi współużytkowania portów Net.TCP](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
