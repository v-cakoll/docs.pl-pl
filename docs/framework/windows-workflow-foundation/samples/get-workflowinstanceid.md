---
title: Działanie getworkflowinstanceid
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 6725ed92bf785e5b7f7d61332944fcce8427388a
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46007285"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="8fa42-102">Działanie getworkflowinstanceid</span><span class="sxs-lookup"><span data-stu-id="8fa42-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="8fa42-103">W tym przykładzie pokazano, jak użyć niestandardowego działania, `GetWorkflowInstanceId` do zwrócenia identyfikatora wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8fa42-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="8fa42-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="8fa42-104">Demonstrates</span></span>  
 <span data-ttu-id="8fa42-105">Tworzenie niestandardowego działania, jak dostęp do wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8fa42-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="8fa42-106">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="8fa42-106">Discussion</span></span>  
 <span data-ttu-id="8fa42-107">Identyfikator wystąpienia uruchomiony przepływ pracy wymaga pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="8fa42-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="8fa42-108">Jeśli chcesz zapisać pełni deklaracyjnego przepływu pracy, należy działanie, które może zwracać identyfikator wystąpienia przepływu pracy, dzięki czemu mogą być przywoływane działania w przepływie pracy, aby zapewnić w pełni deklaracyjnego przepływu pracy tworzenia.</span><span class="sxs-lookup"><span data-stu-id="8fa42-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="8fa42-109">Wiele scenariuszy wymagają dostępu do Identyfikatora wystąpienia: z kilkoma przykładami są rejestrowania lub inspekcji lub wykonując korelacji na poziomie aplikacji, podając identyfikator wystąpienia powrotem do klienta dla przyszłych skojarzenia (na przykład za pomocą tego działania wewnątrz Działanie SendReply).</span><span class="sxs-lookup"><span data-stu-id="8fa42-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="8fa42-110">`GetWorkflowInstanceId` jest implementowany jako <xref:System.Activities.CodeActivity%601> ponieważ aplikacja musi zwracać wartość typu <xref:System.Guid>, i musi mieć dostęp do <xref:System.Activities.CodeActivityContext> w celu uzyskania przepływu pracy wystąpienia identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="8fa42-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="8fa42-111">Jego implementacja jest dosyć.</span><span class="sxs-lookup"><span data-stu-id="8fa42-111">Its implementation is fairly basic.</span></span>  
  
```  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
protected override Guid Execute(CodeActivityContext context)  
        {  
            return context.WorkflowInstanceId;  
        }  
}  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="8fa42-112">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8fa42-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8fa42-113">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="8fa42-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8fa42-114">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="8fa42-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8fa42-115">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8fa42-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
