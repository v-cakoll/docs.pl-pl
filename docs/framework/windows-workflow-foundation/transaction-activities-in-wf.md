---
title: Działania transakcji w WF
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: 7ffd64abdc6edf45174d4b756833d65ec0ef747c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670264"
---
# <a name="transaction-activities-in-wf"></a>Działania transakcji w WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Ma kilka działań dostarczane przez system do modelowania transakcji, wynagrodzenie i anulowania. Tych modeli programowania Zezwalaj na przepływ pracy, aby kontynuować postęp w przypadku zmian w logice biznesowej i obsługi błędów. Aby uzyskać więcej informacji o transakcji, wynagrodzenie i anulowania, zobacz [transakcji](workflow-transactions.md), [wynagrodzenie](compensation.md), i [anulowania](modeling-cancellation-behavior-in-workflows.md).  
  
## <a name="transaction-activities"></a>Działania transakcji  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|Kojarzy logikę anulowania, w postaci działania z głównym ścieżką wykonywania, również jest wyrażona jako działania.|  
|<xref:System.Activities.Statements.CompensableActivity>|Obsługuje wynagrodzenie działania podrzędne.|  
|<xref:System.Activities.Statements.Compensate>|Jawnie wywołuje procedurę obsługi <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.Confirm>|Jawnie wywołuje procedurę obsługi potwierdzenia <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.TransactionScope>|Rozgranicza granic transakcji.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|Zakresy okres istnienia transakcji, która jest inicjowane przez odebranego komunikatu. Transakcja może przekazane do przepływu pracy w komunikacie inicjujący lub utworzonych przez dyspozytor, gdy wiadomość zostaje odebrana. **Uwaga:**  <xref:System.ServiceModel.Activities.TransactedReceiveScope> Znajduje się w **komunikatów** części **przybornika**.|
