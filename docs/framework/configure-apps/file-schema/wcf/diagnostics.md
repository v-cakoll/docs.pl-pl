---
title: '&lt;Diagnostyka&gt;'
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: de11145620e8fdf96785908df85ab5ecdfd2e25e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524598"
---
# <a name="ltdiagnosticsgt"></a>&lt;Diagnostyka&gt;
`diagnostics` Element definiuje ustawienia używane przez administratora w czasie wykonywania inspekcji i kontroli.  
  
 \<system.ServiceModel>  
\<Diagnostyka >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
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
|etwProviderId|Ciąg określający identyfikator dostawcy śledzenia zdarzeń, który zapisuje zdarzenia do sesji ETW.|  
|Liczniki wydajności|Określa, czy są włączone liczniki wydajności dla zestawu. Prawidłowe wartości to:<br /><br /> — Wyłączone: Liczniki wydajności są wyłączone.<br />-ServiceOnly: Tylko liczniki wydajności istotne dla tej usługi jest włączone.<br />— Wszystkie: Liczniki wydajności mogą być wyświetlane w czasie wykonywania.<br />— Wartość domyślna: _WCF_Admin wystąpienia licznika wydajności pojedynczego zostanie utworzony. To wystąpienie jest używane do włączenia zbierania danych METRYK dla używana przez infrastrukturę. Brak wartości liczników dla tego wystąpienia są aktualizowane, a w związku z tym pozostanie od zera. Jest wartością domyślną, jeśli konfiguracja nie jest obecny dla usługi WCF.|  
|wmiProviderEnabled|Wartość logiczna określająca, czy włączony jest dostawca usługi WMI dla zestawu. Dostawca usługi WMI jest wymagana dla użytkownika w celu uzyskania dostępu do funkcji inspekcji i kontroli programu Windows Communication Foundation (WCF) w czasie wykonywania. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<endToEndTracing>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|Element konfiguracji, który umożliwia włączanie i wyłączanie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.|  
|[\<messageLogging>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|W tym artykule opisano ustawienia rejestrowania komunikatów WCF.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|serviceModel|Element główny wszystkich elementów konfiguracji programu WCF.|  
  
## <a name="remarks"></a>Uwagi  
 `diagnostics` Sekcja definiuje ustawienia diagnostyki dla wszystkich usług znajdujących się w zestawie. Nie jest możliwe do definiowania ustawień diagnostycznych oddzielne na poziomie usługi, chyba że istnieje tylko jedna usługa w zestawie. Atrybuty są ustawione zgodnie z wymogami sekcji.  
  
## <a name="example"></a>Przykład  
  
```xml  
<diagnostics wmiProviderEnabled="false"
             performanceCounters="all">
  <messageLogging logEntireMessage="true"
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
