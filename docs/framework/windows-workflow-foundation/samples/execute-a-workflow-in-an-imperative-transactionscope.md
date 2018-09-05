---
title: Wykonanie przepływu pracy w elemencie Imperatywnym TransactionScope
ms.date: 03/30/2017
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
ms.openlocfilehash: 2744434e807664ca93b4f5bc27a1f3b89716ce87
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520173"
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a>Wykonanie przepływu pracy w elemencie Imperatywnym TransactionScope
Ten przykład pokazuje sposób wykonywania przepływu pracy przy użyciu <xref:System.Activities.WorkflowInvoker> w obszarze <xref:System.Transactions.Transaction> z kodu C# imperatywnego.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 W C# kodu imperatywnego <xref:System.Transactions.TransactionScope> jest użyty do hermetyzacji zestawu roboczego, który jest wykonywany w ramach tej samej transakcji. <xref:System.Transactions.TransactionScope> Polega na tworzeniu otoczenia transakcji i Inicjowanie <xref:System.Transactions.Transaction.Current%2A> właściwość, która następnie może zostać oceniony przez wszelkie prace wykonywane na tym wątku.  
  
 Aby uzyskać równoważne zachowanie w przepływie pracy, środowisko wykonawcze musi wykonywania dodatkowej pracy inicjowania <xref:System.Transactions.Transaction.Current%2A> przed wykonaniem każdego działania, ponieważ przepływ pracy nie są zachowywane koligacji wątku między działaniami. Dzięki temu środowiska uruchomieniowego, wynikowe zachowanie jest to, że podczas wykonywania przepływu pracy przy użyciu <xref:System.Activities.WorkflowInvoker> wewnątrz <xref:System.Transactions.TransactionScope>, wszystkie działania są gwarantowane, w ramach kontekstu otoczenia transakcji utworzone przez <xref:System.Transactions.TransactionScope>.  
  
 Przepływ pracy może zawierać tylko jednej transakcji otoczenia dla każdego wystąpienia przepływu pracy; Transakcje zagnieżdżone nie są dostępne. Nawet wtedy, gdy przepływ pracy zawiera <xref:System.Activities.Statements.TransactionScope> działania, to nie powoduje utworzenia nowej transakcji wewnętrznej. Zamiast tego należy to ponownie używa transakcji otoczenia, który został utworzony poza przepływu pracy.  
  
 Przykład rozpoczyna nową <xref:System.Transactions.TransactionScope>, wyświetla identyfikator transakcji i rozpoczyna się w przepływie pracy używającym <xref:System.Activities.WorkflowInvoker>. Przepływ pracy drukuje transakcji identyfikator ponownie, pokazujący, że jest tej samej transakcji, a następnie uruchamia <xref:System.Activities.Statements.TransactionScope>, następnie kończy. <xref:System.Activities.WorkflowInvoker.Invoke%2A> Wywołanie na <xref:System.Activities.WorkflowInvoker> jest synchroniczne, oryginalnym wątku blokuje ukończenie przepływu pracy. Po ukończeniu przepływu pracy zakończeniu transakcji, a zasoby usunięte.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ImperativeTransactionSample.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`