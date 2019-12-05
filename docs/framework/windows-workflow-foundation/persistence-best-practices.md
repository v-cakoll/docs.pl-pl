---
title: Najlepsze rozwiązania w zakresie stanów trwałych
ms.date: 03/30/2017
ms.assetid: 6974c5a4-1af8-4732-ab53-7d694608a3a0
ms.openlocfilehash: 8ffbb3ebfa8f85e2b0052a9df9ada30766accd8e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802521"
---
# <a name="persistence-best-practices"></a>Najlepsze rozwiązania w zakresie stanów trwałych
W tym dokumencie opisano najlepsze rozwiązania dotyczące projektowania i konfigurowania przepływu pracy związane z trwałością przepływu pracy.  
  
## <a name="design-and-implementation-of-durable-workflows"></a>Projektowanie i wdrażanie trwałych przepływów pracy  
 Ogólnie rzecz biorąc przepływy pracy działają w krótkich okresach, które są przeplatane z czasem, w którym przepływ pracy jest bezczynny, ponieważ oczekuje na zdarzenie. To zdarzenie może być takie jak komunikat lub czasomierz wygasania. Aby można było zwolnić wystąpienie przepływu pracy, gdy stanie się bezczynna, Host usługi musi utrzymywać wystąpienie przepływu pracy. Jest to możliwe tylko wtedy, gdy wystąpienie przepływu pracy nie znajduje się w strefie no-utrwalania (na przykład oczekiwanie na zakończenie transakcji lub oczekiwanie na asynchroniczne wywołanie zwrotne). Aby zezwolić na zwalnianie wystąpienia bezczynnego przepływu pracy, autor przepływu pracy powinien używać zakresów transakcji i działań asynchronicznych tylko dla działań krótkoterminowych. W szczególności autor powinien utrzymywać opóźnienia w tych strefach nietrwałych, tak jak to możliwe.  
  
 Przepływ pracy można utrwalać tylko wtedy, gdy wszystkie typy danych używane przez przepływ pracy są serializowane. Ponadto typy niestandardowe używane w utrwalonych przepływach pracy muszą być możliwe do serializacji z <xref:System.Runtime.Serialization.NetDataContractSerializer>, aby można było je utrwalić przez <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.  
  
 Wystąpienie przepływu pracy nie może zostać odzyskane w przypadku awarii hosta lub komputera, jeśli nie zostało utrwalone. Ogólnie rzecz biorąc zalecamy, aby w cyklu życia przepływu pracy zachować wystąpienie przepływu pracy.  
  
 Jeśli przepływ pracy jest zajęty przez długi czas, zalecamy regularne utrwalanie wystąpienia przepływu pracy w całym okresie jego zajętości. Można to zrobić, dodając <xref:System.Activities.Statements.Persist> działania przez sekwencję działań, które zachowują wystąpienie przepływu pracy. W ten sposób odtwarzanie domen aplikacji, awarie hosta lub awarie komputerów nie powoduje wycofania systemu z powrotem do początku okresu zajętego. Należy pamiętać, że dodanie <xref:System.Activities.Statements.Persist> działań do przepływu pracy może prowadzić do obniżenia wydajności.  
  
 Sieć szkieletowa aplikacji systemu Windows Server znacznie upraszcza konfigurację i użycie trwałości. Aby uzyskać więcej informacji, zobacz [trwałość sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))  
  
## <a name="configuration-of-scalability-parameters"></a>Konfiguracja parametrów skalowalności  
 Wymagania dotyczące skalowalności i wydajności określają ustawienia następujących parametrów:  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>  
  
- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A>  
  
 Parametry te należy ustawić w następujący sposób zgodnie z bieżącym scenariuszem.  
  
### <a name="scenario-a-small-number-of-workflow-instances-that-require-optimal-response-time"></a>Scenariusz: niewielka liczba wystąpień przepływów pracy, które wymagają optymalnego czasu odpowiedzi  
 W tym scenariuszu wszystkie wystąpienia przepływu pracy powinny pozostawać w stanie bezczynności. Ustaw <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na dużą wartość. Użycie tego ustawienia uniemożliwia przechodzenie wystąpienia przepływu pracy między komputerami. Tego ustawienia należy używać tylko w przypadku, gdy co najmniej jeden z następujących warunków jest spełniony:  
  
- Wystąpienie przepływu pracy odbiera pojedynczy komunikat w okresie istnienia.  
  
- Wszystkie wystąpienia przepływu pracy są uruchamiane na pojedynczym komputerze  
  
- Wszystkie komunikaty odbierane przez wystąpienie przepływu pracy są odbierane przez ten sam komputer.  
  
 Użyj działań <xref:System.Activities.Statements.Persist> lub ustaw <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> na 0, aby włączyć odzyskiwanie wystąpienia przepływu pracy po awarii hosta usługi lub komputera.  
  
### <a name="scenario-workflow-instances-are-idle-for-long-periods-of-time"></a>Scenariusz: wystąpienia przepływu pracy są bezczynne przez długi okres czasu  
 W tym scenariuszu Ustaw dla <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> wartość 0, aby jak najszybciej zwolnić zasoby.  
  
### <a name="scenario-workflow-instances-receive-multiple-messages-in-a-short-period-of-time"></a>Scenariusz: wystąpienia przepływu pracy odbierają wiele komunikatów w krótkim czasie  
 W tym scenariuszu Ustaw <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na 60 sekund, jeśli te komunikaty są odbierane przez ten sam komputer. Zapobiega to szybkiemu wyładowaniu i ładowaniu wystąpienia przepływu pracy. Nie zachowuje to również wystąpienia w pamięci zbyt długo.  
  
 Ustaw wartość <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na 0 i ustaw <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A> na BasicRetry lub AggressiveRetry, jeśli te komunikaty mogą być odbierane przez różne komputery. Pozwala to na załadowanie wystąpienia przepływu pracy przez inny komputer.  
  
