---
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 56a44fdb62062903ca3ad00f8105a66ccab02cca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151965"
---
# <a name="sqlworkflowinstancestore"></a>\<sqlWorkflowInstanceStore>
Zachowanie usługi, które umożliwia skonfigurowanie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcji, która obsługuje utrwalanie informacji o stanie wystąpień usługi przepływu pracy w bazie danych PROGRAMU SQL Server 2005 lub SQL Server 2008. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [Magazyn wystąpień przepływu pracy SQL](../../../windows-workflow-foundation/sql-workflow-instance-store.md).  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<zachowania>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<usługiZachowady>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>zachowania**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sqlWorkflowInstanceStore>**  
  
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
|Parametry połączenia|Ciąg, który zawiera parametry połączenia używane do łączenia się z podstawowej bazy danych trwałości.|  
|connectionStringName|Ciąg zawierający nazwany ciąg połączenia z serwerem bazy danych. Przykładem nazwanego ciągu połączenia jest "DefaultConnectionString".|  
|hostLockRenewalWydajoda|Wartość przedziału czasu określa okres czasu, w którym hosta musi odnowić blokady w wystąpieniu. Jeśli host nie odnowić blokady w określonym czasie, wystąpienie jest odblokowana i może zostać pobrana przez innego hosta.<br /><br /> Zwalnianie przepływu pracy oznacza, że jest również utrwalony. Jeśli ten atrybut jest ustawiony na zero, wystąpienie przepływu pracy jest utrwalone i zwalniane natychmiast po tym, jak przepływ pracy stanie się bezczynny. Ustawienie tego atrybutu na TimeSpan.MaxValue skutecznie wyłącza operację zwalniania. Wystąpienia przepływu pracy bezczynności nigdy nie są usuwane.|  
|instancjaCompletionAction|Wartość określająca, czy dane wystąpienia przepływu pracy są przechowywane w magazynie trwałości po zakończeniu wystąpienia przepływu pracy, czy też są usuwane w tym momencie. Ta wartość jest typu <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> Wyliczone akcje obejmują usunięcie danych wystąpienia z magazynu trwałości lub nie usunięcie danych wystąpienia z magazynu trwałości, gdy wystąpienie zakończyło działanie.<br /><br /> Utrzymywanie wystąpień po zakończeniu powoduje, że baza danych trwałości szybko rośnie, co wpływa na wydajność bazy danych. Należy skonfigurować zasadę przeczyszczeniu bazy danych, można usunąć te rekordy okresowo, aby upewnić się, że wydajność bazy danych jest na poziomie, które spełniają wymagań dotyczących wydajności.|  
|instanceEncodingOption|Opcjonalna wartość, która określa, czy informacje o stanie wystąpienie jest skompresowany za pomocą algorytmu GZip, zanim informacje są zapisywane w magazynie w trwałości... Ta wartość jest typu <xref:System.Activities.DurableInstancing.InstanceEncodingOption>. Możliwe wartości dla <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None>tej właściwości są , <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip>który określa brak kompresji i , który określa, że dane wystąpienia jest skompresowany i używa algorytmu gzip.|  
|instanceLockedExceptionAction|Wartość, która określa akcję, która występuje w odpowiedzi na wyjątek zgłaszany, gdy host próbuje zablokować wystąpienia, ponieważ wystąpienie jest zablokowany przez inny host. Ta wartość jest typu <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> Dostępne są następujące opcje w tym polu można używać: Brak, Ponów podstawowy i spróbuj ponownie wykonać skuteczną. Wartość domyślna to Brak. Poniższa lista zawiera opisy tych trzech opcji:<br /><br /> - Brak. Host usługi nie próbuje zablokować wystąpienie i przekazuje <xref:System.Runtime.DurableInstancing.InstanceLockedException> do obiektu wywołującego.<br />- Podstawowe ponowienie próby. Host usługi reattempts do blokowania wystąpienie jest interwał ponawiania liniowo i przekazuje wyjątek do obiektu wywołującego na końcu sekwencji.<br />- Agresywne ponowienie próby. Host usługi reattempts do blokowania wystąpienie z opóźnieniem wykładniczo zwiększa i przekazuje <xref:System.Runtime.DurableInstancing.InstanceLockedException> do obiektu wywołującego na końcu sekwencji.|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie> \<usługZachod>](behavior-of-servicebehaviors-of-workflow.md)|Określa zachowanie elementu.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [Magazyn wystąpień przepływu pracy SQL](../../../windows-workflow-foundation/sql-workflow-instance-store.md)
