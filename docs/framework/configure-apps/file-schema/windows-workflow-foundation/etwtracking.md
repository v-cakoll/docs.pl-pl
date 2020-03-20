---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: d562bd4e3d46a1bdf41fc4065fee926850a49aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152174"
---
# <a name="etwtracking"></a>\<> śledzenia etw
Zachowanie usługi, które pozwala usłudze korzystać <xref:System.Activities.Tracking.EtwTrackingParticipant>ze śledzenia ETW za pomocą pliku .  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<zachowania>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<usługiZachowady>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>zachowania**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>śledzenia etw**  
  
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
|[\<zachowanie> \<usługZachod>](behavior-of-servicebehaviors-of-workflow.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Po dodaniu konfiguracji zachowanie, ten element konfiguracji służy do konfigurowania opcji uczestnikiem śledzenia w usłudze przepływu pracy.  
  
 Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki. Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie konfiguracji przedstawiono standardowego uczestnika śledzenia ETW skonfigurowany w pliku Web.config.  
  
 Identyfikator dostawcy używany przez uczestnika śledzenia ETW do zapisywania rekordów śledzenia na ETW jest zdefiniowany w sekcji ** \<diagnostyki>.** Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia. Jest to zdefiniowane przez **atrybut profileName** elementu ** \<add>.** Po zdefiniowaniu są one uczestnik śledzenia jest dodawany do ** \<etwTracking>** zachowanie usługi. Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [Kontrola i śledzenie przepływu pracy](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Uczestnicy śledzenia](../../../windows-workflow-foundation/tracking-participants.md)
