---
title: "Trwałość przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 769197b3f59c68c79f94c71c49ba4b1f4f98da2c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-persistence"></a>Trwałość przepływu pracy
Trwałość przepływu pracy jest trwałe przechwytywania stanu wystąpienia przepływu pracy, niezależnie od informacji procesu lub komputera. Jest to zrobić, aby przekazać dobrze znanego punktu odzyskiwania dla wystąpienia przepływu pracy w przypadku awarii systemu lub zachować pamięci przez zwalnianie wystąpienia przepływu pracy, które są aktywnie niewykonania pracy lub przenoszenie stanu wystąpienia przepływu pracy z jednego węzła do innego węzeł w farmie serwerów.  
  
 Trwałość umożliwia elastyczność procesu, skalowalność, odzyskiwania w wypadku awarii i możliwość bardziej wydajnie zarządzać pamięcią. Proces trwałości obejmuje określenie punktu trwałości, zbieranie danych można zapisać i na koniec delegowania rzeczywistego magazynu danych do dostawcy trwałości.  
  
 Włączanie utrwalania przepływu pracy, należy skojarzyć magazyn wystąpienia z **WorkflowApplication** lub **obiektu WorkflowServiceHost** wymienionych w [jak: Włącz trwałość dla Przepływy pracy i przepływ pracy usług](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md). **WorkflowApplication** i **obiektu WorkflowServiceHost** umożliwiają w magazynie wystąpień skojarzonych z nimi utrwalanie wystąpienia przepływu pracy w magazynie informacji o trwałości i ładowanie wystąpienia przepływu pracy do pamięć oparte na dane wystąpienia przepływu pracy, które są przechowywane w magazynie informacji o trwałości.  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Jest dostarczany z **SqlWorkflowInstanceStore** klasy, która zezwala na trwałość danych i metadane dotyczące wystąpienia przepływu pracy w bazie danych programu SQL Server 2005 lub SQL Server 2008. Zobacz [magazyn wystąpienia przepływu pracy SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) więcej szczegółów.  
  
 Do przechowywania i załaduj swoje dane specyficzne dla aplikacji, oraz informacje dotyczące wystąpienia przepływu pracy, można utworzyć uczestników trwałości, które rozszerzają <xref:System.Activities.Persistence.PersistenceParticipant> klasy. Uczestnika trwałości uczestniczy w procesie trwałości można zapisać w magazynie informacji o trwałości, aby załadować dane z magazynu wystąpień w pamięci i wykonywać żadnych dodatkowych logiki w ramach transakcji trwałości niestandardowe dane do serializacji. Aby uzyskać więcej informacji, zobacz [uczestników trwałości](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).  
  
 Windows Server AppFabric upraszcza proces konfigurowania trwałości. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Koncepcji trwałości z systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=201200)  
  
## <a name="implicit-persistence-points"></a>Niejawne punktów trwałości  
 Poniższa lista zawiera przykłady warunków, od których przepływu pracy jest trwały, gdy magazyn wystąpienia jest skojarzony z przepływem pracy.  
  
-   Gdy **TransactionScope** zakończeniu działania lub **TransactedReceiveScope** ukończeniu działania.  
  
-   Kiedy zostanie bezczynne wystąpienia przepływu pracy i **WorkflowIdleBehavior** jest ustawiony na hosta przepływu pracy. Dzieje się tak, na przykład, korzystając z komunikatów działania lub w **opóźnienie** działania.  
  
-   Gdy obiekt WorkflowApplication staje się bezczynności i **PersistableIdle** właściwości aplikacji ustawiono **PersistableIdleAction.Persist**.  
  
-   Gdy aplikacja hosta jest instrukcją utrwalić lub zwolnić wystąpienia przepływu pracy.  
  
-   Jeśli wystąpienia przepływu pracy zostało zakończone lub zakończeniu.  
  
-   Gdy **utrwalanie** wykonuje działania.  
  
-   Gdy wystąpienia przepływu pracy utworzony przy użyciu poprzedniej wersji programu Windows Workflow Foundation napotkał punkt trwałości podczas wykonywania interoperacyjne.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
-   [Magazyn wystąpienia przepływu pracy SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)  
  
-   [Wystąpienie magazynów](../../../docs/framework/windows-workflow-foundation/instance-stores.md)  
  
-   [Uczestnicy trwałości](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)  
  
-   [Najlepsze rozwiązania w zakresie trwałości](../../../docs/framework/windows-workflow-foundation/persistence-best-practices.md)  
  
-   [Wystąpienia-utrwalony przepływu pracy](../../../docs/framework/windows-workflow-foundation/non-persisted-workflow-instances.md)  
  
-   [Wstrzymywanie i wznawianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/pausing-and-resuming-a-workflow.md)
