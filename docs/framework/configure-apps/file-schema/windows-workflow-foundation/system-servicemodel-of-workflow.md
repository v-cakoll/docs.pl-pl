---
title: < system.serviceModel > przepływu pracy
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 005a274df9e9ab99227a3748b7a25c9d465d020f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768878"
---
# <a name="systemservicemodel-of-workflow"></a>\<system.serviceModel > przepływu pracy
Ta sekcja konfiguracji zawiera wszystkie elementy konfiguracji przepływu pracy.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
    <behavior name="String">  
      <bufferReceive maxPendingMessagesPerChannel="Integer" />  
      <etwTracking profileName="String" />  
     <sendMessageChannelCache allowUnsafeCaching="Boolean" >          
        <channelSettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
        <factorySettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
     </sendMessageChannelCache>  
      <sqlWorkflowInstanceStore   
          connectionStringName="String"   
          honstLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionaction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
    </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <tracking>    
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
             <activityStateQuery activityName="String" />  
                <arguments>  
                   <argument name="String"/>  
                </arguments>  
                <states>  
                   <state name="String"/>  
                </states>  
                <variables>  
                   <variable name="String"/>  
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
                 faultHandlerActivityName="String"/>  
          </faultPropagationQueries>  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                 <state name="String"/>  
              </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowania >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behaviors-of-workflow.md)|Ta sekcja definiuje **serviceBehaviors** kolekcji.  Każdy element w kolekcji definiuje zachowanie elementy używane przez usługi. Każdy element zachowanie jest określony przez jego unikatowy **nazwa** atrybutu.|  
|[\<tracking>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.<br /><br /> Aby uzyskać więcej informacji śledzenia przepływu pracy i jego konfiguracji, zobacz [przepływu pracy i śledzenie](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [Konfigurowanie śledzenia przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|\<Konfiguracja >|Element główny dla wszystkich elementów konfiguracji w PLiku konfiguracji PLatformy .NET.|
