---
title: Wycofanie transakcji
ms.date: 03/30/2017
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
ms.openlocfilehash: 15333b159625f07449b0a93634a1a9a854614a57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517160"
---
# <a name="transaction-rollback"></a>Wycofanie transakcji
W tym przykładzie przedstawiono sposób tworzenia niestandardowego <xref:System.Activities.NativeActivity> dostępu do otoczenia <xref:System.Activities.RuntimeTransactionHandle> uzyskać transakcja otoczenia i jawnie wycofać go.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W przepływie pracy, transakcja jest automatycznie zakończona podczas peryferyjnych <xref:System.Activities.Statements.TransactionScope> lub <xref:System.ServiceModel.Activities.TransactedReceiveScope> zakończeniu.  Transakcja przedstawia niejawnie po nieobsługiwany wyjątek propaguje granicy zakresu. Jednak może być czas, kiedy warto jawnie wycofać transakcji bez konieczności Zgłoś wyjątek. W takim przypadku można działania niestandardowe wycofywania jak w tym przykładzie jawnie przerwać transakcję otoczenia i podaj z powodu wyjątku opcjonalne.  
  
 `RollbackActivity` Jest <xref:System.Activities.NativeActivity> ponieważ wymaga dostępu do właściwości wykonywania, aby pobrać otoczenia <xref:System.Activities.RuntimeTransactionHandle>. W `Execute` metody, uzyskuje <xref:System.Activities.RuntimeTransactionHandle> i sprawdza, czy jest `null`, co oznacza, że działanie zostało użyte bez transakcja otoczenia czasu wykonywania. Następnie uzyskuje transakcji, ponownie sprawdzanie czy `null` jest obecny. Istnieje możliwość ma otoczenia <xref:System.Activities.RuntimeTransactionHandle> bez kiedykolwiek inicjowanie transakcja czasu wykonywania. Na koniec przerywa transakcję wywołując <xref:System.Transactions.Transaction.Rollback%2A> i określenia wyjątku dostarczone przez użytkownika lub wyjątek ogólny, stwierdzający, że działanie wycofana transakcji.  
  
 Pokaz przepływ pracy składa się z <xref:System.Activities.Statements.TransactionScope> którego treści Wyświetla stan transakcji przed i po `RollbackActivity` wykonuje. Należy pamiętać, że mimo że transakcja została wycofana, <xref:System.Activities.Statements.TransactionScope> wykonuje się i nie przerwać przepływu pracy do chwili zakończenia treści. Przepływ pracy zostało przerwane, ponieważ <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> wartością domyślną właściwości `true`.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Załadowanie rozwiązania TransactionRollback.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
3.  Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a>Zobacz też  
 [Transakcje](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
