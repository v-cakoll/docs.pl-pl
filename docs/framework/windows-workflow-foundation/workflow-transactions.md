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
# <a name="workflow-transactions"></a>Transakcje przepływu pracy

[!INCLUDE[wf1](../../../includes/wf1-md.md)]zapewnia wsparcie dla <xref:System.Transactions> uczestnictwa w transakcjach przy użyciu <xref:System.Activities.Statements.TransactionScope> działania do zakresu transakcji jednostki pracy. Podczas <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> gdy musi być <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> jawnie zakończone działanie niejawnie wywołuje zakończyć transakcję po pomyślnym zakończeniu. Wszelkie działania, które są <xref:System.Activities.Statements.TransactionScope.Body%2A> zawarte <xref:System.Activities.Statements.TransactionScope> w działania uczestniczyć w transakcji. WF można przepływać transakcje do przepływu pracy <xref:System.ServiceModel.Activities.TransactedReceiveScope> za pomocą działania. Podobnie <xref:System.Activities.Statements.TransactionScope> jak działanie, wszelkie działania <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> zawarte w uczestnicy transakcji. WF zapewnia, że działania <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> zależne <xref:System.Activities.Statements.TransactionScope> <xref:System.ServiceModel.Activities.TransactedReceiveScope>od prac z obu i . Jeśli działania dostarczone przez system nie spełniają wszystkich wymagań, działania niestandardowe mogą być tworzone przy <xref:System.Activities.RuntimeTransactionHandle> użyciu, aby włączyć zaawansowane scenariusze kontroli przepływu i transakcji.  
  
W poniższym przykładzie przepływ pracy jest <xref:System.Activities.Statements.Sequence> skonstruowany składający się <xref:System.Activities.Statements.TransactionScope> z działania, które zawiera działania podrzędne, w tym działania. Działania <xref:System.Activities.Statements.TransactionScope.Body%2A> wykonania w <xref:System.Activities.Statements.TransactionScope> ramach transakcji zainicjowane <xref:System.Activities.Statements.TransactionScope> przez działanie.  
  
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
  
Aby uzyskać więcej informacji, zobacz temat używania <xref:System.ServiceModel.Activities.TransactedReceiveScope>usług przepływu do i z usług przepływu [pracy](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
