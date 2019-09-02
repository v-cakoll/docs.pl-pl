---
title: Jednofazowe i wielofazowe zatwierdzanie transakcji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: 2abb9c13e9b0cb394546252e0e51e53c8ff9eefb
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205997"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a><span data-ttu-id="8ba51-102">Jednofazowe i wielofazowe zatwierdzanie transakcji</span><span class="sxs-lookup"><span data-stu-id="8ba51-102">Committing a Transaction in Single-Phase and Multi-Phase</span></span>
<span data-ttu-id="8ba51-103">Poszczególne zasoby używane w transakcji jest zarządzane przez Menedżera zasobów (MB), w których działania są koordynowany przez Menedżera transakcji (TM).</span><span class="sxs-lookup"><span data-stu-id="8ba51-103">Each resource used in a transaction is managed by a resource manager (RM), whose actions are coordinated by a transaction manager (TM).</span></span> <span data-ttu-id="8ba51-104">Zasoby związane z [rejestrowaniem w temacie transakcji](enlisting-resources-as-participants-in-a-transaction.md) omawiają sposób, w jaki zasób (lub wiele zasobów) może być zarejestrowany w transakcji.</span><span class="sxs-lookup"><span data-stu-id="8ba51-104">The [Enlisting Resources as Participants in a Transaction](enlisting-resources-as-participants-in-a-transaction.md) topic discusses how a resource (or multiple resources) can be enlisted in a transaction.</span></span> <span data-ttu-id="8ba51-105">W tym temacie opisano, jak można skoordynowanego między wyświetlone zasoby zobowiązaniom transakcji.</span><span class="sxs-lookup"><span data-stu-id="8ba51-105">This topic discusses how transaction commitment can be coordinated among enlisted resources.</span></span>  
  
 <span data-ttu-id="8ba51-106">Na końcu transakcji aplikacja żąda, aby transakcja została zatwierdzona lub wycofana.</span><span class="sxs-lookup"><span data-stu-id="8ba51-106">At the end of the transaction, the application requests the transaction to be either committed or rolled back.</span></span> <span data-ttu-id="8ba51-107">Menedżer transakcji musi wyeliminowania zagrożeń, takich jak niektórych menedżerów zasobów głosowanie zatwierdzić, podczas gdy inne głosowania można wycofać transakcji.</span><span class="sxs-lookup"><span data-stu-id="8ba51-107">The transaction manager must eliminate risks like some resource managers voting to commit while others voting to roll back the transaction.</span></span>  
  
 <span data-ttu-id="8ba51-108">Transakcja wiąże się z więcej niż jeden zasób, należy wykonać dwufazowego (2PC).</span><span class="sxs-lookup"><span data-stu-id="8ba51-108">If your transaction involves more than one resource, you must perform a two-phase commit (2PC).</span></span> <span data-ttu-id="8ba51-109">Protokół dwufazowego (fazy przygotowania i fazy rezerwacji) zapewnia, że po zakończeniu transakcji, wszystkie zmiany do wszystkich zasobów są całkowicie zadeklarowanej lub w pełni przywrócona.</span><span class="sxs-lookup"><span data-stu-id="8ba51-109">The two-phase commit protocol (the prepare phase and the commit phase) ensures that when the transaction ends, all changes to all resources are either totally committed or fully rolled back.</span></span> <span data-ttu-id="8ba51-110">Wszyscy uczestnicy są następnie poinformowany o wyniku końcowego.</span><span class="sxs-lookup"><span data-stu-id="8ba51-110">All the participants are then informed of the final result.</span></span> <span data-ttu-id="8ba51-111">Aby uzyskać szczegółową dyskusję na temat dwufazowego protokołu zatwierdzania, zapoznaj*się z książką "przetwarzanie transakcji: Koncepcje i techniki (seria Morgan Kaufmann w systemach zarządzanie danymi) ISBN:* 1558601902 "przez Jim szary.</span><span class="sxs-lookup"><span data-stu-id="8ba51-111">For a detailed discussion of the two-phase commit protocol, please consult the book "*Transaction Processing : Concepts and Techniques (Morgan Kaufmann Series in Data Management Systems) ISBN:1558601902*" by Jim Gray.</span></span>  
  
 <span data-ttu-id="8ba51-112">Można także zoptymalizować wydajność Twojej transakcji przez biorących udział w protokole zatwierdzania jednego etapu.</span><span class="sxs-lookup"><span data-stu-id="8ba51-112">You can also optimize your transaction's performance by taking part in the Single Phase Commit protocol.</span></span> <span data-ttu-id="8ba51-113">Aby uzyskać więcej informacji, zobacz [Optymalizacja przy użyciu jednej fazy zatwierdzania i powiadomienia o pojedynczej fazie](optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="8ba51-113">For more information, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](optimization-spc-and-promotable-spn.md).</span></span>  
  
 <span data-ttu-id="8ba51-114">Jeśli po prostu chcesz informujące o wyniku transakcji i zrezygnować z uczestnictwa w głosowaniu, należy zarejestrować dla <xref:System.Transactions.Transaction.TransactionCompleted> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8ba51-114">If you just want to be informed of a transaction's outcome, and do not want to participate in voting, you should register for the <xref:System.Transactions.Transaction.TransactionCompleted> event.</span></span>  
  
