---
title: "Działania transakcji w WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b12cfa1cecde648e66872784eb1e353f8c16da8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-activities-in-wf"></a>Działania transakcji w WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Ma kilka działań dostarczane przez system dla modelowania transakcji, kompensacji i anulowania. Te modele programowania Zezwalaj przepływu pracy kontynuować postęp w przypadku zmiany w module logiki biznesowej oraz obsługi błędów. [!INCLUDE[crabout](../../../includes/crabout-md.md)]transakcje, kompensacji i anulowania, zobacz [transakcji](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [kompensacji](../../../docs/framework/windows-workflow-foundation/compensation.md), i [anulowania](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).  
  
## <a name="transaction-activities"></a>Działania transakcji  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|Kojarzy logiki anulowania w formularzu działania z głównym ścieżka wykonywania również wyrażone jako działania.|  
|<xref:System.Activities.Statements.CompensableActivity>|Obsługuje kompensacji działania podrzędne.|  
|<xref:System.Activities.Statements.Compensate>|Jawnie wywołuje procedurę obsługi <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.Confirm>|Jawnie wywołuje procedurę obsługi potwierdzenia <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.TransactionScope>|Rozgranicza granic transakcji.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|Zakresy okres istnienia transakcji inicjowanego przez odebranego komunikatu. Transakcja może przekazane do przepływu pracy w komunikacie inicjujący lub utworzony przez Dyspozytor podczas odbioru wiadomości. **Uwaga:** <xref:System.ServiceModel.Activities.TransactedReceiveScope> znajduje się w **wiadomości** sekcji **przybornika**.|
