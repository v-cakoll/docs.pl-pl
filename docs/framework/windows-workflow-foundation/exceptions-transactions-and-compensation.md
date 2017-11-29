---
title: "Wyjątki, transakcje i kompensacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be803580a4d8ed195222e5960cfa6e26804d91c5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="0aaec-102">Wyjątki, transakcje i kompensacji</span><span class="sxs-lookup"><span data-stu-id="0aaec-102">Exceptions, Transactions, and Compensation</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="0aaec-103">udostępnia kilka różnych mechanizmów obsługi błędów czasu wykonywania w przepływach pracy.</span><span class="sxs-lookup"><span data-stu-id="0aaec-103"> provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="0aaec-104">Przepływy pracy można użyć kombinacji programów obsługi wyjątków, transakcje, anulowanie i kompensacji obsługi i powrócić do poprawnego działania z błędów.</span><span class="sxs-lookup"><span data-stu-id="0aaec-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0aaec-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0aaec-105">In This Section</span></span>  
 [<span data-ttu-id="0aaec-106">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="0aaec-106">Exceptions</span></span>](../../../docs/framework/windows-workflow-foundation/exceptions.md)  
 <span data-ttu-id="0aaec-107">Pokazuje, jak używać <xref:System.Activities.Statements.TryCatch> działanie obsługi wyjątków w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="0aaec-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="0aaec-108">Transakcje</span><span class="sxs-lookup"><span data-stu-id="0aaec-108">Transactions</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)  
 <span data-ttu-id="0aaec-109">Pokazuje, jak używać <xref:System.Activities.Statements.TransactionScope> działania, aby móc używać transakcji w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="0aaec-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="0aaec-110">Kompensacji</span><span class="sxs-lookup"><span data-stu-id="0aaec-110">Compensation</span></span>](../../../docs/framework/windows-workflow-foundation/compensation.md)  
 <span data-ttu-id="0aaec-111">W tym artykule opisano kompensacji w przepływach pracy i pokazuje, jak używać kompensacji działania, takich jak <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, i <xref:System.Activities.Statements.Confirm>.</span><span class="sxs-lookup"><span data-stu-id="0aaec-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="0aaec-112">Anulowanie</span><span class="sxs-lookup"><span data-stu-id="0aaec-112">Cancellation</span></span>](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="0aaec-113">Opisuje sposób wykonywania anulowania obsługi w przepływach pracy przy użyciu działań wbudowanych, jak również działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="0aaec-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="0aaec-114">Debugowanie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="0aaec-114">Debugging Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/debugging-workflows.md)  
 <span data-ttu-id="0aaec-115">Opisuje sposób debugowania przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="0aaec-115">Describes how to debug workflows.</span></span>
