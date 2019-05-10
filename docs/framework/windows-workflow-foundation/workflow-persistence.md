---
title: Trwałość przepływu pracy
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: afe47975a393db3074222ebf0461f5b73fb6442d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655797"
---
# <a name="workflow-persistence"></a>Trwałość przepływu pracy
Trwałość przepływu pracy jest trwały przechwytywania stanu wystąpienia przepływu pracy, niezależnie od informacji proces lub komputer. Ma to na zapewnienie znanego punktu odzyskiwania dla wystąpienia przepływu pracy w przypadku awarii systemu lub zachować pamięci przez zwalnianie wystąpienia przepływu pracy, które nie wykonują aktywnie pracy lub przenieść stanu wystąpienia przepływu pracy z jednego węzła do innego węzeł w farmie serwerów.  
  
 Stan trwały umożliwia procesu elastyczność, skalowalności, odzyskiwania w przypadku awarii i możliwość bardziej wydajne zarządzanie pamięcią. Proces trwałości obejmuje określenie punktu trwałości, zbieranie danych, które mają być zapisywane i na koniec delegowanie rzeczywisty magazyn danych do dostawcy stanów trwałych.  
  
 Aby włączyć opcję trwałości dla przepływu pracy, należy skojarzyć magazyn wystąpienia z **WorkflowApplication** lub **WorkflowServiceHost** zgodnie z opisem w [jak: Włączanie stanów trwałych dla przepływów pracy i usług przepływu pracy](how-to-enable-persistence-for-workflows-and-workflow-services.md). **WorkflowApplication** i **WorkflowServiceHost** umożliwiają magazyn wystąpienia skojarzonych z nimi utrwalanie wystąpienia przepływu pracy w magazynie w trwałości i ładowanie wystąpienia przepływu pracy do pamięć, w oparciu o dane wystąpienia przepływu pracy, które są przechowywane w magazynie w trwałości.  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Jest dostarczany z **SqlWorkflowInstanceStore** klasy, która zezwala na trwałości danych oraz metadane dotyczące wystąpienia przepływu pracy w bazie danych programu SQL Server 2005 lub SQL Server 2008. Zobacz [Store wystąpienia przepływu pracy SQL](sql-workflow-instance-store.md) Aby uzyskać więcej informacji.  
  
 Aby przechowywać i załadować dane specyficzne dla aplikacji wraz z informacjami dotyczącego wystąpienia przepływu pracy, należy utworzyć uczestnicy stanów trwałych, które rozszerzają <xref:System.Activities.Persistence.PersistenceParticipant> klasy. Uczestnika stanów trwałych bierze udział w procesie trwałości zapisanie danych niestandardowych do serializacji w magazynie w trwałości, aby załadować dane z magazynu wystąpień w pamięci i przeprowadzenie dodatkowej logiki w ramach transakcji trwałości. Aby uzyskać więcej informacji, zobacz [uczestnicy stanów trwałych](persistence-participants.md).  
  
 Windows Server AppFabric upraszcza proces konfigurowania trwałości. Aby uzyskać więcej informacji, zobacz [trwałości koncepcji z systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=201200)  
  
## <a name="implicit-persistence-points"></a>Niejawne punktów trwałości  
 Poniższa lista zawiera przykłady warunki, na których jest trwały przepływu pracy, gdy magazyn wystąpienia jest skojarzony z przepływem pracy.  
  
- Gdy **TransactionScope** zakończy działanie lub **TransactedReceiveScope** zakończy działanie.  
  
- Gdy wystąpienie przepływu pracy staje się bezczynności i **WorkflowIdleBehavior** jest ustawiona na hosta przepływu pracy. Ten problem wystąpi, na przykład, gdy używasz działań dotyczących komunikatów lub w **opóźnienie** działania.  
  
- Gdy WorkflowApplication staje się bezczynności i **PersistableIdle** aplikacji zostaje ustalona **PersistableIdleAction.Persist**.  
  
- Gdy aplikacja hosta jest zobowiązany do utrwalenia lub zwolnij wystąpienia przepływu pracy.  
  
- Gdy wystąpienie przepływu pracy zostanie zakończony, lub zakończy się.  
  
- Gdy **utrwalanie** wykonuje działanie.  
  
- Gdy wystąpienie przepływu pracy opracowanych za pomocą poprzedniej wersji programu Windows Workflow Foundation napotyka punktu trwałości podczas wykonywania interoperacyjne.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
- [Magazyn wystąpień przepływu pracy SQL](sql-workflow-instance-store.md)  
  
- [Magazyny wystąpień](instance-stores.md)  
  
- [Uczestnicy stanów trwałych](persistence-participants.md)  
  
- [Najlepsze rozwiązania w zakresie stanów trwałych](persistence-best-practices.md)  
  
- [Nietrwałe wystąpienia przepływu pracy](non-persisted-workflow-instances.md)  
  
- [Wstrzymywanie i wznawianie przepływu pracy](pausing-and-resuming-a-workflow.md)
