---
title: Pobierz WorkflowInstanceId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6e8794be83a80882e2e249c0f774697f6174d0b8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="8753b-102">Pobierz WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="8753b-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="8753b-103">W tym przykładzie przedstawiono sposób użycia to niestandardowe działanie `GetWorkflowInstanceId` do zwrócenia identyfikator wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8753b-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="8753b-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="8753b-104">Demonstrates</span></span>  
 <span data-ttu-id="8753b-105">Programowanie działań niestandardowych, jak uzyskać dostępu do wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8753b-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="8753b-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="8753b-106">Discussion</span></span>  
 <span data-ttu-id="8753b-107">Pobieranie Identyfikatora wystąpienia uruchomiony przepływ pracy wymaga pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="8753b-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="8753b-108">Jeśli chcesz zapisać pełni deklaracyjnego przepływu pracy, należy to działanie, które może zwracać identyfikator wystąpienia przepływu pracy, dzięki czemu można odwoływać się działanie w przepływie pracy, aby zapewnić pełni deklaracyjnego przepływu pracy tworzenia.</span><span class="sxs-lookup"><span data-stu-id="8753b-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="8753b-109">Wiele scenariuszy wymagają dostępu do identyfikator wystąpienia: kilka przykładów dla logowania lub inspekcji lub wykonywania korelacji na poziomie aplikacji, podając identyfikator wystąpienia skojarzenia przyszłych powrót do klienta (na przykład za pomocą tego działania wewnątrz Działanie SendReply).</span><span class="sxs-lookup"><span data-stu-id="8753b-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="8753b-110">`GetWorkflowInstanceId`jest zaimplementowany jako <xref:System.Activities.CodeActivity%601> ponieważ musi zwracać wartość typu <xref:System.Guid>, i musi mieć dostęp do <xref:System.Activities.CodeActivityContext> dla pobierania przepływu pracy wystąpienia identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="8753b-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="8753b-111">Jej implementacja jest dosyć prosta.</span><span class="sxs-lookup"><span data-stu-id="8753b-111">Its implementation is fairly basic.</span></span>  
  
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
>  <span data-ttu-id="8753b-112">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8753b-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8753b-113">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="8753b-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8753b-114">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="8753b-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8753b-115">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8753b-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
