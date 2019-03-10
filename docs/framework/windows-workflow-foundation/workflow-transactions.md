---
title: Transakcje przepływu pracy
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: cb2a72bb24640d214170c52b8b3bf0a328d3f775
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714622"
---
# <a name="workflow-transactions"></a>Transakcje przepływu pracy

[!INCLUDE[wf1](../../../includes/wf1-md.md)] zapewnia obsługę uczestnictwa w programie <xref:System.Transactions> transakcji przy użyciu <xref:System.Activities.Statements.TransactionScope> działanie, aby ograniczyć zakres transakcyjne jednostkę pracy. Gdy <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> muszą zostać wykonane w sposób jawny <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> działania niejawnie wywołuje ukończenia transakcji po pomyślnym zakończeniu. Każde działanie, które są zawarte w <xref:System.Activities.Statements.TransactionScope.Body%2A> z <xref:System.Activities.Statements.TransactionScope> działania uczestniczyć w transakcji. WF można przepływ transakcji do przepływu pracy za pośrednictwem <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. Podobnie jak <xref:System.Activities.Statements.TransactionScope> aktywności, wszelkich działań zawartych w <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> bierze udział w transakcji. WF gwarantuje, że działań zależnych od ustawień lokalnych na <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> działa zarówno <xref:System.Activities.Statements.TransactionScope> i <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Jeśli działania dostarczane przez system nie dotyczą wszystkich wymagań, można skompilować niestandardowych działań przy użyciu <xref:System.Activities.RuntimeTransactionHandle> włączyć zaawansowane przepływu i scenariuszy kontroli transakcji.  
  
W poniższym przykładzie przepływ pracy jest konstruowany składający się z <xref:System.Activities.Statements.Sequence> działania, który zawiera działania podrzędne, w tym <xref:System.Activities.Statements.TransactionScope> działania. <xref:System.Activities.Statements.TransactionScope.Body%2A> Działania <xref:System.Activities.Statements.TransactionScope> wykonywanie w ramach transakcji inicjowane przez <xref:System.Activities.Statements.TransactionScope> działania.  
  
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
  
Aby uzyskać więcej informacji, zobacz temat przy użyciu <xref:System.ServiceModel.Activities.TransactedReceiveScope>, zobacz [przepływu transakcji do i z usług przepływu pracy](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
