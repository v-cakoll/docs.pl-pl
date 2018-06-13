---
title: Działania transakcji w WF
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: f2709601fc4fd88a1c5223a5a3e97e139ceca954
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516612"
---
# <a name="transaction-activities-in-wf"></a>Działania transakcji w WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Ma kilka działań dostarczane przez system dla modelowania transakcji, kompensacji i anulowania. Te modele programowania Zezwalaj przepływu pracy kontynuować postęp w przypadku zmiany w module logiki biznesowej oraz obsługi błędów. Aby uzyskać więcej informacji o transakcji, kompensacji i anulowania, zobacz [transakcji](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [kompensacji](../../../docs/framework/windows-workflow-foundation/compensation.md), i [anulowania](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).  
  
## <a name="transaction-activities"></a>Działania transakcji  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|Kojarzy logiki anulowania w formularzu działania z głównym ścieżka wykonywania również wyrażone jako działania.|  
|<xref:System.Activities.Statements.CompensableActivity>|Obsługuje kompensacji działania podrzędne.|  
|<xref:System.Activities.Statements.Compensate>|Jawnie wywołuje procedurę obsługi <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.Confirm>|Jawnie wywołuje procedurę obsługi potwierdzenia <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.TransactionScope>|Rozgranicza granic transakcji.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|Zakresy okres istnienia transakcji inicjowanego przez odebranego komunikatu. Transakcja może przekazane do przepływu pracy w komunikacie inicjujący lub utworzony przez Dyspozytor podczas odbioru wiadomości. **Uwaga:** <xref:System.ServiceModel.Activities.TransactedReceiveScope> znajduje się w **wiadomości** sekcji **przybornika**.|
