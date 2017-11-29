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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f6132f1d9cbeef3ed7af5d2b711d04e8bd5755bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="c7323-102">Działania transakcji w WF</span><span class="sxs-lookup"><span data-stu-id="c7323-102">Transaction Activities in WF</span></span>
<span data-ttu-id="c7323-103">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Ma kilka działań dostarczane przez system dla modelowania transakcji, kompensacji i anulowania.</span><span class="sxs-lookup"><span data-stu-id="c7323-103">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="c7323-104">Te modele programowania Zezwalaj przepływu pracy kontynuować postęp w przypadku zmiany w module logiki biznesowej oraz obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="c7323-104">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="c7323-105">transakcje, kompensacji i anulowania, zobacz [transakcji](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [kompensacji](../../../docs/framework/windows-workflow-foundation/compensation.md), i [anulowania](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="c7323-105"> transactions, compensation, and cancellation, see [Transactions](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [Compensation](../../../docs/framework/windows-workflow-foundation/compensation.md), and [Cancellation](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="c7323-106">Działania transakcji</span><span class="sxs-lookup"><span data-stu-id="c7323-106">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="c7323-107">Kojarzy logiki anulowania w formularzu działania z głównym ścieżka wykonywania również wyrażone jako działania.</span><span class="sxs-lookup"><span data-stu-id="c7323-107">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="c7323-108">Obsługuje kompensacji działania podrzędne.</span><span class="sxs-lookup"><span data-stu-id="c7323-108">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="c7323-109">Jawnie wywołuje procedurę obsługi <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="c7323-109">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="c7323-110">Jawnie wywołuje procedurę obsługi potwierdzenia <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="c7323-110">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="c7323-111">Rozgranicza granic transakcji.</span><span class="sxs-lookup"><span data-stu-id="c7323-111">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="c7323-112">Zakresy okres istnienia transakcji inicjowanego przez odebranego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="c7323-112">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="c7323-113">Transakcja może przekazane do przepływu pracy w komunikacie inicjujący lub utworzony przez Dyspozytor podczas odbioru wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c7323-113">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="c7323-114">**Uwaga:** <xref:System.ServiceModel.Activities.TransactedReceiveScope> znajduje się w **wiadomości** sekcji **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="c7323-114">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
