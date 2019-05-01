---
title: Wyjątki, transakcje i kompensacja
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: c4d66e252561ad7b896ff8092e80013c51bd463c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774013"
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="9c71c-102">Wyjątki, transakcje i kompensacja</span><span class="sxs-lookup"><span data-stu-id="9c71c-102">Exceptions, Transactions, and Compensation</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="9c71c-103">udostępnia kilka różnych mechanizmów obsługi błędów czasu wykonywania w przepływach pracy.</span><span class="sxs-lookup"><span data-stu-id="9c71c-103">provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="9c71c-104">Przepływy pracy można użyć kombinacji programów obsługi wyjątków, transakcje, anulowanie i rekompensaty do obsługi i powrócić do poprawnego działania z warunków błędów.</span><span class="sxs-lookup"><span data-stu-id="9c71c-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c71c-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9c71c-105">In This Section</span></span>  
 [<span data-ttu-id="9c71c-106">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="9c71c-106">Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="9c71c-107">Pokazuje sposób użycia <xref:System.Activities.Statements.TryCatch> działania, aby obsłużyć wyjątki w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="9c71c-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="9c71c-108">Transakcje</span><span class="sxs-lookup"><span data-stu-id="9c71c-108">Transactions</span></span>](workflow-transactions.md)  
 <span data-ttu-id="9c71c-109">Pokazuje sposób użycia <xref:System.Activities.Statements.TransactionScope> działania, aby móc używać transakcji w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="9c71c-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="9c71c-110">Kompensacja</span><span class="sxs-lookup"><span data-stu-id="9c71c-110">Compensation</span></span>](compensation.md)  
 <span data-ttu-id="9c71c-111">W tym artykule opisano rekompensaty w przepływach pracy i pokazuje, jak używać takich jak działania Kompensacja <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, i <xref:System.Activities.Statements.Confirm>.</span><span class="sxs-lookup"><span data-stu-id="9c71c-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="9c71c-112">Anulowanie</span><span class="sxs-lookup"><span data-stu-id="9c71c-112">Cancellation</span></span>](modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="9c71c-113">W tym artykule opisano sposób wykonywania anulowania obsługi w przepływach pracy za pomocą wbudowanych działań, a także działania niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="9c71c-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="9c71c-114">Debugowanie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="9c71c-114">Debugging Workflows</span></span>](debugging-workflows.md)  
 <span data-ttu-id="9c71c-115">Opisuje sposób debugowania przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="9c71c-115">Describes how to debug workflows.</span></span>
