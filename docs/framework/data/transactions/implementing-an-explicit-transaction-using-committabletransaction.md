---
title: Implementowanie jawnych transakcji przy użyciu obiekcie CommittableTransaction
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 29efe5e5-897b-46c2-a35f-e599a273acc8
ms.openlocfilehash: 1edcdefeaafbee3cfbc0810a47e64f38f9f97ddc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-an-explicit-transaction-using-committabletransaction"></a>Implementowanie jawnych transakcji przy użyciu obiekcie CommittableTransaction
<xref:System.Transactions.CommittableTransaction> Klasa umożliwia jawne dla aplikacji, aby używać transakcji, a nie za pomocą <xref:System.Transactions.TransactionScope> klasy niejawnie. Jest to przydatne w przypadku aplikacji, które mają być używane przez wiele wywołań funkcji lub wielu wywołań wątku tej samej transakcji. W odróżnieniu od <xref:System.Transactions.TransactionScope> klasy, moduł zapisujący aplikacji musi w szczególności wywołać <xref:System.Transactions.CommittableTransaction.Commit%2A> i <xref:System.Transactions.Transaction.Rollback%2A> metody, aby zatwierdzić lub przerwać transakcji.  
  
## <a name="overview-of-the-committabletransaction-class"></a>Przegląd klasy CommittableTransaction  
 <xref:System.Transactions.CommittableTransaction> Klasa pochodzi z <xref:System.Transactions.Transaction> klasy, dlatego dostarczanie wszystkich funkcji drugiego. Jest szczególnie przydatna <xref:System.Transactions.Transaction.Rollback%2A> metody w <xref:System.Transactions.Transaction> klasa, która umożliwia także wycofać <xref:System.Transactions.CommittableTransaction> obiektu.  
  
 <xref:System.Transactions.Transaction> Klasa jest podobna do <xref:System.Transactions.CommittableTransaction> klasy, ale nie oferuje `Commit` metody. Umożliwia to przekazania obiektu transakcji (lub klony jego) do innych metod (potencjalnie na inny wątek) przy zachowaniu kontroli nad kiedy transakcja została zatwierdzona. Dzwonić kodu jest w stanie zarejestrować i oddawać głosy na transakcji, ale tylko twórca <xref:System.Transactions.CommittableTransaction> obiekt ma możliwość zatwierdzania transakcji.  
  
 Należy zwrócić uwagę następujących typów podczas pracy z <xref:System.Transactions.CommittableTransaction> klasy,  
  
-   Tworzenie <xref:System.Transactions.CommittableTransaction> transakcji nie ustawiono otoczenia transakcji. Należy w szczególności wartości i zresetować otoczenia transakcji, aby upewnić się, że menedżerów zasobów działają w kontekście transakcji po prawej, w razie potrzeby. Jest sposobem ustawienia bieżącej transakcji otoczenia przez ustawienie statycznego <xref:System.Transactions.Transaction.Current%2A> dla właściwości globalnym <xref:System.Transactions.Transaction> obiektu.  
  
-   Element <xref:System.Transactions.CommittableTransaction> obiektu nie może być używany ponownie. Po <xref:System.Transactions.CommittableTransaction> obiektu została przekazana lub wycofana, nie może być używana ponownie w transakcji. Oznacza to, że nie można ustawić jako bieżący kontekst transakcji otoczenia.  
  
