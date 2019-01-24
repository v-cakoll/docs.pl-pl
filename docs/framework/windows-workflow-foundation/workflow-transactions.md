---
title: Transakcje przepływu pracy
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 061cebb6791ada9e3e64097a6490b1e2b4736839
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624222"
---
# <a name="workflow-transactions"></a><span data-ttu-id="f05b2-102">Transakcje przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f05b2-102">Workflow Transactions</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="f05b2-103">zapewnia obsługę uczestnictwa w programie <xref:System.Transactions> transakcji przy użyciu <xref:System.Activities.Statements.TransactionScope> działanie, aby ograniczyć zakres transakcyjne jednostkę pracy.</span><span class="sxs-lookup"><span data-stu-id="f05b2-103">provides support for participating in <xref:System.Transactions> transactions by using the <xref:System.Activities.Statements.TransactionScope> activity to scope a transacted unit of work.</span></span> <span data-ttu-id="f05b2-104">Gdy <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> muszą zostać wykonane w sposób jawny <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> działania niejawnie wywołuje ukończenia transakcji po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="f05b2-104">While the <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> must be explicitly completed the <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> activity implicitly calls complete on the transaction upon successful completion.</span></span> <span data-ttu-id="f05b2-105">Każde działanie, które są zawarte w <xref:System.Activities.Statements.TransactionScope.Body%2A> z <xref:System.Activities.Statements.TransactionScope> działania uczestniczyć w transakcji.</span><span class="sxs-lookup"><span data-stu-id="f05b2-105">Any activities that are contained in the <xref:System.Activities.Statements.TransactionScope.Body%2A> of the <xref:System.Activities.Statements.TransactionScope> activity participate in the transaction.</span></span> <span data-ttu-id="f05b2-106">WF można przepływ transakcji do przepływu pracy za pośrednictwem <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.</span><span class="sxs-lookup"><span data-stu-id="f05b2-106">WF can to flow transactions into a workflow through the use of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="f05b2-107">Podobnie jak <xref:System.Activities.Statements.TransactionScope> aktywności, wszelkich działań zawartych w <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> bierze udział w transakcji.</span><span class="sxs-lookup"><span data-stu-id="f05b2-107">Like the <xref:System.Activities.Statements.TransactionScope> activity, any activity contained in the <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participates in the transaction.</span></span> <span data-ttu-id="f05b2-108">WF gwarantuje, że działań zależnych od ustawień lokalnych na <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> działa zarówno <xref:System.Activities.Statements.TransactionScope> i <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="f05b2-108">WF ensures that activities dependent on <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> works with both <xref:System.Activities.Statements.TransactionScope> and <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="f05b2-109">Jeśli działania dostarczane przez system nie dotyczą wszystkich wymagań, można skompilować niestandardowych działań przy użyciu <xref:System.Activities.RuntimeTransactionHandle> włączyć zaawansowane przepływu i scenariuszy kontroli transakcji.</span><span class="sxs-lookup"><span data-stu-id="f05b2-109">If the system-provided activities do not address all requirements, custom activities can be built using the <xref:System.Activities.RuntimeTransactionHandle> to enable advanced flow and transaction control scenarios.</span></span>  
  
<span data-ttu-id="f05b2-110">W poniższym przykładzie przepływ pracy jest konstruowany składający się z <xref:System.Activities.Statements.Sequence> działania, który zawiera działania podrzędne, w tym <xref:System.Activities.Statements.TransactionScope> działania.</span><span class="sxs-lookup"><span data-stu-id="f05b2-110">In the following example, a workflow is constructed consisting of a <xref:System.Activities.Statements.Sequence> activity that contains child activities including a <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="f05b2-111"><xref:System.Activities.Statements.TransactionScope.Body%2A> Działania <xref:System.Activities.Statements.TransactionScope> wykonywanie w ramach transakcji inicjowane przez <xref:System.Activities.Statements.TransactionScope> działania.</span><span class="sxs-lookup"><span data-stu-id="f05b2-111">The <xref:System.Activities.Statements.TransactionScope.Body%2A> activities of the <xref:System.Activities.Statements.TransactionScope> execute under the transaction initialized by the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
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
  
<span data-ttu-id="f05b2-112">Aby uzyskać więcej informacji, zobacz temat przy użyciu <xref:System.ServiceModel.Activities.TransactedReceiveScope>, zobacz [przepływu transakcji do i z usług przepływu pracy](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="f05b2-112">For more information, see about using <xref:System.ServiceModel.Activities.TransactedReceiveScope>, see [Flowing Transactions into and out of Workflow Services](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f05b2-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f05b2-113">See also</span></span>
- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