## <a name="two-phase-commit-2pc"></a><span data-ttu-id="8ba51-115">Dwufazowego (2PC)</span><span class="sxs-lookup"><span data-stu-id="8ba51-115">Two-phase Commit (2PC)</span></span>  
 <span data-ttu-id="8ba51-116">W pierwszej fazy transakcji Menedżer transakcji pyta każdy zasób, aby ustalić, czy zatwierdzeniu lub wycofać transakcji.</span><span class="sxs-lookup"><span data-stu-id="8ba51-116">In the first transaction phase, the transaction manager queries each resource to determine whether a transaction should be committed or rolled back.</span></span> <span data-ttu-id="8ba51-117">Drugi etap transakcji Menedżer transakcji powiadamia każdego zasobu wynik jego zapytań, dzięki któremu można wykonać wszelkie niezbędne czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="8ba51-117">In the second transaction phase, the transaction manager notifies each resource of the outcome of its queries, allowing it to perform any necessary cleanup.</span></span>  
  
 <span data-ttu-id="8ba51-118">Aby wziąć udział w tym rodzaju transakcji, Menedżer zasobów musi zaimplementować <xref:System.Transactions.IEnlistmentNotification> interfejs, który zapewnia metody wywoływane przez Menedżera TM jako powiadomienia podczas 2PC.</span><span class="sxs-lookup"><span data-stu-id="8ba51-118">To participate in this kind of transaction, a resource manager must implement the <xref:System.Transactions.IEnlistmentNotification> interface, which provides methods that are called by the TM as notifications during a 2PC.</span></span>  <span data-ttu-id="8ba51-119">W poniższym przykładzie przedstawiono przykład takiej implementacji.</span><span class="sxs-lookup"><span data-stu-id="8ba51-119">The following sample shows an example of such implementation.</span></span>  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a><span data-ttu-id="8ba51-120">Przygotuj faza (fazy 1)</span><span class="sxs-lookup"><span data-stu-id="8ba51-120">Prepare phase (Phase 1)</span></span>  
 <span data-ttu-id="8ba51-121">Po odebraniu <xref:System.Transactions.CommittableTransaction.Commit%2A> żądania od aplikacji Menedżer transakcji rozpoczyna przygotowywanie wszystkich uczestników uczestniczących przez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> wywołanie metody dla każdego zarejestrowanego zasobu w celu uzyskania głosu każdego zasobu na Transaction.</span><span class="sxs-lookup"><span data-stu-id="8ba51-121">Upon receiving a <xref:System.Transactions.CommittableTransaction.Commit%2A> request from the application, the transaction manager begins the Prepare phase of all the enlisted participants by calling the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method on each enlisted resource, in order to obtain each resource's vote on the transaction.</span></span>  
  
 <span data-ttu-id="8ba51-122">Menedżer zasobów implementujący <xref:System.Transactions.IEnlistmentNotification> interfejs powinien najpierw <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> zaimplementować metodę, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ba51-122">Your resource manager that implements the <xref:System.Transactions.IEnlistmentNotification> interface should first implement the <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> method as the following simple example shows.</span></span>  
  
