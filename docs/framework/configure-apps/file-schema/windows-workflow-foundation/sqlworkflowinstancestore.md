---
title: '&lt;Obiekt sqlWorkflowInstanceStore&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d412e13dc42107d2bfe11c94e51e9690d0c5206b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltsqlworkflowinstancestoregt"></a>&lt;Obiekt sqlWorkflowInstanceStore&gt;
Zachowanie usługi, która pozwala na skonfigurowanie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcji, która obsługuje trwałych informacji o stanie dla wystąpienia usługi przepływu pracy w bazie danych programu SQL Server 2005 lub SQL Server 2008. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [magazyn wystąpienia przepływu pracy SQL](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
\<System. ServiceModel >  
\<zachowania >  
\<serviceBehaviors >  
\<zachowanie >  
\<Obiekt sqlWorkflowInstanceStore >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sqlWorkflowInstanceStore connectionStringName="String" 
                                honstLockRenewalPeriod="TimeSpan" 
                                instanceCompletionAction="DeleteNothing/DeleteAll" 
                                instanceEncodingAction="None/GZip" 
                                instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                runnableInstancesDetectionPeriod="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Parametry połączenia|Ciąg, który zawiera parametry połączenia używane do łączenia się z podstawowej bazy danych trwałości.|  
|connectionStringName|Ciąg, który zawiera parametry połączenia nazwanego na serwerze bazy danych. Oto przykład parametrów połączenia nazwanego jest "DefaultConnectionString".|  
|honstLockRenewalPeriod|Wartość przedziału czasu określa okres czasu, w którym hosta musi odnowić blokady w wystąpieniu. Jeśli host nie odnowić blokady w określonym czasie, wystąpienie jest odblokowana i może zostać pobrana przez innego hosta.<br /><br /> Zwalnianie przepływu pracy oznacza to również utrwalone. Ten atrybut jest ustawiony na zero, wystąpienie przepływu pracy jest utrwalona i zwalnianie natychmiast po przepływu pracy, staje się bezczynności. Ustawienie tego atrybutu na wartość TimeSpan.MaxValue skutecznie wyłącza operacja zwolnienia. Wystąpienia przepływu pracy bezczynności nigdy nie są usuwane.|  
|instanceCompletionAction|Wartość, która określa, czy dane wystąpienia przepływu pracy jest przechowywany w magazynie informacji o trwałości, po zakończeniu działania wystąpienia przepływu pracy lub w przypadku zostaną usunięte w tym momencie. Ta wartość jest typu <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> Akcje wyliczany składają się z usuwanie danych wystąpienia w sklepie trwałości lub nie usunięcie danych wystąpienia w sklepie trwałości, po zakończeniu jego działania wystąpienia.<br /><br /> Przechowywanie wystąpień po zakończeniu powoduje szybko wzrostu bazy trwałości i ma to wpływ na wydajność bazy danych. Należy skonfigurować zasadę przeczyszczeniu bazy danych, można usunąć te rekordy okresowo, aby upewnić się, że wydajność bazy danych jest na poziomie, które spełniają wymagań dotyczących wydajności.|  
|instanceEncodingOption|Opcjonalna wartość, która określa, czy informacje o stanie wystąpienie jest skompresowany za pomocą algorytmu GZip, zanim informacje są zapisywane w magazynie w trwałości... Ta wartość jest typu `System.Activities.DurableInstancing.InstanceEncodingAction`. Możliwe wartości dla tej właściwości to "None", który określa nie kompresji i "GZip", która określa tego wystąpienia, dane są kompresowane i używa algorytmu gzip.|  
|instanceLockedExceptionAction|Wartość, która określa akcję, która występuje w odpowiedzi na wyjątek zgłaszany, gdy host próbuje zablokować wystąpienia, ponieważ wystąpienie jest zablokowany przez inny host. Ta wartość jest typu <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> Dostępne są następujące opcje w tym polu można używać: Brak, Ponów podstawowy i spróbuj ponownie wykonać skuteczną. Wartość domyślna to Brak. Poniższa lista zawiera opisy tych trzech opcji:<br /><br /> -Brak. Host usługi nie próbuje zablokować wystąpienie i przekazuje <xref:System.Runtime.DurableInstancing.InstanceLockedException> do obiektu wywołującego.<br />-Podstawowe ponów próbę. Host usługi reattempts do blokowania wystąpienie jest interwał ponawiania liniowo i przekazuje wyjątek do obiektu wywołującego na końcu sekwencji.<br />-Agresywne ponów próbę. Host usługi reattempts do blokowania wystąpienie z opóźnieniem wykładniczo zwiększa i przekazuje <xref:System.Runtime.DurableInstancing.InstanceLockedException> do obiektu wywołującego na końcu sekwencji.|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie > z \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Określa zachowanie elementu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>  
 [Magazyn wystąpienia przepływu pracy SQL](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)
