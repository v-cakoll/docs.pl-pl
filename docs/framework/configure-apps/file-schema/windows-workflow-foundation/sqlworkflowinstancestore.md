---
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 7a6f9fb5b2b98d2951343b5a529507b3fcd88dc8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947520"
---
# <a name="sqlworkflowinstancestore"></a>\<sqlWorkflowInstanceStore>
Zachowanie usługi, które umożliwia skonfigurowanie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcji, która obsługuje utrwalanie informacji o stanie dla wystąpień usługi przepływu pracy w bazie danych SQL Server 2005 lub SQL Server 2008. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [Magazyn wystąpień usługi SQL Workflow](../../../windows-workflow-foundation/sql-workflow-instance-store.md).  
  
\<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
\<sqlWorkflowInstanceStore>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sqlWorkflowInstanceStore connectionStringName="String" 
                                hostLockRenewalPeriod="TimeSpan" 
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
|Parametry połączenia|Ciąg zawierający parametry połączenia używane do nawiązania połączenia z podstawową bazą danych trwałości.|  
|connectionStringName|Ciąg, który zawiera nazwane parametry połączenia z serwerem bazy danych. Przykład nazwanego ciągu połączenia to "DefaultConnectionString".|  
|hostLockRenewalPeriod|Wartość przedziału czasu określa okres czasu, w którym hosta musi odnowić blokady w wystąpieniu. Jeśli host nie odnowić blokady w określonym czasie, wystąpienie jest odblokowana i może zostać pobrana przez innego hosta.<br /><br /> Zwalnianie przepływu pracy oznacza, że jest również utrwalone. Jeśli ten atrybut ma wartość zero, wystąpienie przepływu pracy jest utrwalane i zwalniane natychmiast po przejściu przepływu pracy w stan bezczynności. Ustawienie tego atrybutu na TimeSpan. MaxValue skutecznie wyłącza operację Zwolnij. Wystąpienia przepływu pracy bezczynności nigdy nie są usuwane.|  
|instanceCompletionAction|Wartość określająca, czy dane wystąpienia przepływu pracy są przechowywane w magazynie trwałości po zakończeniu działania wystąpienia przepływu pracy lub po jego usunięciu. Ta wartość jest typu <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> Wyliczeniowe akcje polegają na usunięciu danych wystąpienia z magazynu trwałości lub usunięciu danych wystąpienia z magazynu trwałości, gdy wystąpienie zostało zakończone.<br /><br /> Przechowywanie wystąpień po zakończeniu powoduje, że baza danych trwałości zostanie szybko powiększana i ma wpływ na wydajność bazy danych. Należy skonfigurować zasadę przeczyszczeniu bazy danych, można usunąć te rekordy okresowo, aby upewnić się, że wydajność bazy danych jest na poziomie, które spełniają wymagań dotyczących wydajności.|  
|instanceEncodingOption|Opcjonalna wartość, która określa, czy informacje o stanie wystąpienie jest skompresowany za pomocą algorytmu GZip, zanim informacje są zapisywane w magazynie w trwałości... Ta wartość jest typu <xref:System.Activities.DurableInstancing.InstanceEncodingOption>. Możliwe wartości tej właściwości <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None>to, które określają brak kompresji, i <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip>, która określa, że dane wystąpienia są kompresowane i używają algorytmu GZip.|  
|instanceLockedExceptionAction|Wartość, która określa akcję, która występuje w odpowiedzi na wyjątek zgłaszany, gdy host próbuje zablokować wystąpienia, ponieważ wystąpienie jest zablokowany przez inny host. Ta wartość jest typu <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> Opcje dozwolone dla tego pola to: Brak, próba podstawowa i agresywne ponowienie. Wartość domyślna to Brak. Poniższa lista zawiera opisy tych trzech opcji:<br /><br /> Dawaj. Host usługi nie próbuje zablokować wystąpienie i przekazuje <xref:System.Runtime.DurableInstancing.InstanceLockedException> do obiektu wywołującego.<br />-Podstawowa ponowna próba. Host usługi reattempts do blokowania wystąpienie jest interwał ponawiania liniowo i przekazuje wyjątek do obiektu wywołującego na końcu sekwencji.<br />-Agresywne ponawianie próby. Host usługi reattempts do blokowania wystąpienie z opóźnieniem wykładniczo zwiększa i przekazuje <xref:System.Runtime.DurableInstancing.InstanceLockedException> do obiektu wywołującego na końcu sekwencji.|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie > w \<usłudze serviceBehaviors >](behavior-of-servicebehaviors-of-workflow.md)|Określa zachowanie elementu.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [Magazyn wystąpień przepływu pracy SQL](../../../windows-workflow-foundation/sql-workflow-instance-store.md)