```csharp
public void Prepare(PreparingEnlistment preparingEnlistment)  
{  
     Console.WriteLine("Prepare notification received");  
     //Perform work  
  
     Console.Write("reply with prepared? [Y|N] ");  
     c = Console.ReadKey();  
     Console.WriteLine();  
  
     //If work finished correctly, reply with prepared  
     if ((c.KeyChar == 'Y') || (c.KeyChar == 'y'))  
     {  
          preparingEnlistment.Prepared();  
          break;  
     }  
  
     // otherwise, do a ForceRollback  
     else if ((c.KeyChar == 'N') || (c.KeyChar == 'n'))  
     {  
          preparingEnlistment.ForceRollback();  
          break;  
     }  
}  
```  
  
 <span data-ttu-id="8ba51-123">Po odebraniu tego wywołania przez Menedżera zasobów trwałych powinien on rejestrować informacje o odzyskiwaniu transakcji (dostępne przez pobranie <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> właściwości) i informacje, które są niezbędne do ukończenia transakcji po zatwierdzeniu.</span><span class="sxs-lookup"><span data-stu-id="8ba51-123">When the durable resource manager receives this call, it should log the transaction's recovery information (available by retrieving the <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> property) and whatever information is necessary to complete the transaction on commit.</span></span> <span data-ttu-id="8ba51-124">To nie jest konieczne jest wykonywana w ramach <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metoda, ponieważ Menedżer zasobów można to zrobić w wątku roboczego.</span><span class="sxs-lookup"><span data-stu-id="8ba51-124">This does not need to be performed within the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method because the RM can do this on a worker thread.</span></span>  
  
 <span data-ttu-id="8ba51-125">Po zakończeniu Menedżera zasobów jego przygotowania pracy, należy głosowania przekazać ani wycofać przez wywołanie metody <xref:System.Transactions.PreparingEnlistment.Prepared%2A> lub <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8ba51-125">When the RM has finished its prepare work, it should vote to commit or roll back by calling the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> or <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> method.</span></span> <span data-ttu-id="8ba51-126">Należy zauważyć, że <xref:System.Transactions.PreparingEnlistment> klasa dziedziczy <xref:System.Transactions.Enlistment.Done%2A> metodę z <xref:System.Transactions.Enlistment> klasy.</span><span class="sxs-lookup"><span data-stu-id="8ba51-126">Notice that the <xref:System.Transactions.PreparingEnlistment> class inherits a <xref:System.Transactions.Enlistment.Done%2A> method from the <xref:System.Transactions.Enlistment> class.</span></span> <span data-ttu-id="8ba51-127">Wywołanie tej metody na <xref:System.Transactions.PreparingEnlistment> wywołania zwrotnego w fazie przygotowania, informuje Menedżer transakcji czy jest tylko do odczytu rejestracji (czyli menedżerów zasobów, które może być odczytany, ale nie można zaktualizować dane chronione przed transakcjami) i Menedżera zasobów odbiera żadne dalsze powiadomienia z menedżerem transakcji wyniku transakcji w fazie 2.</span><span class="sxs-lookup"><span data-stu-id="8ba51-127">If you call this method on the <xref:System.Transactions.PreparingEnlistment> callback during the Prepare phase, it informs the TM that it is a Read-Only enlistment (that is, resource managers that can read but cannot update transaction-protected data) and the RM receives no further notifications from the transaction manager as to the outcome of the transaction in phase 2.</span></span>  
  
 <span data-ttu-id="8ba51-128">Aplikacja jest powiadamiana o pomyślnym zobowiązaniu transakcji po zagłosowaniu <xref:System.Transactions.PreparingEnlistment.Prepared%2A>wszystkich menedżerów zasobów.</span><span class="sxs-lookup"><span data-stu-id="8ba51-128">The application is told of the successful commitment of the transaction after all the resource managers vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span></span>  
  
