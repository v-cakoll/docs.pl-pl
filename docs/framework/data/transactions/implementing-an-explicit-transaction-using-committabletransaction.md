---
title: Implementowanie transakcji jawnej przy użyciu CommitableTransaction
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 29efe5e5-897b-46c2-a35f-e599a273acc8
ms.openlocfilehash: 18d8a22e20626a30585f556f97b54c65f1ab46a2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645776"
---
# <a name="implementing-an-explicit-transaction-using-committabletransaction"></a>Implementowanie transakcji jawnej przy użyciu CommitableTransaction
<xref:System.Transactions.CommittableTransaction> Klasy zapewnia sposób jawny dla aplikacji używać transakcji, w przeciwieństwie do używania <xref:System.Transactions.TransactionScope> niejawnie klasy. Jest to przydatne w przypadku aplikacji, które chcą korzystać z tej samej transakcji w wielu wywołań funkcji lub wielu wywołań wątku. W odróżnieniu od <xref:System.Transactions.TransactionScope> klasy, Edytor aplikacji musi wywołać specjalnie <xref:System.Transactions.CommittableTransaction.Commit%2A> i <xref:System.Transactions.Transaction.Rollback%2A> metody w celu zatwierdzenia lub przerwania transakcji.  
  
## <a name="overview-of-the-committabletransaction-class"></a>Przegląd klasy CommittableTransaction  
 <xref:System.Transactions.CommittableTransaction> Klasa pochodzi z <xref:System.Transactions.Transaction> klasy, dlatego dostarczanie wszystkich funkcji drugiego. Jest szczególnie przydatna <xref:System.Transactions.Transaction.Rollback%2A> metody w <xref:System.Transactions.Transaction> klasa, która umożliwia także wycofać <xref:System.Transactions.CommittableTransaction> obiektu.  
  
 <xref:System.Transactions.Transaction> Klasa jest podobna do <xref:System.Transactions.CommittableTransaction> klasy, ale nie oferuje `Commit` metody. Umożliwia to przekazania obiektu transakcji (lub klony jego) do innych metod (potencjalnie na inny wątek) przy zachowaniu kontroli nad kiedy transakcja została zatwierdzona. Dzwonić kodu jest w stanie zarejestrować i oddawać głosy na transakcji, ale tylko twórca <xref:System.Transactions.CommittableTransaction> obiekt ma możliwość zatwierdzania transakcji.  
  
 Należy zwrócić uwagę następujących typów podczas pracy z <xref:System.Transactions.CommittableTransaction> klasy,  
  
- Tworzenie <xref:System.Transactions.CommittableTransaction> transakcji nie ustawiono otoczenia transakcji. Należy w szczególności wartości i zresetować otoczenia transakcji, aby upewnić się, że menedżerów zasobów działają w kontekście transakcji po prawej, w razie potrzeby. Jest sposobem ustawienia bieżącej transakcji otoczenia przez ustawienie statycznego <xref:System.Transactions.Transaction.Current%2A> dla właściwości globalnym <xref:System.Transactions.Transaction> obiektu.  
  
- Element <xref:System.Transactions.CommittableTransaction> obiektu nie może być używany ponownie. Po <xref:System.Transactions.CommittableTransaction> obiektu została przekazana lub wycofana, nie może być używana ponownie w transakcji. Oznacza to, że nie można ustawić jako bieżący kontekst transakcji otoczenia.  
  
