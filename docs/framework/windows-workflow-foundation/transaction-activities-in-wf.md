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
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="d0a6a-102">Działania transakcji w WF</span><span class="sxs-lookup"><span data-stu-id="d0a6a-102">Transaction Activities in WF</span></span>
<span data-ttu-id="d0a6a-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Ma kilka działań dostarczane przez system do modelowania transakcji, wynagrodzenie i anulowania.</span><span class="sxs-lookup"><span data-stu-id="d0a6a-103">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="d0a6a-104">Tych modeli programowania Zezwalaj na przepływ pracy, aby kontynuować postęp w przypadku zmian w logice biznesowej i obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="d0a6a-104">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> <span data-ttu-id="d0a6a-105">Aby uzyskać więcej informacji o transakcji, wynagrodzenie i anulowania, zobacz [transakcji](workflow-transactions.md), [wynagrodzenie](compensation.md), i [anulowania](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="d0a6a-105">For more information about transactions, compensation, and cancellation, see [Transactions](workflow-transactions.md), [Compensation](compensation.md), and [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="d0a6a-106">Działania transakcji</span><span class="sxs-lookup"><span data-stu-id="d0a6a-106">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="d0a6a-107">Kojarzy logikę anulowania, w postaci działania z głównym ścieżką wykonywania, również jest wyrażona jako działania.</span><span class="sxs-lookup"><span data-stu-id="d0a6a-107">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="d0a6a-108">Obsługuje wynagrodzenie działania podrzędne.</span><span class="sxs-lookup"><span data-stu-id="d0a6a-108">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="d0a6a-109">Jawnie wywołuje procedurę obsługi <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="d0a6a-109">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="d0a6a-110">Jawnie wywołuje procedurę obsługi potwierdzenia <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="d0a6a-110">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="d0a6a-111">Rozgranicza granic transakcji.</span><span class="sxs-lookup"><span data-stu-id="d0a6a-111">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="d0a6a-112">Zakresy okres istnienia transakcji, która jest inicjowane przez odebranego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d0a6a-112">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="d0a6a-113">Transakcja może przekazane do przepływu pracy w komunikacie inicjujący lub utworzonych przez dyspozytor, gdy wiadomość zostaje odebrana.</span><span class="sxs-lookup"><span data-stu-id="d0a6a-113">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="d0a6a-114">**Uwaga:**  <xref:System.ServiceModel.Activities.TransactedReceiveScope> Znajduje się w **komunikatów** części **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="d0a6a-114">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