### <a name="commit-phase-phase-2"></a><span data-ttu-id="8ba51-129">Zatwierdź fazy (faza 2)</span><span class="sxs-lookup"><span data-stu-id="8ba51-129">Commit phase (Phase 2)</span></span>  
 <span data-ttu-id="8ba51-130">W drugiej fazy transakcji, gdy Menedżer transakcji odbiera pomyślne przygotowuje z wszystkich menedżerów zasobów (wywoływane ma wszystkich menedżerów zasobów <xref:System.Transactions.PreparingEnlistment.Prepared%2A> na końcu fazy 1), wywołuje ono <xref:System.Transactions.IEnlistmentNotification.Commit%2A> metody dla każdego Menedżera zasobów.</span><span class="sxs-lookup"><span data-stu-id="8ba51-130">In the second phase of the transaction, if the transaction manager receives successful prepares from all the resource managers (all the resource managers have invoked <xref:System.Transactions.PreparingEnlistment.Prepared%2A> at the end of phase 1), it invokes the <xref:System.Transactions.IEnlistmentNotification.Commit%2A> method for each resource manager.</span></span> <span data-ttu-id="8ba51-131">Menedżerowie zasobów mogą następnie wprowadzić trwałe zmiany i zakończyć zatwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="8ba51-131">The resource managers can then make the changes durable and complete the commit.</span></span>  
  
 <span data-ttu-id="8ba51-132">Jeśli którykolwiek z menedżerów zasobów zgłosił niepowodzenie przygotowania w fazie 1, Menedżer transakcji wywołuje <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> metodę dla każdego Menedżera zasobów i wskazuje niepowodzenie zatwierdzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ba51-132">If any resource manager reported a failure to prepare in phase 1, the transaction manager invokes the <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> method for each resource manager and indicates the failure of the commit to the application.</span></span>  
  
 <span data-ttu-id="8ba51-133">W tym celu Menedżer zasobów powinien zaimplementować następujące metody.</span><span class="sxs-lookup"><span data-stu-id="8ba51-133">Thus, your resource manager should implement the following methods.</span></span>  
  
```csharp
public void Commit (Enlistment enlistment)  
{  
     // Do any work necessary when commit notification is received  
  
     // Declare done on the enlistment  
     enlistment.Done();  
}  
  
public void Rollback (Enlistment enlistment)  
{  
     // Do any work necessary when rollback notification is received  
  
     // Declare done on the enlistment    
     enlistment.Done();    
}  
```  
  
 <span data-ttu-id="8ba51-134">Menedżer zasobów powinien wykonać wszelkie prace niezbędne do zakończenia transakcji na podstawie typu powiadomień i informuje Menedżer transakcji, który zakończył się przez wywołanie metody <xref:System.Transactions.Enlistment.Done%2A> metody w <xref:System.Transactions.Enlistment> parametru.</span><span class="sxs-lookup"><span data-stu-id="8ba51-134">The RM should perform any work necessary to finish the transaction based on the notification type, and inform the TM that it has finished by calling <xref:System.Transactions.Enlistment.Done%2A> method on the <xref:System.Transactions.Enlistment> parameter.</span></span> <span data-ttu-id="8ba51-135">Tej pracy można wykonać na wątku roboczego.</span><span class="sxs-lookup"><span data-stu-id="8ba51-135">This work can be done on a worker thread.</span></span> <span data-ttu-id="8ba51-136">Należy pamiętać, że powiadomieniami 2 może się tak zdarzyć tekście w tym samym wątku, który wywołał <xref:System.Transactions.PreparingEnlistment.Prepared%2A> metody w fazie 1.</span><span class="sxs-lookup"><span data-stu-id="8ba51-136">Note that the phase 2 notifications can happen inline on the same thread that called the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> method in phase 1.</span></span> <span data-ttu-id="8ba51-137">W związku z tym nie należy wykonywać żadnej pracy po <xref:System.Transactions.PreparingEnlistment.Prepared%2A> wywołaniu (na przykład zwalniać blokad), które należy wykonać przed odebraniem powiadomień fazy 2.</span><span class="sxs-lookup"><span data-stu-id="8ba51-137">As such, you should not do any work after the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> call (for example, releasing locks) that you would expect to have completed before receiving the phase 2 notifications.</span></span>  
  
