---
title: Transakcje przepływu pracy
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 223c18195c8ffd0b51eb5dff77aa81953f6e47a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182675"
---
# <a name="workflow-transactions"></a><span data-ttu-id="8e993-102">Transakcje przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8e993-102">Workflow Transactions</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="8e993-103">zapewnia wsparcie dla <xref:System.Transactions> uczestnictwa w transakcjach przy użyciu <xref:System.Activities.Statements.TransactionScope> działania do zakresu transakcji jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="8e993-103">provides support for participating in <xref:System.Transactions> transactions by using the <xref:System.Activities.Statements.TransactionScope> activity to scope a transacted unit of work.</span></span> <span data-ttu-id="8e993-104">Podczas <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> gdy musi być <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> jawnie zakończone działanie niejawnie wywołuje zakończyć transakcję po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="8e993-104">While the <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> must be explicitly completed the <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> activity implicitly calls complete on the transaction upon successful completion.</span></span> <span data-ttu-id="8e993-105">Wszelkie działania, które są <xref:System.Activities.Statements.TransactionScope.Body%2A> zawarte <xref:System.Activities.Statements.TransactionScope> w działania uczestniczyć w transakcji.</span><span class="sxs-lookup"><span data-stu-id="8e993-105">Any activities that are contained in the <xref:System.Activities.Statements.TransactionScope.Body%2A> of the <xref:System.Activities.Statements.TransactionScope> activity participate in the transaction.</span></span> <span data-ttu-id="8e993-106">WF można przepływać transakcje do przepływu pracy <xref:System.ServiceModel.Activities.TransactedReceiveScope> za pomocą działania.</span><span class="sxs-lookup"><span data-stu-id="8e993-106">WF can to flow transactions into a workflow through the use of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="8e993-107">Podobnie <xref:System.Activities.Statements.TransactionScope> jak działanie, wszelkie działania <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> zawarte w uczestnicy transakcji.</span><span class="sxs-lookup"><span data-stu-id="8e993-107">Like the <xref:System.Activities.Statements.TransactionScope> activity, any activity contained in the <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participates in the transaction.</span></span> <span data-ttu-id="8e993-108">WF zapewnia, że działania <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> zależne <xref:System.Activities.Statements.TransactionScope> <xref:System.ServiceModel.Activities.TransactedReceiveScope>od prac z obu i .</span><span class="sxs-lookup"><span data-stu-id="8e993-108">WF ensures that activities dependent on <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> works with both <xref:System.Activities.Statements.TransactionScope> and <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="8e993-109">Jeśli działania dostarczone przez system nie spełniają wszystkich wymagań, działania niestandardowe mogą być tworzone przy <xref:System.Activities.RuntimeTransactionHandle> użyciu, aby włączyć zaawansowane scenariusze kontroli przepływu i transakcji.</span><span class="sxs-lookup"><span data-stu-id="8e993-109">If the system-provided activities do not address all requirements, custom activities can be built using the <xref:System.Activities.RuntimeTransactionHandle> to enable advanced flow and transaction control scenarios.</span></span>  
  
<span data-ttu-id="8e993-110">W poniższym przykładzie przepływ pracy jest <xref:System.Activities.Statements.Sequence> skonstruowany składający się <xref:System.Activities.Statements.TransactionScope> z działania, które zawiera działania podrzędne, w tym działania.</span><span class="sxs-lookup"><span data-stu-id="8e993-110">In the following example, a workflow is constructed consisting of a <xref:System.Activities.Statements.Sequence> activity that contains child activities including a <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="8e993-111">Działania <xref:System.Activities.Statements.TransactionScope.Body%2A> wykonania w <xref:System.Activities.Statements.TransactionScope> ramach transakcji zainicjowane <xref:System.Activities.Statements.TransactionScope> przez działanie.</span><span class="sxs-lookup"><span data-stu-id="8e993-111">The <xref:System.Activities.Statements.TransactionScope.Body%2A> activities of the <xref:System.Activities.Statements.TransactionScope> execute under the transaction initialized by the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
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
  
<span data-ttu-id="8e993-112">Aby uzyskać więcej informacji, zobacz temat używania <xref:System.ServiceModel.Activities.TransactedReceiveScope>usług przepływu do i z usług przepływu [pracy](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="8e993-112">For more information, see about using <xref:System.ServiceModel.Activities.TransactedReceiveScope>, see [Flowing Transactions into and out of Workflow Services](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e993-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e993-113">See also</span></span>

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
