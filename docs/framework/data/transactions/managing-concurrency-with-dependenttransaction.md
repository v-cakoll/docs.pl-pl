---
title: Zarządzanie współbieżnością za pomocą DependentTransaction
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: 8de7cc6257317ff7128f25968a9dcf80ae5af89d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040428"
---
# <a name="managing-concurrency-with-dependenttransaction"></a><span data-ttu-id="44f12-102">Zarządzanie współbieżnością za pomocą DependentTransaction</span><span class="sxs-lookup"><span data-stu-id="44f12-102">Managing Concurrency with DependentTransaction</span></span>
<span data-ttu-id="44f12-103"><xref:System.Transactions.Transaction> Obiekt zostanie utworzony przy użyciu <xref:System.Transactions.Transaction.DependentClone%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="44f12-103">The <xref:System.Transactions.Transaction> object is created using the <xref:System.Transactions.Transaction.DependentClone%2A> method.</span></span> <span data-ttu-id="44f12-104">Jedynym celem jest zagwarantowanie, że transakcja nie może zostać zatwierdzona, a niektóre inne fragmenty kodu (na przykład wątek roboczy) nadal wykonują prace nad transakcją.</span><span class="sxs-lookup"><span data-stu-id="44f12-104">Its sole purpose is to guarantee that the transaction cannot commit while some other pieces of code (for example, a worker thread) are still performing work on the transaction.</span></span> <span data-ttu-id="44f12-105">Gdy działanie wykonane w ramach sklonowanej transakcji zostanie ukończone i gotowe do zatwierdzenia, może powiadomić twórcę transakcji przy użyciu metody <xref:System.Transactions.DependentTransaction.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="44f12-105">When the work done within the cloned transaction is complete and ready to be committed, it can notify the creator of the transaction using the <xref:System.Transactions.DependentTransaction.Complete%2A> method.</span></span> <span data-ttu-id="44f12-106">W związku z tym można zachować spójności i poprawności danych.</span><span class="sxs-lookup"><span data-stu-id="44f12-106">Thus, you can preserve the consistency and correctness of data.</span></span>  
  
 <span data-ttu-id="44f12-107"><xref:System.Transactions.DependentTransaction> Klasy można również zarządzać współbieżności między zadania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="44f12-107">The <xref:System.Transactions.DependentTransaction> class can also be used to manage concurrency between asynchronous tasks.</span></span> <span data-ttu-id="44f12-108">W tym scenariuszu nadrzędnego można kontynuować wykonywania żadnych kodu podczas klon zależny działa na własnych zadań.</span><span class="sxs-lookup"><span data-stu-id="44f12-108">In this scenario, the parent can continue to execute any code while the dependent clone works on its own tasks.</span></span> <span data-ttu-id="44f12-109">Innymi słowy, wykonanie elementu nadrzędnego nie jest blokowane do momentu zakończenia zależnego.</span><span class="sxs-lookup"><span data-stu-id="44f12-109">In other words, the parent's execution is not blocked until the dependent completes.</span></span>  
  
## <a name="creating-a-dependent-clone"></a><span data-ttu-id="44f12-110">Tworzenie klon zależny</span><span class="sxs-lookup"><span data-stu-id="44f12-110">Creating a Dependent Clone</span></span>  
 <span data-ttu-id="44f12-111">Aby utworzyć zależne transakcji, należy wywołać <xref:System.Transactions.Transaction.DependentClone%2A> metody i przekazać <xref:System.Transactions.DependentCloneOption> wyliczenia jako parametr.</span><span class="sxs-lookup"><span data-stu-id="44f12-111">To create a dependent transaction, call the <xref:System.Transactions.Transaction.DependentClone%2A> method and pass the <xref:System.Transactions.DependentCloneOption> enumeration as a parameter.</span></span> <span data-ttu-id="44f12-112">Ten parametr określa zachowanie transakcji, jeśli `Commit` jest wywoływana w transakcji nadrzędnej przed klon zależny wskazuje, że jest gotowa na zatwierdzenie transakcji (przez wywołanie metody <xref:System.Transactions.DependentTransaction.Complete%2A> metody).</span><span class="sxs-lookup"><span data-stu-id="44f12-112">This parameter defines the behavior of the transaction if `Commit` is called on the parent transaction before the dependent clone indicates that it is ready for the transaction to commit (by calling the <xref:System.Transactions.DependentTransaction.Complete%2A> method).</span></span> <span data-ttu-id="44f12-113">Następujące wartości są prawidłowe dla tego parametru:</span><span class="sxs-lookup"><span data-stu-id="44f12-113">The following values are valid for this parameter:</span></span>  
  