### <a name="implementing-indoubt"></a><span data-ttu-id="8ba51-138">Zaimplementowanie wątpliwości</span><span class="sxs-lookup"><span data-stu-id="8ba51-138">Implementing InDoubt</span></span>  
 <span data-ttu-id="8ba51-139">Na koniec należy zaimplementować <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> metodę dla Menedżera zasobów lotnych.</span><span class="sxs-lookup"><span data-stu-id="8ba51-139">Finally, you should implement the <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> method for the volatile resource manager.</span></span> <span data-ttu-id="8ba51-140">Ta metoda jest wywoływana, gdy Menedżer transakcji traci kontaktu z jednego lub więcej uczestników, więc ich stan jest nieznany.</span><span class="sxs-lookup"><span data-stu-id="8ba51-140">This method is called if the transaction manager loses contact with one or more participants, so their status is unknown.</span></span> <span data-ttu-id="8ba51-141">W takim przypadku powinni wylogować się ten fakt tak, aby można było zbadać później czy wszystkich uczestników transakcji pozostały w niespójnym stanie.</span><span class="sxs-lookup"><span data-stu-id="8ba51-141">If this occurs, you should log this fact so that you can investigate later whether any of the transaction participants has been left in an inconsistent state.</span></span>  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a><span data-ttu-id="8ba51-142">Jedna faza zatwierdzania optymalizacji</span><span class="sxs-lookup"><span data-stu-id="8ba51-142">Single Phase Commit Optimization</span></span>  
 <span data-ttu-id="8ba51-143">Protokół zatwierdzania pojedynczej fazy jest bardziej wydajny w czasie wykonywania, ponieważ wszystkie aktualizacje są wykonywane bez jawnej koordynacji.</span><span class="sxs-lookup"><span data-stu-id="8ba51-143">The Single Phase Commit protocol is more efficient at run time because all updates are done without any explicit coordination.</span></span> <span data-ttu-id="8ba51-144">Aby uzyskać więcej informacji na temat tego protokołu, zobacz [Optymalizacja przy użyciu jednej fazy zatwierdzania i powiadomienia o pojedynczej fazie](optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="8ba51-144">For more information on this protocol, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](optimization-spc-and-promotable-spn.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba51-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ba51-145">See also</span></span>

- [<span data-ttu-id="8ba51-146">Optymalizacja za pomocą zatwierdzania jednofazowego i umożliwiającego awansowanie powiadomienia jednofazowego</span><span class="sxs-lookup"><span data-stu-id="8ba51-146">Optimization using Single Phase Commit and Promotable Single Phase Notification</span></span>](optimization-spc-and-promotable-spn.md)
- [<span data-ttu-id="8ba51-147">Rejestrowanie zasobów jako uczestników transakcji</span><span class="sxs-lookup"><span data-stu-id="8ba51-147">Enlisting Resources as Participants in a Transaction</span></span>](enlisting-resources-as-participants-in-a-transaction.md)
