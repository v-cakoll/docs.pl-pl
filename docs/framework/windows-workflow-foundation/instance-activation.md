---
title: Aktywacja wystąpienia
ms.date: 03/30/2017
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
ms.openlocfilehash: 41dfc076bdee72c2f4d0c781c6588caa927c740e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641677"
---
# <a name="instance-activation"></a>Aktywacja wystąpienia
Store wystąpienia przepływu pracy SQL uruchamia zadania wewnętrzne, okresowo budzi się i wykrywa wystąpienia przepływu pracy możliwy do uruchomienia lub aktywowalnej w bazie danych trwałości. Jeśli zostaną znalezione wystąpienia możliwy do uruchomienia przepływu pracy, powiadamia hosta przepływu pracy, który jest w stanie aktywacji wystąpienia. Jeśli Magazyn wystąpienia wykryje wystąpienia przepływu pracy aktywowalnej, powiadamia ogólnego hosta, który aktywuje hosta przepływu pracy, który z kolei uruchamia wystąpienie przepływu pracy. W poniższych sekcjach w tym temacie opisano proces aktywacji wystąpienia szczegółowo.  
  
## <a name="RunnableSection"></a> Wykrywanie i aktywowanie wystąpienia możliwy do uruchomienia przepływu pracy  
 Store wystąpienia przepływu pracy SQL traktuje wystąpienie przepływu pracy *możliwy do uruchomienia* Jeśli wystąpienie nie jest w stanie wstrzymania lub stanu ukończenia, a także spełnia następujące warunki:  
  
- Wystąpienie jest odblokowana i ma oczekujące czasomierza, który wygasł.  
  
- Wystąpienie ma blokadę wygasła.  
  
- Wystąpienie jest odblokowana i jego stan to **Executing**.  
  
 Wywołuje Store wystąpienia przepływu pracy SQL <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> gdy znajdzie możliwe do uruchomienia wystąpienia. Po tym SqlWorkflowInstanceStore Zatrzymuje monitorowanie aż do momentu <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> jest wywoływana jeden raz w sklepie.  
  
 Hosta przepływu pracy, które zostały zasubskrybowane przez dla <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> i możliwością ładowania uruchamia wystąpienie <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> względem magazynu wystąpienia, aby załadować wystąpienia do pamięci. Hosta przepływu pracy jest uznawany za stanie ładowanie wystąpienia przepływu pracy, jeśli host i wystąpienia ma właściwość metadanych **WorkflowServiceType** ustawić taką samą wartość.  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>Wykrywanie i aktywowanie wystąpienia Aktywowalnej przepływu pracy  
 Wystąpienie przepływu pracy jest uważany za *aktywowalnej* wystąpienie jest możliwy do uruchomienia, jeśli ma nie hosta przepływu pracy, który jest w stanie ładowanie wystąpienia jest uruchomiona na komputerze. Znajdują się wykrywanie i aktywowanie wystąpień możliwych do uruchomienia przepływu pracy nad definicją wystąpienia możliwy do uruchomienia przepływu pracy.  
  
 Wywołuje Store wystąpienia przepływu pracy SQL <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> gdy znajdzie wystąpienie aktywowalnej przepływu pracy w bazie danych. Po tym SqlWorkflowInstanceStore Zatrzymuje monitorowanie aż do momentu <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> jest wywoływana jeden raz w sklepie.  
  
 Gdy ogólny hosta, który ma subskrypcję dla <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> odbiera zdarzenia, wykonuje <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> względem magazynu wystąpienia, aby uzyskać parametry aktywacji wymagane do utworzenia hosta przepływu pracy. Ogólny hosta korzysta z tych parametrów aktywacji w celu utworzenia hosta przepływu pracy, który z kolei ładuje i uruchamia wystąpienie możliwy do uruchomienia usługi.  
  
## <a name="generic-hosts"></a>Ogólny hostów  
 Ogólny host jest hostem z wartością właściwości metadanych **WorkflowServiceType** ogólnego hostów jest równa **WorkflowServiceType.Any** do wskazania, że może obsługiwać dowolny typ przepływu pracy. Host ogólnego ma parametr XName o nazwie **ActivationType**.  
  
 Obecnie usługa Store wystąpienia przepływu pracy SQL obsługuje ogólny hostów przy użyciu wartości parametru ActivationType równa **WAS**. Jeśli nie ustawiono ActivationType WAS, zgłasza Store wystąpienia przepływu pracy SQL <xref:System.Runtime.DurableInstancing.InstancePersistenceException>. Usługa zarządzania przepływu pracy, który jest dostarczany z [!INCLUDE[dublin](../../../includes/dublin-md.md)] jest ogólny hosta, który ma ustawiony typ aktywacji **WAS**.  
  
 W celu aktywacji WAS ogólnego hosta wymaga zestawu parametrów aktywacji w celu uzyskania adresu punktu końcowego, w którym można aktywować nowe hosty. Parametry aktywacji WAS aktywacji są nazwę lokacji, ścieżka do aplikacji względem lokacji oraz ścieżkę usługi względem aplikacji. Store wystąpienia przepływu pracy SQL przechowuje te parametry aktywacji podczas wykonywania <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>.  
  
## <a name="runnable-instances-detection-period"></a>Okres wykrywania wystąpień możliwych do uruchomienia  
 **Możliwy do uruchomienia okres wykrywania wystąpień** właściwość Store wystąpienia przepływu pracy SQL określa okres czasu, po upływie którego Store wystąpienia przepływu pracy SQL uruchamia zadanie wykrywania, aby wykrywać wszelkie możliwe do uruchomienia lub aktywowalnej przepływu pracy wystąpień w bazie danych trwałości od poprzedniego cyklu wykrywania. Zobacz [możliwy do uruchomienia okres wykrywania wystąpień](runnable-instances-detection-period.md) Aby uzyskać więcej informacji na temat tej właściwości.