## <a name="creating-a-committabletransaction"></a>Tworzenie CommittableTransaction  
 Poniższy przykład tworzy nową <xref:System.Transactions.CommittableTransaction> i zatwierdza go.  
  
 [!code-csharp[Tx_CommittableTx#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_committabletx/cs/committabletxwithsql.cs#1)]
 [!code-vb[Tx_CommittableTx#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_committabletx/vb/committabletxwithsql.vb#1)]  
  
 Utworzenie wystąpienia <xref:System.Transactions.CommittableTransaction> automatycznie nie ustawiono kontekstu otoczenia transakcji. Dlatego żadnych operacji na Menedżera zasobów nie jest częścią tej transakcji. Statycznych <xref:System.Transactions.Transaction.Current%2A> właściwość globalnej <xref:System.Transactions.Transaction> obiekt jest używany do ustawić lub pobrać transakcja otoczenia i aplikacja musi ustawić ręcznie, aby upewnić się, że Menedżer zasobów mogą uczestniczyć w transakcji. Istnieje również dobrze jest zapisać stary transakcji otoczenia i go przywrócić po zakończeniu za pomocą <xref:System.Transactions.CommittableTransaction> obiektu.  
  
 Aby zatwierdzić transakcji, musisz jawnie wywołać <xref:System.Transactions.CommittableTransaction.Commit%2A> metody. Dla wycofywania transakcji, należy wywołać <xref:System.Transactions.Transaction.Rollback%2A> metody. Należy zauważyć, że do <xref:System.Transactions.CommittableTransaction> została przekazana lub wycofana, wszystkie zasoby zaangażowane w tej transakcji nadal jest zablokowany.  
  
 Element <xref:System.Transactions.CommittableTransaction> obiektu można stosować w przypadku wywołania funkcji i wątków. Jednak jest maksymalnie Deweloper aplikacji do obsługi wyjątków, a w szczególności wywołać <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> metody w przypadku awarii.  
  
## <a name="asynchronous-commit"></a>Zatwierdzanie asynchroniczne  
 <xref:System.Transactions.CommittableTransaction> Klasa zawiera także mechanizm asynchronicznie Zatwierdzanie transakcji. Zatwierdzanie transakcji może zająć sporo czasu, ponieważ mogą dotyczyć, wiele dostęp do bazy danych i opóźnienia sieci. Chce się uniknąć zakleszczenie w aplikacjach wysokiej przepływności, można użyć zatwierdzania asynchronicznego na zakończenie pracy transakcyjnej tak szybko, jak to możliwe i uruchom operację zatwierdzania jako zadania w tle. <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> i <xref:System.Transactions.CommittableTransaction.EndCommit%2A> metody <xref:System.Transactions.CommittableTransaction> klasy pozwalają w tym celu.  
  
 Można wywołać metodę <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> wysłania Napad zatwierdzania do wątków z puli wątków. Można również wywołać <xref:System.Transactions.CommittableTransaction.EndCommit%2A> do określenia, czy transakcja faktycznie została zatwierdzona. Jeśli nie można przekazać z jakiegokolwiek powodu, transakcji <xref:System.Transactions.CommittableTransaction.EndCommit%2A> zgłasza wyjątek transakcji. Jeśli transakcja nie jest jeszcze przekazano do czasu <xref:System.Transactions.CommittableTransaction.EndCommit%2A> jest wywoływana, obiekt wywołujący zostało zablokowane do chwili transakcji nie zostanie przekazana lub zostało przerwane.  
  
 Najprostszym sposobem czy asynchroniczne zatwierdzania jest dostarczając metodę wywołania zwrotnego wywoływana, gdy zatwierdzania zostało zakończone. Jednakże, należy wywołać <xref:System.Transactions.CommittableTransaction.EndCommit%2A> metody w oryginalnym <xref:System.Transactions.CommittableTransaction> obiekt używany do wywoływania połączenie. Uzyskanie ten obiekt umożliwia przypisanie elementu podrzędnego *IAsyncResult* parametru metody wywołania zwrotnego, ponieważ <xref:System.Transactions.CommittableTransaction> klasa implementuje <xref:System.IAsyncResult> klasy.  
  
 W poniższym przykładzie pokazano, jak można zrobić zatwierdzania asynchronicznego.  
  
```csharp  
public void DoTransactionalWork()  
{  
     Transaction oldAmbient = Transaction.Current;  
     CommittableTransaction committableTransaction = new CommittableTransaction();  
     Transaction.Current = committableTransaction;  
  
     try  
     {  
          /* Perform transactional work here */  
          // No errors - commit transaction asynchronously  
          committableTransaction.BeginCommit(OnCommitted,null);  
     }  
     finally  
     {  
          //Restore the ambient transaction   
          Transaction.Current = oldAmbient;  
     }  
}  
void OnCommitted(IAsyncResult asyncResult)  
{  
     CommittableTransaction committableTransaction;  
     committableTransaction = asyncResult as CommittableTransaction;     
     Debug.Assert(committableTransaction != null);  
     try  
     {  
          using(committableTransaction)  
          {  
               committableTransaction.EndCommit(asyncResult);  
          }  
     }  
     catch(TransactionException e)  
     {  
          //Handle the failure to commit  
     }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie transakcji niejawnej przy użyciu zakresu transakcji](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
 [Przetwarzanie transakcji](../../../../docs/framework/data/transactions/index.md)
