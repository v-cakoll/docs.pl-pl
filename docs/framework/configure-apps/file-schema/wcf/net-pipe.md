---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: 7d868d84318db8c9fe188293154dc275060a3952
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933187"
---
# <a name="netpipe"></a>\<> net. pipe
Określa ustawienia konfiguracji dla usługi aktywacji potoków nazwanych, która zarządza okresem istnienia połączenia nazwanego potoku i obsługuje żądania aktywacji, które docierają do potoków nazwanych.  
  
 \<system.serviceModel.activation>  
\<> net. pipe  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
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
|`maxPendingAccepts`|Liczba całkowita określająca maksymalną liczbę oczekujących współbieżnych wątków w punkcie końcowym nasłuchiwania dla usługi udostępniania. Wartość domyślna to 2.|  
|`maxPendingConnections`|Liczba całkowita określająca maksymalną liczbę połączeń, które mogą poczekać na wysłanie. Wartość domyślna to 100.|  
|`receiveTimeout`|Wartość <xref:System.TimeSpan> określająca limit czasu odczytu danych ramek i wykonywania operacji wysyłania połączenia z podkreśleń. Wartość domyślna to "00:00:10"|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybut służący do określania kont użytkowników dla procesów, które obsługują usługi WCF i mają dostęp do połączenia z usługą udostępniania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost. exe.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
