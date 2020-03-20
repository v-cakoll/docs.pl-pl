---
title: <behavior>przepływu <serviceBehaviors> pracy
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152323"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a>\<zachowanie> \<usługZachowatości> przepływu pracy
Element **zachowania** zawiera zbiór ustawień zachowania usługi. Każde zachowanie jest indeksowane według jego **nazwy**. Usługi można połączyć się z każdego zachowania za pomocą tego atrybutu **behaviorConfiguration** [ \<elementu>.](../wcf/endpoint-element.md) Dzięki temu punktów końcowych udostępnić typowych konfiguracji zachowanie bez ponownego definiowania ustawień.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<zachowania>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<usługiZachowady>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>zachowania**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan"
                           leaseTimeout="TimeSpan"
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan"
                           leaseTimeout="TimeSpan"
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String"
                                  hostLockRenewalPeriod="TimeSpan"
                                  instanceCompletionAction="DeleteNothing/DeleteAll"
                                  instanceEncodingAction="None/GZip"
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan"
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|name|Unikatowy ciąg, który zawiera nazwę konfiguracji zachowanie. Ta wartość jest ciągiem zdefiniowanej przez użytkownika, który musi być unikatowy, ponieważ działa jako ciąg identyfikacyjny dla elementu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<buforRecetywne>](bufferreceive.md)|Zachowanie usługi, które umożliwia usługa do użycia buforowanego odbierać przetwarzania, co umożliwia usługi przepływu pracy w celu przetwarzania komunikatów poza kolejnością.|  
|[\<>routingu](../wcf/routing-of-servicebehavior.md)|Zachowanie usługi, które pozwala usłudze korzystać <xref:System.Activities.Tracking.EtwTrackingParticipant>ze śledzenia ETW za pomocą pliku .|  
|[\<>sendMessageChannelCache](sendmessagechannelcache.md)|Zachowanie usługi, która umożliwia dostosowanie poziomów udostępniania pamięci podręcznej, ustawienia pamięci podręcznej fabryki kanału i ustawienia pamięci podręcznej kanału dla przepływów pracy, które wysyłają wiadomości do punktów końcowych usługi przy użyciu wysyłania działań obsługi wiadomości.|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|Zachowanie usługi, które umożliwia skonfigurowanie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcji, która obsługuje utrwalanie informacji o stanie wystąpień usługi przepływu pracy w bazie danych PROGRAMU SQL Server 2005 lub SQL Server 2008.|  
|[\<>przepływu pracyIdle](workflowidle.md)|Zachowanie usługi sterująca po zwolnione wystąpienia bezczynności przepływu pracy i utrwalone.|  
|[\<>zarządzanie przepływem pracy](workflowinstancemanagement.md)|Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.|  
|[\<workflowUnhandledException>](workflowunhandledexception.md)|Zachowanie usługi, który umożliwia określenie Akcja podejmowana po wystąpieniu nieobsługiwanego wyjątku w ramach usługi przepływu pracy.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<usługiZachowady>](servicebehaviors-of-workflow.md)|Kolekcja elementów zachowanie usługi.|
