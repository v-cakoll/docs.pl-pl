---
title: Trwałość przepływu pracy
description: .NET Framework 4.6.1 zawiera klasę obiekt SqlWorkflowInstanceStore, która umożliwia trwałość danych przepływu pracy i metadanych w SQL Server bazie danych.
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: 1178bd3800fce95be96e601a17bfeff2c05cfceb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419307"
---
# <a name="workflow-persistence"></a>Trwałość przepływu pracy
Trwałość przepływu pracy to trwałe Przechwytywanie stanu wystąpienia przepływu pracy niezależnie od informacji o procesie lub komputerze. W tym celu należy zapewnić dobrze znany punkt odzyskiwania wystąpienia przepływu pracy w przypadku awarii systemu lub zachować pamięć, zwalniając wystąpienia przepływu pracy, które nie działają aktywnie, lub przenieść stan wystąpienia przepływu pracy z jednego węzła do innego w węźle farmy serwerów.  
  
 Trwałość umożliwia elastyczność procesów, skalowalność, odzyskiwanie w miarę awarii oraz możliwość bardziej wydajnego zarządzania pamięcią. Proces trwałości obejmuje identyfikację punktu trwałości, zbieranie danych do zapisania, a wreszcie delegowanie rzeczywistego magazynu danych do dostawcy trwałości.  
  
 Aby włączyć trwałość dla przepływu pracy, należy skojarzyć magazyn wystąpień z obiektem **WorkflowApplication** lub **WorkflowServiceHost** , jak wspomniano w [instrukcje: Włączanie trwałości dla przepływów pracy i usług przepływu pracy](how-to-enable-persistence-for-workflows-and-workflow-services.md). Obiekty **WorkflowApplication** i **WorkflowServiceHost** używają magazynu wystąpień skojarzonego z nimi w celu włączenia utrwalania wystąpień przepływu pracy do magazynu trwałości i ładowania wystąpień przepływu pracy do pamięci na podstawie danych wystąpienia przepływu pracy przechowywanych w magazynie trwałości.  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]Dostarcza z klasą **obiekt SqlWorkflowInstanceStore** , która umożliwia trwałość danych i metadanych o wystąpieniach przepływu pracy w bazie danych SQL Server 2005 lub SQL Server 2008. Aby uzyskać więcej informacji, zobacz [Magazyn wystąpień przepływu pracy SQL](sql-workflow-instance-store.md) .  
  
 Aby przechowywać i ładować dane specyficzne dla aplikacji wraz z informacjami związanymi z wystąpieniem przepływu pracy, można utworzyć uczestników trwałości rozszerzających <xref:System.Activities.Persistence.PersistenceParticipant> klasę. Uczestnik trwałości uczestniczy w procesie trwałości w celu zapisania niestandardowych danych, które można serializować do magazynu trwałości, do załadowania danych z magazynu wystąpień do pamięci oraz do wykonania dodatkowej logiki w ramach transakcji trwałości. Aby uzyskać więcej informacji, zobacz temat [trwałość uczestników](persistence-participants.md).  
  
 Sieć szkieletowa aplikacji systemu Windows Server upraszcza proces konfigurowania trwałości. Aby uzyskać więcej informacji, zobacz [pojęcia dotyczące trwałości przy użyciu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))  
  
## <a name="implicit-persistence-points"></a>Niejawne punkty trwałości  
 Poniższa lista zawiera przykłady warunków, na których przepływ pracy jest utrwalany, gdy magazyn wystąpień jest skojarzony z przepływem pracy.  
  
- Po zakończeniu działania elementu **TransactionScope** lub zakończeniu działania **TransactedReceiveScope** .  
  
- Gdy wystąpienie przepływu pracy stanie się bezczynna, a **WorkflowIdleBehavior** jest ustawiony na hoście przepływu pracy. Dzieje się tak na przykład wtedy, gdy używane są działania dotyczące komunikatów lub **opóźnienia** .  
  
- Gdy obiekt WorkflowApplication stanie się bezczynny, a właściwość **PersistableIdle** aplikacji jest ustawiona na **PersistableIdleAction. utrwalanie**.  
  
- Gdy aplikacja hosta nakazuje utrwalenie lub zwolnienie wystąpienia przepływu pracy.  
  
- Po przerwaniu lub zakończeniu wystąpienia przepływu pracy.  
  
- Gdy działanie **utrwalania** jest wykonywane.  
  
- Gdy wystąpienie przepływu pracy utworzone przy użyciu poprzedniej wersji Windows Workflow Foundation napotka punkt trwałości podczas wykonywania międzyoperacyjnego.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
- [Magazyn wystąpień przepływu pracy SQL](sql-workflow-instance-store.md)  
  
- [Magazyny wystąpień](instance-stores.md)  
  
- [Uczestnicy stanów trwałych](persistence-participants.md)  
  
- [Najlepsze rozwiązania w zakresie stanów trwałych](persistence-best-practices.md)  
  
- [Nietrwałe wystąpienia przepływu pracy](non-persisted-workflow-instances.md)  
  
- [Wstrzymywanie i wznawianie przepływu pracy](pausing-and-resuming-a-workflow.md)
