---
title: <add>programu WCF
ms.date: 03/30/2017
ms.assetid: c196f6d7-77f6-4266-973c-305b2b4dd8a2
ms.openlocfilehash: fa94f15a296aa03640bf0a262eb45ea1664944cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926621"
---
# <a name="add-of-wcf"></a>\<Dodawanie > WCF
Konfigurowanie śledzenia uczestnika nasłuchujący rekordów śledzenia jest emitowane bezpośrednio ze środowiska wykonawczego i przetworzyć je w sposób został skonfigurowany. Dotyczy to również zapis do określonych danych wyjściowych (np. PLik, konsoli, ETW), przetwarzania/agregowania rekordy lub dowolną kombinację, który może być wymagane.  
  
 Aby uzyskać więcej informacji o śledzeniu i śledzeniu przepływów pracy, zobacz [śledzenie przepływu pracy i](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) śledzenie i [Śledzenie uczestników](../../../windows-workflow-foundation/tracking-participants.md).  
  
 \<system.serviceModel>  
\<Śledzenie >  
\<Uczestnicy >  
\<add>  
  
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
  
|Element|Opis|  
|-------------|-----------------|  
|nazwa|Ciąg określający nazwę uczestnika śledzenia.|  
|Nazwa_profilu|Ciąg określający nazwę profilu śledzenia, który definiuje rekordów śledzenia uczestnika śledzenia ma subskrypcję.|  
|— typ|Ciąg, który określa typ uczestnika śledzenia.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Uczestnicy >](../windows-workflow-foundation/participants.md)|Lista śledzenia uczestników|  
  
## <a name="remarks"></a>Uwagi  
 Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki. Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.  
  
 Wiele uczestników śledzenia może jednocześnie używać zdarzeń śledzenia. Uczestnik śledzenia mogą być skojarzone z profilem różnych śledzenia.  
  
 Standardowe śledzenia uczestnika, który jest podawany jako który zapisuje rekordy śledzenia sesji funkcji ETW. Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji. Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń. Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konfiguracji przedstawia standardowy Uczestnik śledzenia ETW skonfigurowany w pliku Web. config.  
  
 Identyfikator dostawcy, który używa uczestnika śledzenia zdarzeń systemu Windows do zapisywania rekordów śledzenia zdarzeń systemu Windows jest zdefiniowany w `<diagnostics>` sekcji. Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia. To jest definiowana za pomocą `profileName` atrybutu `<add>` elementu. Te po zdefiniowaniu, śledzenie uczestnika zostanie dodany do `<etwTracking>` usługi zachowanie. Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile" />
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [Kontrola i śledzenie przepływu pracy](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Uczestnicy śledzenia](../../../windows-workflow-foundation/tracking-participants.md)
