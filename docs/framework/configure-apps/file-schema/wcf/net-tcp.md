---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 4a3a17655f5469fe84c0b684ebdac9848bbfba84
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397694"
---
# \<net.tcp>
Określa ustawienia konfiguracji dla sieci. Usługa udostępniania portów TCP, która umożliwia wielu procesom współużytkowanie tego samego portu TCP.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**  
  
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
|`listenBacklog`|Liczba całkowita określająca maksymalną liczbę oczekujących połączeń, które są akceptowane z udostępnionego połączenia, ale nie są jeszcze wysyłane do usług Windows Communication Foundation (WCF). Wartość domyślna to 10.|  
|`maxPendingAccepts`|Liczba całkowita określająca maksymalną liczbę oczekujących współbieżnych wątków w punkcie końcowym nasłuchiwania dla usługi udostępniania. Wartość domyślna to 2.|  
|`MaxPendingConnections`|Maksymalna liczba połączeń, które odbiornik może oczekiwać na akceptację przez aplikację. Po przekroczeniu tej wartości przydziału nowe połączenia przychodzące są usuwane, a nie czekają na ich zaakceptowanie. Funkcje połączeń, takie jak zabezpieczenia komunikatów, mogą spowodować otwarcie więcej niż jednego połączenia przez klienta. Administratorzy usługi powinni uwzględnić te dodatkowe połączenia podczas ustawiania wartości tego przydziału. Wartość domyślna to 10.|  
|`receiveTimeout`|Wartość określająca <xref:System.TimeSpan> limit czasu odczytu danych ramek i wykonywania operacji wysyłania połączenia z podkreśleń. Wartość domyślna to "00:00:10".|  
|`teredoEnabled`|Wartość logiczna wskazująca, czy usługa udostępniania portów używa usługi Microsoft Teredo do nasłuchiwania na portach TCP w imieniu usług WCF. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|Kolekcja elementów konfiguracji, które zawierają atrybut służący `securityIdentifier` do określania kont użytkowników dla procesów, które obsługują usługi WCF i mają dostęp do połączenia z usługą udostępniania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost. exe.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat udostępniania portów, zobacz [net. TCP — Udostępnianie portów](../../../wcf/feature-details/net-tcp-port-sharing.md). Aby dowiedzieć się, jak skonfigurować usługę udostępniania portów, zobacz [Konfigurowanie usługi udostępniania portów Net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [Współużytkowanie portów w składniku Net.TCP](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [Konfigurowanie usługi współużytkowania portów Net.TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
