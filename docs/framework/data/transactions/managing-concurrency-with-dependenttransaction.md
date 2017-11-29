---
title: "Zarządzanie współbieżności z DependentTransaction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6cb0fa7f328b158613836e6ab20bd33545dc3a5d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="managing-concurrency-with-dependenttransaction"></a>Zarządzanie współbieżności z DependentTransaction
<xref:System.Transactions.Transaction> Obiekt zostanie utworzony przy użyciu <xref:System.Transactions.Transaction.DependentClone%2A> metody. Jedynym celem jest zagwarantowanie, że transakcja nie można zatwierdzić podczas innych fragmentów kodu (na przykład wątku roboczego) nadal wykonywania pracy na transakcji. Podczas pracy w ramach transakcji sklonowany jest gotowy do zostać zatwierdzone, może powiadomić twórca przy użyciu transakcji <xref:System.Transactions.DependentTransaction.Complete%2A> metody. W związku z tym można zachować spójności i poprawności danych.  
  
 <xref:System.Transactions.DependentTransaction> Klasy można również zarządzać współbieżności między zadania asynchronicznego. W tym scenariuszu nadrzędnego można kontynuować wykonywania żadnych kodu podczas klon zależny działa na własnych zadań. Innymi słowy wykonywania elementu nadrzędnego nie jest zablokowany do momentu ukończenia zależnego.  
  
## <a name="creating-a-dependent-clone"></a>Tworzenie klon zależny  
 Aby utworzyć zależne transakcji, należy wywołać <xref:System.Transactions.Transaction.DependentClone%2A> metody i przekazać <xref:System.Transactions.DependentCloneOption> wyliczenia jako parametr. Ten parametr określa zachowanie transakcji, jeśli `Commit` jest wywoływana w transakcji nadrzędnej przed klon zależny wskazuje, że jest gotowa na zatwierdzenie transakcji (przez wywołanie metody <xref:System.Transactions.DependentTransaction.Complete%2A> metody). Następujące wartości są prawidłowe dla tego parametru:  
  
-   <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>Tworzy zależnych transakcji, która blokuje proces zatwierdzania transakcji nadrzędnej do czasu transakcji nadrzędnej limit lub do czasu <xref:System.Transactions.DependentTransaction.Complete%2A> zostanie wywołany dla wszystkich zależności wskazujące ich zakończenia. Jest to przydatne, gdy klient nie ma transakcji nadrzędnej można przekazać do momentu zależnych transakcji została ukończona. Jeśli element nadrzędny zakończy pracę starszych niż zależne transakcji i wywołuje <xref:System.Transactions.CommittableTransaction.Commit%2A> dla transakcji, proces zatwierdzania jest zablokowany w stanie, w którym dodatkowe pracy można wykonać na transakcji i można było utworzyć nowe rejestracji, aż wszystkie wywołania zależności <xref:System.Transactions.DependentTransaction.Complete%2A>. Jako ukończony je wszystkie jego pracę, a następnie wywołać <xref:System.Transactions.DependentTransaction.Complete%2A>, rozpocznie się proces zatwierdzania dla transakcji.  
  
-   <xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, z drugiej strony, tworzy zależne transakcji, która automatycznie przerywa Jeśli <xref:System.Transactions.CommittableTransaction.Commit%2A> jest wywoływana w transakcji nadrzędnej przed <xref:System.Transactions.DependentTransaction.Complete%2A> jest wywoływana. W takim przypadku wszystkie prace wykonane w transakcji zależne jest prawidłowa w ramach jednej transakcji okres istnienia i nie jest Państwo przekazać tylko jego części.  
  
 <xref:System.Transactions.DependentTransaction.Complete%2A> Metoda musi zostać wywołana tylko raz, kiedy aplikacja zakończy pracę transakcji zależnych; w przeciwnym razie <xref:System.InvalidOperationException> jest generowany. Po wywołaniu to wywołanie, nie należy spróbować żadnych dodatkowych działań w transakcji lub wyjątku.  
  
 Poniższy przykładowy kod przedstawia sposób tworzenia zależnych transakcji do zarządzania dwóch jednoczesnych zadań w klonowania zależnych transakcji i przekazaniem ich do wątku roboczego.  
  
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
  
 Ponieważ zależne transakcji jest tworzone z <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, ma gwarancji, że nie można zatwierdzić transakcji, aż wszystkie transakcyjnych zadań wykonywanych na sekundę wątek został zakończony i <xref:System.Transactions.DependentTransaction.Complete%2A> jest wywoływana w transakcji zależnych. Oznacza to, że jeśli zakres klienta kończy się (podczas próby usunięcia obiektu transakcji na końcu **przy użyciu** instrukcji) przed nowe wywołania wątku <xref:System.Transactions.DependentTransaction.Complete%2A> zależnych transakcji kodu klienta blokuje do <xref:System.Transactions.DependentTransaction.Complete%2A> jest wywoływana na zależnego. Następnie transakcji może zakończyć przekazywanie lub przerywanie.  
  
## <a name="concurrency-issues"></a>Problemy z współbieżności  
 Istnieje kilka problemów współbieżności dodatkowe, które należy zwrócić uwagę podczas korzystania z <xref:System.Transactions.DependentTransaction> klasy:  
  
-   Jeśli wątku roboczego powoduje wycofanie transakcji, ale nadrzędnego próbuje zatwierdzić, <xref:System.Transactions.TransactionAbortedException> zgłaszany.  
  
-   Należy utworzyć nowy klon zależny dla każdego wątku roboczego w transakcji. Nie przekazuj tego samego klon zależny wiele wątków, ponieważ tylko jeden z nich można wywołać <xref:System.Transactions.DependentTransaction.Complete%2A> na nim.  
  
-   Jeśli wątku roboczego spawns nowego wątku roboczego, upewnij się, że tworzenie klon zależny od klon zależny i przekazywanie ich do nowego wątku.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Transactions.DependentTransaction>
