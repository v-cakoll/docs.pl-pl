---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: 653693fef92072cb1e6e23234359b765f0f18fc9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940229"
---
# <a name="etwtracking"></a>\<etwTracking >
Zachowanie usługi, które umożliwia usłudze korzystanie z funkcji śledzenia ETW przy użyciu <xref:System.Activities.Tracking.EtwTrackingParticipant>programu.  
  
\<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
\<etwTracking >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Nazwa_profilu|Ciąg określający nazwę profilu śledzenia skojarzony z tym działaniem.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie > w \<usłudze serviceBehaviors >](behavior-of-servicebehaviors-of-workflow.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Po dodaniu konfiguracji zachowanie, ten element konfiguracji służy do konfigurowania opcji uczestnikiem śledzenia w usłudze przepływu pracy.  
  
 Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki. Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konfiguracji przedstawia standardowy Uczestnik śledzenia ETW skonfigurowany w pliku Web. config.  
  
 Identyfikator dostawcy, którego Uczestnik śledzenia funkcji ETW używa do zapisywania rekordów śledzenia w funkcji ETW,  **\<** jest zdefiniowany w sekcji > diagnostyki. Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia. Jest on definiowany przez atrybut  **\<** ProfileName elementu Add >. Po ich zdefiniowaniu Uczestnik śledzenia zostanie dodany do  **\<zachowania usługi etwTracking >** . Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.  
  
```xml  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [Kontrola i śledzenie przepływu pracy](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Uczestnicy śledzenia](../../../windows-workflow-foundation/tracking-participants.md)
