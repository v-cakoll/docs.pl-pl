---
title: '&lt;Diagnostyka&gt;'
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 0854ce6525fd7c96cf7c19d2c86dadef1b9a53bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltdiagnosticsgt"></a>&lt;Diagnostyka&gt;
`diagnostics` Element definiuje ustawienia używane przez administratora w czasie wykonywania inspekcji i kontroli.  
  
 \<system.ServiceModel>  
\<Diagnostyka >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>  
  <diagnostics 
      etwProviderId="String"       
      performanceCounters="Off/ServiceOnly/All/Default"              
      wmiProviderEnabled="Boolean" >       
    <endToEndTracing 
        activityTracing="Boolean"  
        messageFlowTracing="Boolean"  
        propagateActivity="Boolean" />  
    <messageLogging 
        logEntireMessage="Boolean"  
        logMalformedMessages="Boolean"  
        logMessagesAtServiceLevel="Boolean"  
        logMessagesAtTransportLevel="Boolean"  
        maxMessagesToLog="Integer"  
        maxSizeOfMessageToLog="Integer" >  
      <filters>  
        <clear />  
      </filters>  
    </messageLogging>  
  </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|etwProviderId|Ciąg określający identyfikator dostawcy śledzenia zdarzeń, która zapisuje zdarzenia do sesji ETW.|  
|liczniki wydajności|Określa, czy są włączone liczniki wydajności dla zestawu. Prawidłowe wartości to<br /><br /> -Off: Liczniki wydajności są wyłączone.<br />-ServiceOnly: Jest włączona tylko liczniki wydajności istotne dla tej usługi.<br />-Wszystkie: Wydajności liczniki można wyświetlać w czasie wykonywania.<br />— Wartość domyślna: _WCF_Admin wystąpienia licznika wydajności pojedynczego jest tworzony. To wystąpienie jest używane umożliwia zbieranie danych SQM używane przez infrastrukturę. Brak wartości liczników dla tego wystąpienia są aktualizowane i w związku z tym pozostanie od zera. Jest to wartość domyślna, jeśli konfiguracja nie jest stosowany w przypadku usługi WCF.|  
|wmiProviderEnabled|Wartość logiczna określająca czy włączone jest dostawca WMI dla zestawu. Dostawca WMI jest wymagany dla użytkownik może uzyskać dostępu do środowiska wykonawczego do inspekcji i kontroli funkcji Windows Communication Foundation (WCF). Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<endToEndTracing >](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|Element konfiguracji, który umożliwia włączanie i wyłączanie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.|  
|[\<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|Opisuje ustawienia rejestrowania komunikatów usługi WCF.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|ServiceModel|Element główny wszystkich elementów konfiguracji usługi WCF.|  
  
## <a name="remarks"></a>Uwagi  
 `diagnostics` Sekcja definiuje ustawień diagnostycznych dla wszystkich usług znajduje się w zestawie. Nie jest możliwe do definiowania ustawień diagnostyki oddzielne na poziomie usługi, chyba że istnieje tylko jedna usługa w zestawie. Atrybuty są ustawione zgodnie z wymaganiami sekcji.  
  
## <a name="example"></a>Przykład  
  
```xml  
<diagnostics
    wmiProviderEnabled="false"  
    performanceCounters="all">  
  <messageLogging 
      logEntireMessage="true"  
      logMalformedMessages="true"  
      logMessagesAtServiceLevel="true"  
      logMessagesAtTransportLevel="true"  
      maxMessagesToLog="42"  
      maxSizeOfMessageToLog="42">  
    <filters>  
      <clear />  
    </filters>  
  </messageLogging>  
</diagnostics>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>
