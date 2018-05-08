---
title: Wystąpienie aktywacji
ms.date: 03/30/2017
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
ms.openlocfilehash: a1b78dc62fbdc6e5551addf400ceb14dc9e822f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="instance-activation"></a>Wystąpienie aktywacji
W magazynie wystąpień przepływu pracy SQL uruchamia zadanie wewnętrznego, które okresowo budzi i wykrywa wystąpienia przepływu pracy do uruchomienia lub aktywowalnej w bazie danych trwałości. W przypadku odnalezienia wystąpienia przepływu pracy do uruchomienia, powiadamia hosta przepływu pracy, który jest w stanie aktywacji wystąpienie. Jeśli w magazynie wystąpień znajdzie wystąpienia przepływu pracy aktywowalnej, powiadamia ogólnego hosta, który uaktywnia hosta przepływu pracy, który z kolei uruchamia wystąpienie przepływu pracy. W poniższych sekcjach, w tym temacie opisano proces aktywacji wystąpienia.  
  
##  <a name="RunnableSection"></a> Wykrywanie i aktywowanie wystąpienia przepływu pracy do uruchomienia  
 W magazynie wystąpień przepływu pracy SQL uwzględnia wystąpienia przepływu pracy *do uruchomienia* Jeśli wystąpienie nie jest w stanie wstrzymania lub stanu ukończenia i spełnia następujące warunki:  
  
-   Wystąpienie jest odblokowany, a ma oczekujące czasomierza, który wygasł.  
  
-   Wystąpienie znajdują się wygasłe blokady.  
  
-   Wystąpienie jest odblokowany, a jego stan jest **Executing**.  
  
 W magazynie wystąpień przepływu pracy SQL zgłasza <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> po znalezione wystąpienie do uruchomienia. Dzięki temu obiekt SqlWorkflowInstanceStore Zatrzymuje monitorowanie do <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> jest wywoływana raz w magazynie.  
  
 Hosta przepływu pracy, które zostały zasubskrybowane dla <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> i wykonuje ładowania możliwość wystąpienia <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> przed w magazynie wystąpień, aby załadować wystąpienie do pamięci. Hosta przepływu pracy jest uznawany za stanie ładowanie wystąpienia przepływu pracy, jeśli host i wystąpienia mają właściwości metadanych **WorkflowServiceType** ustawioną taką samą wartość.  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>Wykrywanie i aktywowanie wystąpienia Aktywowalnej przepływu pracy  
 Wystąpienie przepływu pracy jest uznawany za *aktywowalnej* wystąpienie jest do uruchomienia, jeśli ma hosta umożliwiającej ładowanie wystąpienia przepływu pracy jest uruchomiony na komputerze. Zobacz wykrywanie i aktywowanie do uruchomienia wystąpień przepływu pracy nad definicji wystąpienia przepływu pracy do uruchomienia.  
  
 W magazynie wystąpień przepływu pracy SQL zgłasza <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> gdy znajdzie wystąpienia przepływu pracy aktywowalnej w bazie danych. Dzięki temu obiekt SqlWorkflowInstanceStore Zatrzymuje monitorowanie do <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> jest wywoływana raz w magazynie.  
  
 Kiedy host ogólnego subskrybowanych dla <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> odbiera zdarzenia, wykonywania <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> przed w magazynie wystąpień, do uzyskania parametrów aktywacji wymagane do utworzenia hosta przepływu pracy. Ogólny host korzysta z tych parametrów aktywacji można utworzyć hosta przepływu pracy, który z kolei ładuje i uruchamia wystąpienie usługi do uruchomienia.  
  
## <a name="generic-hosts"></a>Ogólny hostów  
 Ogólny host jest hostem o wartość właściwości metadanych **WorkflowServiceType** dla hostów ogólnego ma ustawioną wartość **WorkflowServiceType.Any** aby wskazać, że może obsługiwać dowolny typ przepływu pracy. Ogólny host ma parametr XName o nazwie **ActivationType**.  
  
 Obecnie w magazynie wystąpień przepływu pracy SQL obsługuje ogólnego hosty z wartością parametru ActivationType ustawioną **WAS**. Jeśli nie ustawiono ActivationType do usługi WAS, zgłasza wyjątek w magazynie wystąpień przepływu pracy SQL <xref:System.Runtime.DurableInstancing.InstancePersistenceException>. Usługi zarządzania przepływu pracy, który jest dostarczany z [!INCLUDE[dublin](../../../includes/dublin-md.md)] jest ogólny hosta, który ma typ aktywacji ustawioną **WAS**.  
  
 Aktywacji WAS rodzajowego hosta wymaga zestawu parametrów aktywacji w celu uzyskania adres punktu końcowego, w którym można aktywować nowe hosty. Parametry aktywacji WAS aktywacji są nazwę lokacji, ścieżka do aplikacji względem lokacji i ścieżka do usługi względem aplikacji. Te parametry aktywacji są przechowywane w magazynie wystąpień przepływu pracy SQL podczas wykonywania <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>.  
  
## <a name="runnable-instances-detection-period"></a>Okres wykrywania wystąpień możliwych do uruchomienia  
 **Okres wykrywania wystąpień możliwych do uruchomienia** właściwość w magazynie wystąpień przepływu pracy SQL określa okres czasu, po którym w magazynie wystąpień przepływu pracy SQL uruchamia zadanie wykrywania do wykrywania wszelkich do uruchomienia lub aktywowalnej przepływu pracy wystąpienia w bazie danych trwałości od poprzedniego cyklu wykrywania. Zobacz [okres wykrywania wystąpień możliwych do uruchomienia](../../../docs/framework/windows-workflow-foundation/runnable-instances-detection-period.md) Aby uzyskać więcej informacji na temat tej właściwości.
