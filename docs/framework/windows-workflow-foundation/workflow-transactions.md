---
title: "Transakcje przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d9cc01d929421b8065a3df21374150bc68fd968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-transactions"></a><span data-ttu-id="572e0-102">Transakcje przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="572e0-102">Workflow Transactions</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="572e0-103">zapewnia obsługę uczestniczących w <xref:System.Transactions> transakcji przy użyciu <xref:System.Activities.Statements.TransactionScope> działania do określania zakresu transakcyjne jednostkę pracy.</span><span class="sxs-lookup"><span data-stu-id="572e0-103"> provides support for participating in <xref:System.Transactions> transactions by using the <xref:System.Activities.Statements.TransactionScope> activity to scope a transacted unit of work.</span></span> <span data-ttu-id="572e0-104">Gdy <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> muszą być wypełnione jawnie <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> niejawnie wywołania ukończyć działania transakcji po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="572e0-104">While the <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> must be explicitly completed the <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> activity implicitly calls complete on the transaction upon successful completion.</span></span> <span data-ttu-id="572e0-105">Żadnych działań, które są zawarte w <xref:System.Activities.Statements.TransactionScope.Body%2A> z <xref:System.Activities.Statements.TransactionScope> działania uczestniczyć w transakcji.</span><span class="sxs-lookup"><span data-stu-id="572e0-105">Any activities that are contained in the <xref:System.Activities.Statements.TransactionScope.Body%2A> of the <xref:System.Activities.Statements.TransactionScope> activity participate in the transaction.</span></span> <span data-ttu-id="572e0-106">WF można przepływ transakcji w przepływie pracy za pośrednictwem <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="572e0-106">WF can to flow transactions into a workflow through the use of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="572e0-107">Podobnie jak <xref:System.Activities.Statements.TransactionScope> działania, wszystkie działania zawarte w <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> uczestniczy w transakcji.</span><span class="sxs-lookup"><span data-stu-id="572e0-107">Like the <xref:System.Activities.Statements.TransactionScope> activity, any activity contained in the <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participates in the transaction.</span></span> <span data-ttu-id="572e0-108">WF zapewnia zależnych od tego działania na <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> działa z obiema <xref:System.Activities.Statements.TransactionScope> i <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="572e0-108">WF ensures that activities dependent on <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> works with both <xref:System.Activities.Statements.TransactionScope> and <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="572e0-109">Jeśli działania dostarczane przez system nie dotyczą wszystkich wymagań, działań niestandardowych można skonstruować za pomocą <xref:System.Activities.RuntimeTransactionHandle> umożliwiające przepływ zaawansowane i scenariuszy kontroli transakcji.</span><span class="sxs-lookup"><span data-stu-id="572e0-109">If the system-provided activities do not address all requirements, custom activities can be built using the <xref:System.Activities.RuntimeTransactionHandle> to enable advanced flow and transaction control scenarios.</span></span>  
  
 <span data-ttu-id="572e0-110">W poniższym przykładzie pobierana z [podstawowego elementu TransactionScope](../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md) przykładowy przepływ pracy jest tworzony, składające się z <xref:System.Activities.Statements.Sequence> działanie, które występują działania podrzędne, w tym <xref:System.Activities.Statements.TransactionScope> działania.</span><span class="sxs-lookup"><span data-stu-id="572e0-110">In the following example, taken from the [Basic TransactionScope](../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md) sample, a workflow is constructed consisting of a <xref:System.Activities.Statements.Sequence> activity that contains child activities including a <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="572e0-111"><xref:System.Activities.Statements.TransactionScope.Body%2A> Działania <xref:System.Activities.Statements.TransactionScope> wykonać w obrębie transakcji zainicjowane przez <xref:System.Activities.Statements.TransactionScope> działania.</span><span class="sxs-lookup"><span data-stu-id="572e0-111">The <xref:System.Activities.Statements.TransactionScope.Body%2A> activities of the <xref:System.Activities.Statements.TransactionScope> execute under the transaction initialized by the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
```csharp  
static Activity ScenarioOne()  
{  
    return new Sequence  
    {  
        Activities =  
        {  
            new WriteLine { Text = "    Begin workflow" },  
  
            new TransactionScope  
            {  
                Body = new Sequence  
                {  
                    Activities =   
                    {  
                        new WriteLine { Text = "    Begin TransactionScope" },  
  
                        new PrintTransactionId(),  
  
                        new TransactionScopeTest(),  
  
                        new WriteLine { Text = "    End TransactionScope" },  
                    },  
                },  
            },  
  
            new WriteLine { Text = "    End workflow" },  
        }  
    };  
}  
```  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="572e0-112">podstawowe [transakcji](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) przykłady oraz scenariusz na podstawie [transakcji](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) próbek.</span><span class="sxs-lookup"><span data-stu-id="572e0-112"> the basic [Transactions](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) samples, and the scenario based [Transactions](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) samples.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="572e0-113">o używaniu <xref:System.ServiceModel.Activities.TransactedReceiveScope>, zobacz [przepływu transakcji do i z usług przepływu pracy](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="572e0-113"> about using <xref:System.ServiceModel.Activities.TransactedReceiveScope>, see [Flowing Transactions into and out of Workflow Services](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="572e0-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="572e0-114">See Also</span></span>  
 <xref:System.Activities.Statements.TransactionScope>  
 <xref:System.Transactions.TransactionScope>  
 <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
