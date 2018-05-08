---
title: Najlepsze rozwiązania w zakresie trwałości
ms.date: 03/30/2017
ms.assetid: 6974c5a4-1af8-4732-ab53-7d694608a3a0
ms.openlocfilehash: 68164cc937c1c718df39c96c3d6ac490ab025fae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="persistence-best-practices"></a>Najlepsze rozwiązania w zakresie trwałości
W tym dokumencie opisano najważniejsze wskazówki dotyczące projektowania przepływu pracy i konfiguracji związane z trwałości przepływu pracy.  
  
## <a name="design-and-implementation-of-durable-workflows"></a>Projekt i implementację trwałe przepływów pracy  
 Ogólnie rzecz biorąc przepływy pracy wykonywania pracy w krótkich okresach, gdy jest przeplatana wraz z czasem, w których przepływu pracy jest bezczynny, ponieważ oczekuje na zdarzenie. To zdarzenie może być czynności, takich jak wiadomość lub wygaszenie czasomierza. Aby można było zwolnić wystąpienia przepływu pracy, gdy stanie się bezczynności, hosta usługi musisz utrwalić wystąpienia przepływu pracy. Jest to możliwe tylko wtedy, gdy wystąpienie przepływu pracy nie jest w strefie no-persist (na przykład oczekiwania dla transakcji ukończyć lub Oczekiwanie na asynchroniczne wywołanie zwrotne). Umożliwia wystąpienia przepływu pracy bezczynności zwolnić Autor przepływu pracy należy używać zakresów transakcji oraz działania asynchronicznego tylko tej akcji. W szczególności Autor powinien zachować opóźnienie działań w ramach tych nie utrwalić stref tak krótka jak to możliwe.  
  
 Przepływ pracy mógł być trwały tylko, jeśli są wszystkie typy danych używanych przez przepływ pracy do serializacji. Ponadto niestandardowych typów używanych w utrwalonych przepływów pracy musi być możliwy do serializacji z <xref:System.Runtime.Serialization.NetDataContractSerializer> celu utrwalone przez <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.  
  
 Nie można odzyskać wystąpienia przepływu pracy w przypadku awarii hosta lub komputera, jeśli nie zostały utrwalone. Ogólnie rzecz biorąc zaleca się utrwalenie wystąpienia przepływu pracy wczesnym etapie cyklu życia przepływu pracy.  
  
 Jeśli przepływ pracy jest zajęta przez długi czas, firma Microsoft zaleca, aby utrwalić wystąpienia przepływu pracy regularnie przez cały okres jej zajęty. Można to zrobić przez dodanie <xref:System.Activities.Statements.Persist> działań w całej sekwencji działań, które przechowują zajęty wystąpienia przepływu pracy. W ten sposób domeny aplikacji odtwarzania, awarii hosta lub komputera błędy nie powodują systemu go z powrotem obniżyć na początek okresu zajęty. Należy pamiętać, że dodawanie <xref:System.Activities.Statements.Persist> działań do przepływu pracy może prowadzić do pogorszenia wydajności.  
  
 Windows Server AppFabric znacząco upraszcza konfigurację i użyj trwałości. Aby uzyskać więcej informacji, zobacz [trwałości sieci szkieletowej aplikacji serwera systemu Windows](http://go.microsoft.com/fwlink/?LinkID=201200&clcid=0x409)  
  
## <a name="configuration-of-scalability-parameters"></a>Konfiguracja parametrów skalowalności  
 Skalowalność i wydajność wymagania określają ustawienia następujące parametry:  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>  
  
-   <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A>  
  
 Te parametry powinien być ustawiony w następujący sposób, zgodnie z tym scenariuszu.  
  
### <a name="scenario-a-small-number-of-workflow-instances-that-require-optimal-response-time"></a>Scenariusz: Niewielkiej liczby wystąpień przepływu pracy, które wymagają czas optymalnego odpowiedzi  
 W tym scenariuszu wszystkie wystąpienia przepływu pracy powinna pozostać załadować stają się bezczynności. Ustaw <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> duża wartość. Użycie tego ustawienia uniemożliwia przeniesienie między komputerami wystąpienia przepływu pracy. To ustawienie należy używać tylko wtedy, gdy spełnione są co najmniej jeden z następujących czynności:  
  
-   Wystąpienia przepływu pracy otrzyma pojedynczą wiadomość w całym cyklu eksploatacji.  
  
-   Uruchom wszystkie wystąpienia przepływu pracy na jednym komputerze  
  
-   Wszystkie komunikaty, które są odbierane przez wystąpienie przepływu pracy są odbierane przez ten sam komputer.  
  
 Użyj <xref:System.Activities.Statements.Persist> działania lub zestawu <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> na 0, aby włączyć odzyskiwanie wystąpienia przepływu pracy po awarii hosta lub komputera usługi.  
  
### <a name="scenario-workflow-instances-are-idle-for-long-periods-of-time"></a>Scenariusz: Wystąpienia przepływu pracy są w stanie bezczynności przez długi czas  
 W tym scenariuszu, należy ustawić <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> na 0, aby zwolnić zasoby tak szybko, jak to możliwe.  
  
### <a name="scenario-workflow-instances-receive-multiple-messages-in-a-short-period-of-time"></a>Scenariusz: Wystąpienia przepływu pracy komunikaty wiele w krótkim czasie  
 W tym scenariuszu, należy ustawić <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> do 60 sekund, jeśli te komunikaty są odbierane przez ten sam komputer. Zapobiega to sekwencję szybkie zwalnianie i ładowanie wystąpienia przepływu pracy. To nie należy również wystąpienia w pamięci zbyt długo.  
  
 Ustaw <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 0 i zestawu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior.InstanceLockedExceptionAction%2A> BasicRetry lub AggressiveRetry, jeśli te komunikaty mogą być odbierany przez różnych komputerach. Dzięki temu wystąpienia przepływu pracy, które mają być załadowane przez inny komputer.  
  
### <a name="scenario-workflow-uses-delay-activities-with-short-durations"></a>Scenariusz: Przepływ pracy używa działania opóźnienie z krótki czas  
 W tym scenariuszu <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> regularnie sonduje trwałości bazy danych dla wystąpienia powinna być załadowany z powodu wygasły <xref:System.Activities.Statements.Delay> działania. Jeśli <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> znalezione przez czasomierz, która wygaśnie za dalej interwału sondowania w magazynie wystąpień przepływu pracy SQL skraca interwału sondowania. Następnie nastąpi dalej sondowania, prawej, po wygaśnięciu czasomierza. W ten sposób w magazynie wystąpień przepływu pracy SQL osiąga wysokiej dokładność czasomierzy uruchamianych dłuższy niż interwał sondowania, które jest ustawiana przez <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>. Aby włączyć przetwarzanie odpowiednim krótszych opóźnień, wystąpienie przepływu pracy muszą pozostawać w pamięci dla co najmniej jeden interwał sondowania.  
  
 Ustaw <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> na 0, aby zapisać czas wygaśnięcia w bazie danych trwałości.  
  
 Ustaw <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> dłużej niż lub równa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> przechowywania wystąpienia w pamięci, przez co najmniej jeden interwał sondowania.  
  
 Nie zaleca się zmniejszenie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> ponieważ prowadzi to do zwiększone obciążenie w bazie danych trwałości. Każdy host usługi, który wykorzystuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonduje bazę danych jeden raz w okresie wykrywania. Ustawienie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> za mały na godzinę interwał może spowodować wydajność systemu zmniejszyć w przypadku dużej liczby hostów usługi.  
  
## <a name="configuring-the-sql-workflow-instance-store"></a>Konfigurowanie magazynu wystąpienia przepływu pracy SQL  
 W magazynie wystąpień przepływu pracy SQL ma następujące parametry konfiguracji:  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceEncodingOption%2A>  
 Ten parametr nakazuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> do skompresowania stanu wystąpienia przepływu pracy. Kompresja zmniejsza ilość danych, które są przechowywane w bazie danych trwałości i zmniejsza ruch sieciowy w przypadku bazy danych trwałości, który znajduje się na serwer dedykowany bazy danych. Użycie kompresji wymaga zasoby obliczeniowe do kompresowanie i wyodrębnianie stan wystąpienia. W większości przypadków kompresji powoduje zwiększenie wydajności.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceCompletionAction%2A>  
 Ten parametr nakazuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zachować lub usunąć wystąpienia ukończone. Porządkowania ukończyć wystąpień zwiększa wymagania dotyczące magazynu bazy danych trwałości i prowadzi do większych tabel, co zwiększa tabeli odnośników czasu. Chyba, że ukończono wystąpienia są wymagane do debugowania lub inspekcji, najlepiej poinstruować <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> do wystąpień usuwanie. Usunięto wystąpień powinny być przechowywane tylko, jeśli użytkownik określi proces po pewnym czasie ich usunięcie. Należy pamiętać, że klucze korelacji nie można użyć ponownie tak długo, jak wystąpienia przepływu pracy ukończonych znajduje się w magazynie wystąpień.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>  
 Ten parametr określa maksymalny interwał, z którym <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonduje trwałości bazy danych dla wystąpienia, które powinny być ładowane podczas obliczania <xref:System.Activities.Statements.Delay> wygasa działania. Jeśli <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> znajdzie czasomierza wygaśnie w następnym interwale czasowym sondowania go skraca interwał sondowania, tak aby dalej sondowania nastąpi po prawej, po wygaśnięciu czasomierza. W ten sposób w magazynie wystąpień przepływu pracy SQL osiąga wysokiej dokładność czasomierzy, które mogła trwać dłużej niż <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>.  
  
 Nie zaleca się zmniejszenie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A>, ponieważ prowadzi to do zwiększone obciążenie w bazie danych trwałości. Każdy host usługi, który wykorzystuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sonduje bazę danych jeden raz w okresie wykrywania. Ustawienie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.RunnableInstancesDetectionPeriod%2A> do zbyt mały interwał może spowodować wydajność systemu zmniejszyć w przypadku dużej liczby hostów usługi.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>  
 Ten parametr określa interwał, z którym host odnawia jego blokady w bazie danych trwałości. Skrócić interwał ten umożliwi szybsze odzyskiwania wystąpień przepływu pracy, na wypadek awarii hosta lub komputera. Z drugiej strony okres odnawiania blokady krótkich zwiększa obciążenie bazy danych trwałości. Każdy host usługi, który wykorzystuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zaktualizuje jego blokady w bazie danych jeden raz w każdym okres odnawiania. Gdy komputer działa wiele hostów usługi, upewnij się, że obciążenie spowodowane odnawiania blokady nie można jej zmniejszyć wydajność systemu. Jeśli go należy rozważyć zwiększenie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.HostLockRenewalPeriod%2A>.  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>  
 U możliwia <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> ponownych prób na załadowanie zablokowanym wystąpienia dalej 30 sekund. Ustaw <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> BasicRetry lub AggressiveRetry Jeśli przepływ pracy odbiera wiele komunikatów w krótkim czasie, a te komunikaty są odbierane przez różnych komputerach.  
  
 Ponieważ mechanizm ponawiania obciążenia nie zapewnia żadnych wydajności narzut tak długo, jak ponownych prób obciążenia nie są sprawdzane, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> powinien być zawsze włączony.