## <a name="creating-a-committabletransaction"></a>Tworzenie CommittableTransaction  
 Poniższy przykład tworzy nowy <xref:System.Transactions.CommittableTransaction> i zatwierdzeń go.  
  
 [!code-csharp[Tx_CommittableTx#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_committabletx/cs/committabletxwithsql.cs#1)]
 [!code-vb[Tx_CommittableTx#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_committabletx/vb/committabletxwithsql.vb#1)]  
  
 Utworzenie wystąpienia <xref:System.Transactions.CommittableTransaction> automatycznie nie ustawiono kontekstu otoczenia transakcji. Dlatego żadnych operacji na Menedżera zasobów nie jest częścią tej transakcji. Statyczne <xref:System.Transactions.Transaction.Current%2A> dla właściwości globalnym <xref:System.Transactions.Transaction> obiekt jest używany do ustawiania lub pobrać otoczenia transakcji i aplikacji należy ręcznie ustawić ją, aby zapewnić, że menedżerów zasobów mogą uczestniczyć w transakcji. Istnieje również dobrze jest zapisać stary transakcji otoczenia i go przywrócić po zakończeniu za pomocą <xref:System.Transactions.CommittableTransaction> obiektu.  
  
 Aby zatwierdzić transakcji, należy jawnie wywołać <xref:System.Transactions.CommittableTransaction.Commit%2A> metody. Dla wycofywania transakcji, należy wywołać <xref:System.Transactions.Transaction.Rollback%2A> metody. Należy zauważyć, że do <xref:System.Transactions.CommittableTransaction> została przekazana lub wycofana, wszystkie zasoby zaangażowane w tej transakcji nadal jest zablokowany.  
  
 Element <xref:System.Transactions.CommittableTransaction> obiektu można stosować w przypadku wywołania funkcji i wątków. Jednak jest klasą deweloperów aplikacji do obsługi wyjątków i wywołać specjalnie <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> metody w razie awarii.  
  
## <a name="asynchronous-commit"></a>Zatwierdzanie asynchroniczne  
 <xref:System.Transactions.CommittableTransaction> Klasa zawiera także mechanizm asynchronicznie Zatwierdzanie transakcji. Zatwierdzanie transakcji może zająć sporo czasu, jak może obejmować, wielu dostępu do bazy danych i opóźnienie sieci możliwy. W celu uniknięcia zakleszczenia w aplikacjach wymagających dużej przepustowości, należy jak najszybciej ukończenia transakcji pracy przy użyciu asynchronicznej zatwierdzania i uruchom operację zatwierdzania jako zadanie w tle. <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> i <xref:System.Transactions.CommittableTransaction.EndCommit%2A> metody <xref:System.Transactions.CommittableTransaction> klasy pozwalają w tym celu.  
  
 Można wywołać metodę <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> wysłania Napad zatwierdzania do wątków z puli wątków. Można również wywołać <xref:System.Transactions.CommittableTransaction.EndCommit%2A> do określenia, czy transakcja faktycznie została zatwierdzona. Jeśli nie można przekazać z jakiegokolwiek powodu, transakcji <xref:System.Transactions.CommittableTransaction.EndCommit%2A> zgłasza wyjątek transakcji. Jeśli transakcja nie jest jeszcze przekazano do czasu <xref:System.Transactions.CommittableTransaction.EndCommit%2A> jest wywoływana, obiekt wywołujący zostało zablokowane do chwili transakcji nie zostanie przekazana lub zostało przerwane.  
  
 Najprostszym sposobem czy asynchroniczne zatwierdzania jest dostarczając metodę wywołania zwrotnego wywoływana, gdy zatwierdzania zostało zakończone. Jednakże, należy wywołać <xref:System.Transactions.CommittableTransaction.EndCommit%2A> metody w oryginalnym <xref:System.Transactions.CommittableTransaction> obiekt używany do wywoływania połączenie. Uzyskanie z tego obiektu możesz takiej *IAsyncResult* parametru metody wywołania zwrotnego, ponieważ <xref:System.Transactions.CommittableTransaction> klasy implementuje <xref:System.IAsyncResult> klasy.  
  
 Poniższy przykład pokazuje, jak zrobić asynchroniczne zatwierdzania.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie transakcji niejawnej przy użyciu zakresu transakcji](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)
- [Przetwarzanie transakcji](../../../../docs/framework/data/transactions/index.md)
