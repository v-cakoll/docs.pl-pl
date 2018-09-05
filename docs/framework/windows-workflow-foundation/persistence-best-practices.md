---
title: Najlepsze rozwiązania trwałości
ms.date: 03/30/2017
ms.assetid: 6974c5a4-1af8-4732-ab53-7d694608a3a0
ms.openlocfilehash: fdbf61e559efbd978df1c5a46fcbbbbc528ec98a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558878"
---
# <a name="persistence-best-practices"></a>Najlepsze rozwiązania trwałości
W tym dokumencie opisano najlepsze rozwiązania dotyczące projektowania przepływu pracy i konfiguracji związanych z trwałość przepływu pracy.  
  
## <a name="design-and-implementation-of-durable-workflows"></a>Projektowanie i implementacja trwałe przepływy pracy  
 Ogólnie rzecz biorąc przepływy pracy wykonywania pracy w krótkich okresach, które jest przeplatana z czasem, podczas których przepływu pracy jest w stanie bezczynności, ponieważ trwa oczekiwanie na zdarzenie. To zdarzenie może być takich zadań jak wiadomość lub wygasający czasomierza. Aby można było wyładować wystąpienia przepływu pracy, gdy staje się nieaktywna, host usługi musi utrwalić wystąpienia przepływu pracy. Jest to możliwe tylko wtedy, gdy wystąpienie przepływu pracy nie jest w strefie no-persist (na przykład, oczekiwanie na ukończenie transakcji lub oczekujący na asynchroniczne wywołanie zwrotne). Aby umożliwić wystąpienia bezczynności przepływu pracy można zwolnić, autor przepływu pracy należy używać zakresach transakcji i działań asynchronicznych tylko krótkotrwałe akcji. W szczególności Autor należy zachować opóźnienie działań w ramach tych nie utrwalić stref możliwie krótkie.  
  
 Przepływ pracy może być utrwalony tylko w przypadku wszystkich typów danych używane przez przepływ pracy do serializacji. Ponadto, niestandardowe typy używane w przepływach pracy utrwalonych muszą podlegać serializacji z <xref:System.Runtime.Serialization.NetDataContractSerializer> w celu jego utrwalenia przez <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.  
  
 Nie można odzyskać wystąpienia przepływu pracy w przypadku awarii hosta lub komputera, jeśli nie została utrwalona. Ogólnie rzecz biorąc zaleca się utrwalić wystąpienia przepływu pracy na wczesnym etapie cyklu życia przepływu pracy.  
  
 Przepływ pracy jest zajęta przez długi czas, zaleca się że utrwalić wystąpienia przepływu pracy, które regularnie w ciągu okresu zajęty. Można to zrobić, dodając <xref:System.Activities.Statements.Persist> działalności w całej sekwencji działań, które nadal wystąpienia przepływu pracy jest zajęty. W ten sposób domeny aplikacji, odtwarzania, awarii hosta lub komputera błędy nie powodują systemu, aby go z powrotem obniżyć na początku okresu zajęty. Należy pamiętać, że dodanie <xref:System.Activities.Statements.Persist> działań przepływu pracy może prowadzić do pogorszenia wydajności.  
  
 Windows Server AppFabric znacznie upraszcza konfigurację i użycie trwałości. Aby uzyskać więcej informacji, zobacz [systemu Windows Server App Fabric trwałości](https://go.microsoft.com/fwlink/?LinkID=201200&clcid=0x409)  
  
## <a name="configuration-of-scalability-parameters"></a>Konfiguracja parametrów skalowalności  
 Wymagania dotyczące skalowalności i wydajności, określić ustawienia z następujących parametrów:  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A>  
  
 Te parametry należy ustawić następujący, zgodnie z bieżącego scenariusza.  
  
### <a name="scenario-a-small-number-of-workflow-instances-that-require-optimal-response-time"></a>Scenariusz: Małą liczbą wystąpień przepływu pracy, które wymagają czas odpowiedzi optymalne  
 W tym scenariuszu wszystkie wystąpienia przepływu pracy powinna pozostać załadowany, gdy przejdą w stan bezczynności. Ustaw <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na dużą wartość. Użyj tego ustawienia uniemożliwia wystąpienie przepływu pracy przenoszenie między komputerami. Użyj tego ustawienia, tylko wtedy, gdy spełnione są co najmniej jeden z następujących czynności:  
  
-   Wystąpienie przepływu pracy otrzymuje jedną wiadomość w okresie swojego istnienia.  
  
-   Wszystkie wystąpienia przepływu pracy jest uruchamiany na komputerze  
  
-   Wszystkie komunikaty, które są odbierane przez wystąpienie przepływu pracy są odbierane przez tego samego komputera.  
  
 Użyj <xref:System.Activities.Statements.Persist> działania lub zestawu <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> na 0, aby włączyć odzyskiwanie wystąpienia przepływu pracy po awarii usługi hosta lub komputera.  
  
### <a name="scenario-workflow-instances-are-idle-for-long-periods-of-time"></a>Scenariusz: Wystąpienia przepływu pracy są bezczynne przez długi czas  
 W tym scenariuszu należy ustawić <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na 0, aby zwolnić zasoby tak szybko, jak to możliwe.  
  
### <a name="scenario-workflow-instances-receive-multiple-messages-in-a-short-period-of-time"></a>Scenariusz: Wystąpienia przepływu pracy odbierać wiele wiadomości w krótkim czasie  
 W tym scenariuszu należy ustawić <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> do 60 sekund, jeśli te komunikaty są odbierane przez tego samego komputera. Zapobiega to szybkiej sekwencji zwalnianie i ładowanie wystąpienia przepływu pracy. To również nie przechowuje wystąpienia w pamięci zbyt długo.  
  
 Ustaw <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 0 i zestaw <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A> BasicRetry lub AggressiveRetry, jeśli te komunikaty mogą pojawić się na różnych komputerach. Dzięki temu wystąpienie przepływu pracy, które mają być załadowane przez inny komputer.  
  
### <a name="scenario-workflow-uses-delay-activities-with-short-durations"></a>Scenariusz: Przepływ pracy używa działania opóźnienie o krótkim czasie trwania  
 W tym scenariuszu <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> regularnie sonduje baza danych stanów trwałych dla wystąpień, która powinna być załadowany z powodu wygasły <xref:System.Activities.Statements.Delay> działania. Jeśli <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> znajduje czasomierza, która wygaśnie kolejnego interwału sondowania Store wystąpienia przepływu pracy SQL skraca interwału sondowania. Następnie nastąpi dalej sondowania, po prawej, po wygaśnięciu czasomierza. W ten sposób Store wystąpienia przepływu pracy SQL osiąga wysoką dokładność czasomierzy, które działają dłużej niż interwał sondowania, które jest ustawiana przez <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>. Aby włączyć czas przetwarzania krótszych opóźnień, wystąpienie przepływu pracy musi pozostać w pamięci dla co najmniej jeden interwał sondowania.  
  
 Ustaw <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> na 0, aby zapisać czasu wygaśnięcia do bazy danych trwałości.  
  
 Ustaw <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na dłużej niż lub równa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> przechowywania wystąpienia w pamięci do co najmniej jeden interwał sondowania.  
  
 Firma Microsoft nie zaleca się zmniejszenie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> ponieważ prowadzi to do zwiększone obciążenie bazy danych trwałości. Każdy host usługi, który wykorzystuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonduje bazę danych, jeden raz w każdym okresie wykrywania. Ustawienie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> zbyt mały na godzinę interwał może spowodować, że wydajność systemu zmniejszyć w przypadku dużej liczby hostów usługi.  
  
## <a name="configuring-the-sql-workflow-instance-store"></a>Konfigurowanie Store wystąpienia przepływu pracy SQL  
 Store wystąpienia przepływu pracy SQL ma następujące parametry konfiguracji:  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceEncodingOption%2A>  
 Powoduje, że ten parametr <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> do skompresowania stanu wystąpienia przepływu pracy. Kompresja zmniejsza ilość danych, które są przechowywane w bazie danych trwałości i zmniejsza ruch w sieci, w przypadku, gdy baza danych stanów trwałych znajduje się na serwer dedykowany bazy danych. Użycie kompresji wymaga zasoby obliczeniowe, aby kompresowanie i wyodrębnianie kondycja tego wystąpienia. W większości przypadków kompresji daje większą wydajność.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceCompletionAction%2A>  
 Powoduje, że ten parametr <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zachować lub usunąć wystąpienia ukończone. Zachowanie ukończone wystąpienia zwiększa wymagania dotyczące magazynu bazy danych trwałości i prowadzi do większych tabel, co zwiększa tabeli odnośników czasu. Chyba że ukończone wystąpienia są wymagane do debugowania i inspekcji, zaleca się poinstruowanie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> do wystąpień Usuwanie ukończone. Usunięto wystąpienia powinna być ograniczona, tylko wtedy, gdy użytkownik nawiązuje proces po pewnym czasie ich usunięcie. Należy pamiętać, że klucze korelacji nie można użyć ponownie tak długo, jak wystąpienia ukończony przepływ pracy znajduje się w magazynie wystąpienia.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>  
 Ten parametr określa maksymalny interwał, z którym <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonduje baza danych stanów trwałych dla wystąpień, które powinny być załadowane podczas <xref:System.Activities.Statements.Delay> wygasa działanie. Jeśli <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> znajdzie czasomierza, która wygaśnie kolejnego interwału sondowania skraca interwał sondowania, tak aby dalej sondowania nastąpi po prawej, po wygaśnięciu czasomierza. W ten sposób Store wystąpienia przepływu pracy SQL osiąga wysoką dokładność czasomierzy, które działają dłużej niż <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>.  
  
 Firma Microsoft nie zaleca się zmniejszenie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>, ponieważ prowadzi to do zwiększone obciążenie bazy danych trwałości. Każdy host usługi, który wykorzystuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonduje bazę danych, jeden raz w każdym okresie wykrywania. Ustawienie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> na zbyt mały interwał może spowodować wydajność systemu zmniejszyć w przypadku dużej liczby hostów usługi.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>  
 Ten parametr określa interwał, z którym hosta odnawia blokady w bazie danych trwałości. Skrócenie tego interwału umożliwi szybsze odzyskiwanie wystąpienia przepływu pracy, na wypadek awarii hosta lub komputera. Z drugiej strony okres odnowienia blokady krótki zwiększa to obciążenie bazy danych trwałości. Każdy host usługi, który wykorzystuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zaktualizuje jej blokady w bazie danych jeden raz w każdym okresie odnawiania. Jeśli komputer ma zainstalowany wiele hostów usługi, upewnij się, obciążenie spowodowane odnowienia blokady nie zmniejsza wydajność systemu. Jeśli go należy rozważyć zwiększenie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>  
 Jeśli włączona, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> ponownych prób można załadować wystąpienia zablokowane przez następnego 30 sekund. Ustaw <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> BasicRetry lub AggressiveRetry, jeśli przepływ pracy otrzymuje wiele wiadomości w krótkim czasie, a te komunikaty są odbierane przez różne komputery.  
  
 Ponieważ mechanizm ponawiania prób obciążenia nie wprowadza żadnych wydajności obciążenie tak długo, jak długo obciążenie ponownych prób nie są sprawdzane, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> powinien być zawsze włączony.
