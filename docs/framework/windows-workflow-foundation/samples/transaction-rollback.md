---
title: Cofnięcie transakcji
ms.date: 03/30/2017
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
ms.openlocfilehash: 8134623248b072ec5a095ab9b10840e94a09243c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464126"
---
# <a name="transaction-rollback"></a>Cofnięcie transakcji
W tym przykładzie pokazano, jak utworzyć niestandardową <xref:System.Activities.NativeActivity> uzyskuje dostęp otoczenia <xref:System.Activities.RuntimeTransactionHandle> uzyskać otoczenia transakcji i jawnie wycofać je.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 W przepływie pracy, transakcja zostanie automatycznie zakończone, kiedy najbardziej zewnętrzna <xref:System.Activities.Statements.TransactionScope> lub <xref:System.ServiceModel.Activities.TransactedReceiveScope> kończy.  Transakcji przedstawia niejawnie, gdy wystąpił nieobsługiwany wyjątek propagowanie granice zakresu. Jednak może być czasy, kiedy warto jawnie wycofać transakcji bez konieczności zgłoszenie wyjątku. W takim przypadku służy działanie niestandardowe wycofywania, jak ta, w tym przykładzie jawnie przerwać otoczenia transakcji i zapewnia Przyczyna wyjątku opcjonalne.  
  
 `RollbackActivity` Jest <xref:System.Activities.NativeActivity> ponieważ wymaga dostępu do właściwości wykonywania, aby pobrać otoczenia <xref:System.Activities.RuntimeTransactionHandle>. W `Execute` metody uzyskuje <xref:System.Activities.RuntimeTransactionHandle> i sprawdza, czy jest `null`, wskazuje, czy działanie zostało użyte bez otoczenia transakcji czasu wykonywania. Następnie uzyskuje transakcja sprawdzanie ponownie czy `null` jest obecny. Istnieje możliwość mają otoczenia <xref:System.Activities.RuntimeTransactionHandle> bez kiedykolwiek inicjowanie transakcji czasu wykonywania. Na koniec przerywa transakcję, wywołując <xref:System.Transactions.Transaction.Rollback%2A> i określenie wyjątku dostarczone przez użytkownika lub wyjątek ogólny, z informacją, że działanie przywracana transakcji.  
  
 Pokaz przepływu pracy składa się z <xref:System.Activities.Statements.TransactionScope> którego treści Wyświetla stan transakcji przed i po nim `RollbackActivity` wykonuje. Należy pamiętać, że nawet jeśli transakcja została wycofana, <xref:System.Activities.Statements.TransactionScope> wykonuje ukończone i nie przerwać przepływu pracy do chwili zakończenia treści. Przepływ pracy zostało przerwane, ponieważ <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> właściwości wartość domyślna to `true`.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Ładowanie rozwiązania TransactionRollback.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
3.  Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a>Zobacz też  
 [Transakcje](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