- <span data-ttu-id="44f12-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> tworzy transakcję zależną, która blokuje proces zatwierdzania transakcji nadrzędnych do momentu przełączenia transakcji nadrzędnej lub do momentu wywołania <xref:System.Transactions.DependentTransaction.Complete%2A> na wszystkich zależnościach wskazujących ich zakończenie.</span><span class="sxs-lookup"><span data-stu-id="44f12-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> creates a dependent transaction that blocks the commit process of the parent transaction until the parent transaction times out, or until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on all dependents indicating their completion.</span></span> <span data-ttu-id="44f12-115">Jest to przydatne, gdy klient nie chce, aby transakcja nadrzędna została zatwierdzona do momentu zakończenia transakcji zależnych.</span><span class="sxs-lookup"><span data-stu-id="44f12-115">This is useful when the client does not want the parent transaction to commit until the dependent transactions have completed.</span></span> <span data-ttu-id="44f12-116">Jeśli element nadrzędny zakończy pracę starszych niż zależne transakcji i wywołuje <xref:System.Transactions.CommittableTransaction.Commit%2A> dla transakcji, proces zatwierdzania jest zablokowany w stanie, w którym dodatkowe pracy można wykonać na transakcji i można było utworzyć nowe rejestracji, aż wszystkie wywołania zależności <xref:System.Transactions.DependentTransaction.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="44f12-116">If the parent finishes its work earlier than the dependent transaction and calls <xref:System.Transactions.CommittableTransaction.Commit%2A> on the transaction, the commit process is blocked in a state where additional work can be done on the transaction and new enlistments can be created, until all of the dependents call <xref:System.Transactions.DependentTransaction.Complete%2A>.</span></span> <span data-ttu-id="44f12-117">Jako ukończony je wszystkie jego pracę, a następnie wywołać <xref:System.Transactions.DependentTransaction.Complete%2A>, rozpocznie się proces zatwierdzania dla transakcji.</span><span class="sxs-lookup"><span data-stu-id="44f12-117">As soon as all of them have finished their work and call <xref:System.Transactions.DependentTransaction.Complete%2A>, the commit process for the transaction begins.</span></span>  
  
- <span data-ttu-id="44f12-118"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, z drugiej strony, tworzy transakcję zależną, która automatycznie przerywa, jeśli <xref:System.Transactions.CommittableTransaction.Commit%2A> jest wywoływana w transakcji nadrzędnej przed wywołaniem <xref:System.Transactions.DependentTransaction.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="44f12-118"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, on the other hand, creates a dependent transaction that automatically aborts if <xref:System.Transactions.CommittableTransaction.Commit%2A> is called on the parent transaction before <xref:System.Transactions.DependentTransaction.Complete%2A> is called.</span></span> <span data-ttu-id="44f12-119">W takim przypadku wszystkie prace wykonane w transakcji zależne jest prawidłowa w ramach jednej transakcji okres istnienia i nie jest Państwo przekazać tylko jego części.</span><span class="sxs-lookup"><span data-stu-id="44f12-119">In this case, all the work done in the dependent transaction is intact within one transaction lifetime, and no one has a chance to commit just a portion of it.</span></span>  
  
 <span data-ttu-id="44f12-120">Metoda <xref:System.Transactions.DependentTransaction.Complete%2A> musi być wywoływana tylko raz, gdy aplikacja zakończy pracę w transakcji zależnej; w przeciwnym razie zostanie zgłoszony <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="44f12-120">The <xref:System.Transactions.DependentTransaction.Complete%2A> method must be called only once when your application finishes its work on the dependent transaction; otherwise, a <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="44f12-121">Po wywołaniu to wywołanie, nie należy spróbować żadnych dodatkowych działań w transakcji lub wyjątku.</span><span class="sxs-lookup"><span data-stu-id="44f12-121">After this call is invoked, you must not attempt any additional work on the transaction, or an exception is thrown.</span></span>  
  
 <span data-ttu-id="44f12-122">Poniższy przykład kodu pokazuje, jak utworzyć transakcję zależną, aby zarządzać dwoma współbieżnymi zadaniami przez klonowanie transakcji zależnej i przekazanie jej do wątku roboczego.</span><span class="sxs-lookup"><span data-stu-id="44f12-122">The following code example shows how to create a dependent transaction to manage two concurrent tasks by cloning a dependent transaction and passing it to a worker thread.</span></span>  
  
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
  
 <span data-ttu-id="44f12-123">Kod klienta tworzy zakres transakcji, który ustawia również otoczenia transakcji.</span><span class="sxs-lookup"><span data-stu-id="44f12-123">The client code creates a transactional scope that also sets the ambient transaction.</span></span> <span data-ttu-id="44f12-124">Transakcja otoczenia nie mają być przekazywane do wątku roboczego.</span><span class="sxs-lookup"><span data-stu-id="44f12-124">You should not pass the ambient transaction to the worker thread.</span></span> <span data-ttu-id="44f12-125">Zamiast tego należy sklonować bieżącej transakcji (otoczenia) przez wywołanie metody <xref:System.Transactions.Transaction.DependentClone%2A> metody w bieżącej transakcji i przekazać zależne od do wątku roboczego.</span><span class="sxs-lookup"><span data-stu-id="44f12-125">Instead, you should clone the current (ambient) transaction by calling the <xref:System.Transactions.Transaction.DependentClone%2A> method on the current transaction, and pass the dependent to the worker thread.</span></span>  
  
 <span data-ttu-id="44f12-126">`ThreadMethod` Metoda wykonuje na nowy wątek.</span><span class="sxs-lookup"><span data-stu-id="44f12-126">The `ThreadMethod` method executes on the new thread.</span></span> <span data-ttu-id="44f12-127">Klient uruchamia nowy wątek, przekazywania zależne transakcji jako `ThreadMethod` parametru.</span><span class="sxs-lookup"><span data-stu-id="44f12-127">The client starts a new thread, passing the dependent transaction as the `ThreadMethod` parameter.</span></span>  
  
 <span data-ttu-id="44f12-128">Ponieważ zależne transakcji jest tworzone z <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, ma gwarancji, że nie można zatwierdzić transakcji, aż wszystkie transakcyjnych zadań wykonywanych na sekundę wątek został zakończony i <xref:System.Transactions.DependentTransaction.Complete%2A> jest wywoływana w transakcji zależnych.</span><span class="sxs-lookup"><span data-stu-id="44f12-128">Because the dependent transaction is created with <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, you are guaranteed that the transaction cannot be committed until all of the transactional work done on the second thread is finished and <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent transaction.</span></span> <span data-ttu-id="44f12-129">Oznacza to, że jeśli kończy zakres klienta (podczas próby usunięcia obiektu transakcji na końcu `using` instrukcji) przed nowe wywołania wątku <xref:System.Transactions.DependentTransaction.Complete%2A> dla transakcji zależnych, kod klienta blokuje aż do <xref:System.Transactions.DependentTransaction.Complete%2A> jest wywoływana w elementach dependent.</span><span class="sxs-lookup"><span data-stu-id="44f12-129">This means that if the client's scope ends (when it tries to dispose of the transaction object at the end of the `using` statement) before the new thread calls <xref:System.Transactions.DependentTransaction.Complete%2A> on the dependent transaction, the client code blocks until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent.</span></span> <span data-ttu-id="44f12-130">Następnie transakcji może zakończyć przekazywanie lub przerywanie.</span><span class="sxs-lookup"><span data-stu-id="44f12-130">Then the transaction can finish committing or aborting.</span></span>  
  
