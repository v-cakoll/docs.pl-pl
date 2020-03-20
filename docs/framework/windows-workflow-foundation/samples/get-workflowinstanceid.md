---
title: Działanie GetWorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 8cb83fcf15b814b0ca6f7f95f1a9b8eec70185cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142735"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="66b24-102">Działanie GetWorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="66b24-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="66b24-103">W tym przykładzie pokazano, jak `GetWorkflowInstanceId` używać działania niestandardowego, aby zwrócić identyfikator wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="66b24-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="66b24-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="66b24-104">Demonstrates</span></span>  
 <span data-ttu-id="66b24-105">Niestandardowe tworzenie działań, jak uzyskać dostęp do wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="66b24-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="66b24-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="66b24-106">Discussion</span></span>  
 <span data-ttu-id="66b24-107">Uzyskanie identyfikatora wystąpienia uruchomionego przepływu pracy wymaga zapisu kodu.</span><span class="sxs-lookup"><span data-stu-id="66b24-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="66b24-108">Jeśli chcesz napisać w pełni deklaratywny przepływ pracy, potrzebujesz działania, które może zwrócić identyfikator wystąpienia przepływu pracy, aby można było odwoływać się do działania w przepływie pracy, aby zapewnić w pełni deklaratywne środowisko tworzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="66b24-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="66b24-109">Wiele scenariuszy wymaga dostępu do identyfikatora wystąpienia: kilka przykładów dotyczy rejestrowania lub inspekcji lub wykonywania korelacji na poziomie aplikacji przez podanie identyfikatora wystąpienia z powrotem do klienta dla przyszłego skojarzenia (na przykład przy użyciu tego działania wewnątrz działania SendReply).</span><span class="sxs-lookup"><span data-stu-id="66b24-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="66b24-110">`GetWorkflowInstanceId`jest implementowany <xref:System.Activities.CodeActivity%601> jako, ponieważ musi zwracać wartość typu <xref:System.Guid>i <xref:System.Activities.CodeActivityContext> musi mieć dostęp do uzyskiwania identyfikatora wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="66b24-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="66b24-111">Jego wdrożenie jest dość proste.</span><span class="sxs-lookup"><span data-stu-id="66b24-111">Its implementation is fairly basic.</span></span>  
  
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
> <span data-ttu-id="66b24-112">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="66b24-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="66b24-113">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="66b24-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="66b24-114">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="66b24-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="66b24-115">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="66b24-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
