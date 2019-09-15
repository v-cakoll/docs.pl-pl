---
title: Działanie GetWorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: f8bd3205f5b7a4b3bae5203dc90a3c393cedcbdd
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989370"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="1c857-102">Działanie GetWorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="1c857-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="1c857-103">Ten przykład ilustruje sposób użycia działania `GetWorkflowInstanceId` niestandardowego w celu zwrócenia identyfikatora wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1c857-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1c857-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="1c857-104">Demonstrates</span></span>  
 <span data-ttu-id="1c857-105">Niestandardowe programowanie działań, jak uzyskać dostęp do wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1c857-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="1c857-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="1c857-106">Discussion</span></span>  
 <span data-ttu-id="1c857-107">Pobieranie identyfikatora wystąpienia uruchomionego przepływu pracy wymaga napisania kodu.</span><span class="sxs-lookup"><span data-stu-id="1c857-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="1c857-108">Jeśli chcesz napisać całkowicie deklaratywny przepływ pracy, potrzebujesz działania, które może zwrócić identyfikator wystąpienia przepływu pracy, aby można było odwołać się do działania w przepływie pracy, aby zapewnić w pełni deklaracyjne środowisko tworzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1c857-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="1c857-109">Wiele scenariuszy wymaga dostępu do identyfikatora wystąpienia: kilka przykładów służy do rejestrowania lub przeprowadzania inspekcji lub w celu przeprowadzenia korelacji na poziomie aplikacji, dostarczając identyfikator wystąpienia z powrotem do klienta w celu przyszłego skojarzenia (na przykład za pomocą tego działania w ramach Działanie SendReply).</span><span class="sxs-lookup"><span data-stu-id="1c857-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="1c857-110">`GetWorkflowInstanceId`jest zaimplementowany jako <xref:System.Activities.CodeActivity%601> , ponieważ musi zwrócić wartość typu <xref:System.Guid>i <xref:System.Activities.CodeActivityContext> musi mieć dostęp do elementu w celu pobrania identyfikatora wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1c857-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="1c857-111">Jego implementacja jest dość podstawowa.</span><span class="sxs-lookup"><span data-stu-id="1c857-111">Its implementation is fairly basic.</span></span>  
  
```csharp  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
    protected override Guid Execute(CodeActivityContext context)  
    {  
        return context.WorkflowInstanceId;  
    }  
}
```  
  
> [!IMPORTANT]
> <span data-ttu-id="1c857-112">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="1c857-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1c857-113">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="1c857-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="1c857-114">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="1c857-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1c857-115">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1c857-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
