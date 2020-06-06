---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 2749bc6c66d491a8a160d98b508fb43aa027b806
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398041"
---
# \<diagnostics>
`diagnostics`Element definiuje ustawienia, które mogą być używane przez administratora na potrzeby inspekcji i kontroli w czasie wykonywania.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
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
|Liczniki wydajności|Określa, czy są włączone liczniki wydajności dla zestawu. Prawidłowe wartości to<br /><br /> -Off: Liczniki wydajności są wyłączone.<br />-Tylko do-Service: włączono tylko liczniki wydajności odpowiednie dla tej usługi.<br />-All: Liczniki wydajności mogą być wyświetlane w czasie wykonywania.<br />-Domyślnie: utworzono pojedyncze wystąpienie licznika wydajności _WCF_Admin. To wystąpienie jest używane do włączania zbierania danych SQM używanych przez infrastrukturę. Żadna z wartości licznika dla tego wystąpienia nie jest aktualizowana i w związku z tym pozostanie równa zero. Jest to wartość domyślna, jeśli żadna konfiguracja nie jest obecna dla programu WCF.|  
|wmiProviderEnabled|Wartość logiczna określająca, czy dostawca WMI dla zestawu jest włączony. Dostawca WMI jest wymagany, aby użytkownik mógł uzyskać dostęp do funkcji inspekcji i kontroli programu Windows Communication Foundation (WCF). Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<endToEndTracing>](endtoendtracing.md)|Element konfiguracji, który pozwala na włączenie i wyłączenie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.|  
|[\<messageLogging>](messagelogging.md)|Opisuje ustawienia rejestrowania komunikatów WCF.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Modelu|Element główny wszystkich elementów konfiguracji WCF.|  
  
## <a name="remarks"></a>Uwagi  
 `diagnostics`Sekcja definiuje ustawienia diagnostyki dla wszystkich usług znajdujących się w zestawie. Nie można definiować oddzielnych ustawień diagnostycznych na poziomie usługi, chyba że w zestawie znajduje się tylko jedna usługa. Atrybuty są ustawiane zgodnie z wymaganiami sekcji.  
  
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
