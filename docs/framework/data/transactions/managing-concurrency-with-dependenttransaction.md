---
title: Zarządzanie współbieżnością za pomocą DependentTransaction
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: a8ddcab4b065c3400f9f9f7ec9ce04befdd0f29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174384"
---
# <a name="managing-concurrency-with-dependenttransaction"></a>Zarządzanie współbieżnością za pomocą DependentTransaction
<xref:System.Transactions.Transaction> Obiekt zostanie utworzony przy użyciu <xref:System.Transactions.Transaction.DependentClone%2A> metody. Jego jedynym celem jest zagwarantowanie, że transakcja nie może zatwierdzić, podczas gdy niektóre inne elementy kodu (na przykład wątek roboczy) nadal wykonują pracę nad transakcją. Po zakończeniu pracy wykonanej w ramach sklonowanej transakcji i gotowości do ich zaagłosowania może powiadomić twórcę transakcji przy użyciu <xref:System.Transactions.DependentTransaction.Complete%2A> metody. W związku z tym można zachować spójności i poprawności danych.  
  
 <xref:System.Transactions.DependentTransaction> Klasy można również zarządzać współbieżności między zadania asynchronicznego. W tym scenariuszu nadrzędnego można kontynuować wykonywania żadnych kodu podczas klon zależny działa na własnych zadań. Innymi słowy wykonanie nadrzędnego nie jest zablokowany, dopóki nie zostanie ukończone zależne.  
  
## <a name="creating-a-dependent-clone"></a>Tworzenie klon zależny  
 Aby utworzyć zależne transakcji, należy wywołać <xref:System.Transactions.Transaction.DependentClone%2A> metody i przekazać <xref:System.Transactions.DependentCloneOption> wyliczenia jako parametr. Ten parametr określa zachowanie transakcji, jeśli `Commit` jest wywoływana w transakcji nadrzędnej przed klon zależny wskazuje, że jest gotowa na zatwierdzenie transakcji (przez wywołanie metody <xref:System.Transactions.DependentTransaction.Complete%2A> metody). Następujące wartości są prawidłowe dla tego parametru:  
  
- <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>tworzy transakcję zależną, która blokuje proces zatwierdzania transakcji nadrzędnej, dopóki nie przesądzi limit czasu transakcji nadrzędnej lub dopóki nie <xref:System.Transactions.DependentTransaction.Complete%2A> zostanie wywołana na wszystkich osobach zależnych wskazujących ich zakończenie. Jest to przydatne, gdy klient nie chce, aby transakcja nadrzędna zatwierdzała się, dopóki transakcje zależne nie zostaną zakończone. Jeśli element nadrzędny zakończy pracę starszych niż zależne transakcji i wywołuje <xref:System.Transactions.CommittableTransaction.Commit%2A> dla transakcji, proces zatwierdzania jest zablokowany w stanie, w którym dodatkowe pracy można wykonać na transakcji i można było utworzyć nowe rejestracji, aż wszystkie wywołania zależności <xref:System.Transactions.DependentTransaction.Complete%2A>. Jako ukończony je wszystkie jego pracę, a następnie wywołać <xref:System.Transactions.DependentTransaction.Complete%2A>, rozpocznie się proces zatwierdzania dla transakcji.  
  
- <xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, z drugiej strony, tworzy transakcję zależną, <xref:System.Transactions.CommittableTransaction.Commit%2A> która automatycznie przerywa, <xref:System.Transactions.DependentTransaction.Complete%2A> jeśli jest wywoływana transakcja nadrzędna przed wywołaniem. W takim przypadku wszystkie prace wykonane w transakcji zależne jest prawidłowa w ramach jednej transakcji okres istnienia i nie jest Państwo przekazać tylko jego części.  
  
 Metoda <xref:System.Transactions.DependentTransaction.Complete%2A> musi być wywoływana tylko raz, gdy aplikacja kończy pracę nad transakcją zależną; w przeciwnym <xref:System.InvalidOperationException> razie jest wyrzucany. Po wywołaniu to wywołanie, nie należy spróbować żadnych dodatkowych działań w transakcji lub wyjątku.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć transakcję zależną do zarządzania dwoma równoczesnymi zadaniami przez klonowanie transakcji zależnej i przekazywanie jej do wątku roboczego.  
  