## <a name="concurrency-issues"></a><span data-ttu-id="44f12-131">Problemy z współbieżności</span><span class="sxs-lookup"><span data-stu-id="44f12-131">Concurrency Issues</span></span>  
 <span data-ttu-id="44f12-132">Istnieje kilka problemów współbieżności dodatkowe, które należy zwrócić uwagę podczas korzystania z <xref:System.Transactions.DependentTransaction> klasy:</span><span class="sxs-lookup"><span data-stu-id="44f12-132">There are a few additional concurrency issues that you need to be aware of when using the <xref:System.Transactions.DependentTransaction> class:</span></span>  
  
- <span data-ttu-id="44f12-133">Jeśli wątku roboczego powoduje wycofanie transakcji, ale nadrzędnego próbuje zatwierdzić, <xref:System.Transactions.TransactionAbortedException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="44f12-133">If the worker thread rolls back the transaction but the parent tries to commit it, a <xref:System.Transactions.TransactionAbortedException> is thrown.</span></span>  
  
- <span data-ttu-id="44f12-134">Należy utworzyć nowy klon zależny dla każdego wątku roboczego w transakcji.</span><span class="sxs-lookup"><span data-stu-id="44f12-134">You should create a new dependent clone for each worker thread in the transaction.</span></span> <span data-ttu-id="44f12-135">Nie przekazuj tego samego klonu zależnego do wielu wątków, ponieważ tylko jeden z nich może wywoływać <xref:System.Transactions.DependentTransaction.Complete%2A> na nim.</span><span class="sxs-lookup"><span data-stu-id="44f12-135">Do not pass the same dependent clone to multiple threads, because only one of them can call <xref:System.Transactions.DependentTransaction.Complete%2A> on it.</span></span>  
  
- <span data-ttu-id="44f12-136">Jeśli wątku roboczego spawns nowego wątku roboczego, upewnij się, że tworzenie klon zależny od klon zależny i przekazywanie ich do nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="44f12-136">If the worker thread spawns a new worker thread, make sure to create a dependent clone from the dependent clone and pass it to the new thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f12-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44f12-137">See also</span></span>

- <xref:System.Transactions.DependentTransaction>
