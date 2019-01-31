---
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 350ffc2eff94492b43acefd95c71e02f6525d55e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285379"
---
# <a name="sqlworkflowinstancestore"></a>\<sqlWorkflowInstanceStore>
Zachowanie usługi, które pozwala na skonfigurowanie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcji, która obsługuje utrwalanie informacji o stanie dla wystąpień usługi przepływu pracy w bazie danych programu SQL Server 2005 lub SQL Server 2008. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [Store wystąpienia przepływu pracy SQL](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
\<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<sqlWorkflowInstanceStore>  
  
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
|Parametry połączenia|Ciąg, który zawiera ciąg połączenia używany do łączenia z podstawowej bazy danych trwałości.|  
|connectionStringName|Ciąg, który zawiera nazwanych parametrów połączenia z serwerem bazy danych. Przykładem nazwanych parametrów połączenia jest "DefaultConnectionString".|  
|honstLockRenewalPeriod|Wartość przedziału czasu określa okres czasu, w którym hosta musi odnowić blokady w wystąpieniu. Jeśli host nie odnowić blokady w określonym czasie, wystąpienie jest odblokowana i może zostać pobrana przez innego hosta.<br /><br /> Zwalnianie przepływu pracy oznacza również utrwalone. Jeśli ten atrybut jest równa zero wystąpienie przepływu pracy jest trwały i zwolnione natychmiast po przepływ pracy staje się nieaktywna. Ustawienie tego atrybutu na TimeSpan.MaxValue skutecznie wyłącza operacja zwolnienia. Wystąpienia przepływu pracy bezczynności nigdy nie są usuwane.|  
|instanceCompletionAction|Wartość, która określa, czy dane wystąpienia przepływu pracy są przechowywane w magazynie w trwałości po ukończeniu wystąpienie przepływu pracy lub jeśli zostanie usunięta w tym momencie. Ta wartość jest typu <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> Akcje wyliczany składają się z usuwanie dane wystąpienia w trwałości sklepie najbardziej prawdopodobnym nie dane wystąpienia w trwałości sklepie po zakończeniu jego działania wystąpienia.<br /><br /> Przechowywanie wystąpień po ukończenia powoduje, że bazy danych trwałości ze wzrostem jej szybko i ma to wpływ na wydajność bazy danych. Należy skonfigurować zasadę przeczyszczeniu bazy danych, można usunąć te rekordy okresowo, aby upewnić się, że wydajność bazy danych jest na poziomie, które spełniają wymagań dotyczących wydajności.|  
|instanceEncodingOption|Opcjonalna wartość, która określa, czy informacje o stanie wystąpienie jest skompresowany za pomocą algorytmu GZip, zanim informacje są zapisywane w magazynie w trwałości... Ta wartość jest typu `System.Activities.DurableInstancing.InstanceEncodingAction`. Możliwe wartości dla tej właściwości to "None", który określa brak kompresji i "GZip", który określa to wystąpienie danych jest skompresowany i za pomocą algorytmu gzip.|  
|instanceLockedExceptionAction|Wartość, która określa akcję, która występuje w odpowiedzi na wyjątek zgłaszany, gdy host próbuje zablokować wystąpienia, ponieważ wystąpienie jest zablokowany przez inny host. Ta wartość jest typu <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> Dostępne są opcje dozwolone dla tego pola: Brak, Ponów podstawowy i skuteczną ponów próbę. Wartość domyślna to Brak. Poniższa lista zawiera opisy tych trzech opcji:<br /><br /> -Brak. Host usługi nie próbuje zablokować wystąpienie i przekazuje <xref:System.Runtime.DurableInstancing.InstanceLockedException> do obiektu wywołującego.<br />-Podstawowe ponów próbę. Host usługi reattempts do blokowania wystąpienie jest interwał ponawiania liniowo i przekazuje wyjątek do obiektu wywołującego na końcu sekwencji.<br />-Skuteczną ponów próbę. Host usługi reattempts do blokowania wystąpienie z opóźnieniem wykładniczo zwiększa i przekazuje <xref:System.Runtime.DurableInstancing.InstanceLockedException> do obiektu wywołującego na końcu sekwencji.|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie > z \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Określa zachowanie elementu.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [Magazyn wystąpień przepływu pracy SQL](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)