```csharp  
public class WorkerThread  
{  
    public void DoWork(DependentTransaction dependentTransaction)  
    {  
        Thread thread = new Thread(ThreadMethod);  
        thread.Start(dependentTransaction);
    }  
  
    public void ThreadMethod(object transaction)
    {
        DependentTransaction dependentTransaction = transaction as DependentTransaction;  
        Debug.Assert(dependentTransaction != null);
        try  
        {  
            using(TransactionScope ts = new TransactionScope(dependentTransaction))  
            {  
                /* Perform transactional work here */
                ts.Complete();  
            }  
        }  
        finally  
        {  
            dependentTransaction.Complete();
             dependentTransaction.Dispose();
        }  
    }  
  
//Client code
using(TransactionScope scope = new TransactionScope())  
{  
    Transaction currentTransaction = Transaction.Current;  
    DependentTransaction dependentTransaction;
    dependentTransaction = currentTransaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
    WorkerThread workerThread = new WorkerThread();  
    workerThread.DoWork(dependentTransaction);  
    /* Do some transactional work here, then: */  
    scope.Complete();  
}  
```  
  
 Kod klienta tworzy zakres transakcji, który ustawia również otoczenia transakcji. Transakcja otoczenia nie mają być przekazywane do wątku roboczego. Zamiast tego należy sklonować bieżącej transakcji (otoczenia) przez wywołanie metody <xref:System.Transactions.Transaction.DependentClone%2A> metody w bieżącej transakcji i przekazać zależne od do wątku roboczego.  
  
 `ThreadMethod` Metoda wykonuje na nowy wątek. Klient uruchamia nowy wątek, przekazywania zależne transakcji jako `ThreadMethod` parametru.  
  
 Ponieważ zależne transakcji jest tworzone z <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, ma gwarancji, że nie można zatwierdzić transakcji, aż wszystkie transakcyjnych zadań wykonywanych na sekundę wątek został zakończony i <xref:System.Transactions.DependentTransaction.Complete%2A> jest wywoływana w transakcji zależnych. Oznacza to, że jeśli zakres klienta kończy się (gdy próbuje pozbyć się `using` obiektu transakcji na końcu <xref:System.Transactions.DependentTransaction.Complete%2A> instrukcji) przed nowym wątku <xref:System.Transactions.DependentTransaction.Complete%2A> wywołuje transakcji zależnej, kod klienta blokuje, dopóki nie zostanie wywołana na zależne. Następnie transakcji może zakończyć przekazywanie lub przerywanie.  
  
## <a name="concurrency-issues"></a>Problemy z współbieżności  
 Istnieje kilka problemów współbieżności dodatkowe, które należy zwrócić uwagę podczas korzystania z <xref:System.Transactions.DependentTransaction> klasy:  
  
- Jeśli wątku roboczego powoduje wycofanie transakcji, ale nadrzędnego próbuje zatwierdzić, <xref:System.Transactions.TransactionAbortedException> zgłaszany.  
  
- Należy utworzyć nowy klon zależny dla każdego wątku roboczego w transakcji. Nie należy przekazywać tego samego klonu zależnego do wielu <xref:System.Transactions.DependentTransaction.Complete%2A> wątków, ponieważ tylko jeden z nich może wywołać na nim.  
  
- Jeśli wątku roboczego spawns nowego wątku roboczego, upewnij się, że tworzenie klon zależny od klon zależny i przekazywanie ich do nowego wątku.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Transactions.DependentTransaction>
