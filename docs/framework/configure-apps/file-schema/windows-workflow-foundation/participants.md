---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: e6e996bd1cc32258167e30287e9338a4773ce921
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152031"
---
# <a name="participants"></a>\<uczestnicy>
Skonfiguruj listę śledzenia uczestników, które będą wysyłane do śledzenia rekordów jest emitowane bezpośrednio ze środowiska wykonawczego i przetwórz je w sposób są skonfigurowane. Dotyczy to również zapis do określonych danych wyjściowych (np. PLik, konsoli, ETW), przetwarzania/agregowania rekordy lub dowolną kombinację, który może być wymagane.  
  
 Aby uzyskać więcej informacji na temat śledzenia i śledzenia uczestników przepływu pracy, zobacz [Śledzenie przepływu pracy oraz śledzenie](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) i śledzenie [uczestników](../../../windows-workflow-foundation/tracking-participants.md).  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>śledzenia**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<uczestników>**  
  
## <a name="syntax"></a>Składnia  
  
```xml
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dodaj>](add-of-participants.md)|Zawiera ustawienia dla uczestnika śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>śledzenia](tracking.md)|Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.|  
  
## <a name="remarks"></a>Uwagi  
 Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki. Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.  
  
 Wielu uczestników śledzenia może korzystać ze zdarzeń śledzenia jednocześnie. Uczestnik śledzenia mogą być skojarzone z profilem różnych śledzenia.  
  
 Standardowe śledzenia uczestnika, który jest podawany jako który zapisuje rekordy śledzenia sesji funkcji ETW. Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji. Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń. Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.  
  
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

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [Kontrola i śledzenie przepływu pracy](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Uczestnicy śledzenia](../../../windows-workflow-foundation/tracking-participants.md)