### <a name="scenario-workflow-uses-delay-activities-with-short-durations"></a>Scenariusz: przepływ pracy używa opóźnień z krótkimi czasami trwania  
 W tym scenariuszu <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> regularnie sonduje trwałość bazy danych dla wystąpień, które powinny być ładowane z powodu wygasłych działań <xref:System.Activities.Statements.Delay>. Jeśli <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> odnajdzie czasomierz, który wygaśnie w następnym interwale sondowania, magazyn wystąpień programu SQL Workflow skraca interwał sondowania. Następne sondowanie będzie odbywać się po wygaśnięciu czasomierza. W ten sposób magazyn wystąpień przepływu pracy SQL osiąga dużą dokładność czasomierzy, które są uruchamiane dłużej niż interwał sondowania ustawiony przez <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>. Aby włączyć czas przetwarzania krótszych opóźnień, wystąpienie przepływu pracy musi pozostawać w pamięci dla co najmniej jednego interwału sondowania.  
  
 Ustaw wartość <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> na 0, aby zapisać czas wygaśnięcia dla bazy danych trwałości.  
  
 Ustaw wartość <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na większą lub równą <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>, aby zachować wystąpienie w pamięci dla co najmniej jednego interwału sondowania.  
  
 Nie zalecamy zredukowania <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>, ponieważ prowadzi to do zwiększonego obciążenia bazy danych trwałości. Każdy host usługi, który używa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonduje bazę danych jeden raz na okres wykrywania. Ustawienie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> na zbyt mały czas przedziału czasu może spowodować spadek wydajności systemu, jeśli liczba hostów usługi jest duża.  
  
## <a name="configuring-the-sql-workflow-instance-store"></a>Konfigurowanie magazynu wystąpień przepływu pracy SQL  
 Magazyn wystąpień przepływu pracy SQL zawiera następujące parametry konfiguracji:  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceEncodingOption%2A>  
 Ten parametr instruuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, aby kompresuje stan wystąpienia przepływu pracy. Kompresja zmniejsza ilość danych przechowywanych w bazie danych trwałości i zmniejsza ruch sieciowy w przypadku, gdy baza danych trwałości znajduje się na dedykowanym serwerze bazy danych. Jeśli kompresja jest używana, wymaga zasobów obliczeniowych w celu kompresowania i wyodrębnienia stanu wystąpienia. W większości przypadków kompresja zapewnia zwiększoną wydajność.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceCompletionAction%2A>  
 Ten parametr nakazuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zachowywania lub usuwania ukończonych wystąpień. Utrzymywanie zakończonych wystąpień zwiększa wymagania dotyczące magazynu bazy danych trwałości i prowadzi do większych tabel, co zwiększa czas wyszukiwania tabeli. Jeśli nie są wymagane żadne ukończone wystąpienia dla debugowania lub inspekcji, najlepiej jest poinstruować <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, aby usunąć ukończone wystąpienia. Usunięte wystąpienia powinny być przechowywane tylko wtedy, gdy użytkownik ustanowi proces, aby ostatecznie je usunąć. Należy zauważyć, że nie można ponownie użyć kluczy korelacji, o ile ukończone wystąpienie przepływu pracy znajduje się w magazynie wystąpień.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>  
 Ten parametr określa maksymalny interwał, za pomocą którego <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonduje trwałość bazy danych dla wystąpień, które powinny być ładowane po wygaśnięciu działania <xref:System.Activities.Statements.Delay>. Jeśli <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> odnajdzie czasomierz, który wygaśnie w następnym interwale sondowania, skraca interwał sondowania, aby następne sondowanie zakończyło się bezpośrednio po wygaśnięciu czasomierza. W ten sposób magazyn wystąpień przepływu pracy SQL osiąga dużą dokładność czasomierzy, które są uruchamiane dłużej niż <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>.  
  
 Nie zalecamy zmniejszenia <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>, ponieważ prowadzi to do zwiększonego obciążenia bazy danych trwałości. Każdy host usługi, który używa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonduje bazę danych jeden raz na okres wykrywania. Ustawienie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> na zbyt mały interwał może spowodować spadek wydajności systemu, jeśli liczba hostów usług jest duża.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>  
 Ten parametr określa interwał, za pomocą którego host odnawia blokadę w bazie danych trwałości. Skrócenie tego interwału umożliwi szybsze odzyskiwanie wystąpień przepływów pracy na wypadek awarii hosta lub komputera. Z drugiej strony, krótki okres odnawiania blokady zwiększa obciążenie bazy danych trwałości. Każdy host usługi, który używa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, zaktualizuje jego blokady w bazie danych o jeden raz na okres odnawiania. Jeśli na komputerze jest uruchomionych wiele hostów usługi, upewnij się, że obciążenie spowodowane odnowieniem blokady nie zmniejsza wydajności systemu. Jeśli tak, rozważ zwiększenie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>  
 Jeśli ta funkcja jest włączona, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> ponawia próbę załadowania zablokowanego wystąpienia przez następne 30 sekund. Ustaw wartość <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> BasicRetry lub AggressiveRetry, jeśli przepływ pracy odbiera wiele komunikatów w krótkim czasie, a te komunikaty są odbierane przez różne komputery.  
  
 Ze względu na to, że mechanizm ponawiania obciążenia nie wprowadza żadnych obciążeń związanych z wydajnością, o ile nie są podejmowane próby załadowania, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> powinny być zawsze włączone.
