---
title: '&lt;trackingProfile&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: fe8d129769d0948160d581aa578b5ac2d0dc0e4d
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087651"
---
# <a name="lttrackingprofilegt"></a>&lt;trackingProfile&gt;
Reprezentuje sekcję konfiguracji do tworzenia subskrypcji do śledzenia rekordów w uczestnikiem śledzenia przepływu pracy. Profil śledzenia zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania. Kwerendy zdefiniowane w profilu śledzenia sekcji zdefiniować rodzaje zdarzenia, które są zwracane w subskrypcji.  
  
 Aby uzyskać więcej informacji śledzenia przepływu pracy i jego konfiguracji, zobacz [przepływu pracy i śledzenie](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
\<system.serviceModel>  
\<Śledzenie >  
\<trackingProfile>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String" 
             profileName="String" 
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String" 
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String" 
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String" 
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String" 
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Ciąg określający nazwę profilu śledzenia.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Uczestnicy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> właściwości.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Śledzenie >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.|  
  
## <a name="remarks"></a>Uwagi  
 Śledzenie profile zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania. W zależności od potrzeb może zapisu profil przybliżonego, które subskrybuje niewielkiego zestawu zmian stanu wysokiego poziomu przepływ pracy. Z drugiej strony można utworzyć bardzo określony profil którego wynikowego zdarzenia są rozbudowanych, odtworzenie przepływ wykonania szczegółowe później.  
  
 Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy. Istnieje kilka typów zapytania, które umożliwiają subskrybować różnymi klasami <xref:System.Activities.Tracking.TrackingRecord> obiektów. Aby uzyskać pełną listę zapytań, zobacz [ \<uczestników >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) i [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)...  
  
 W poniższym przykładzie pokazano profil śledzenia w pliku konfiguracji, który umożliwia śledzenia uczestnika do subskrybowania `Started` i `Completed` zdarzenia przepływu pracy.  
  
```xml  
<system.serviceModel>  
  <tracking>    
    <trackingProfile name="Sample Tracking Profile">  
      <workflow activityDefinitionId="*">  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
            <states>  
              <state name="Started"/>  
              <state name="Completed"/>  
            </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [Kontrola i śledzenie przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
