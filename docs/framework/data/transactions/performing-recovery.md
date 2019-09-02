---
title: Odzyskiwanie systemu
ms.date: 03/30/2017
ms.assetid: 6dd17bf6-ba42-460a-a44b-8046f52b10d0
ms.openlocfilehash: fe0e096c31b2ef62a1bc50d40c87f2e12c87343f
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205887"
---
# <a name="performing-recovery"></a>Odzyskiwanie systemu
Menedżer zasobów ułatwia rozwiązanie trwałych rejestracji w transakcji przez reenlisting uczestnika transakcji po awarii zasobu.  
  
## <a name="the-recovery-process"></a>Proces odzyskiwania  
 Aby trwale zarejestrować zasób (opisany przez implementację <xref:System.Transactions.IEnlistmentNotification> interfejsu), który może być później możliwy do odzyskania, należy <xref:System.Transactions.Transaction.EnlistDurable%2A> wywołać metodę. Ponadto należy podać <xref:System.Transactions.Transaction.EnlistDurable%2A> metody z identyfikatorem Menedżera zasobów ( <xref:System.Guid>) używany do stale etykiety uczestnika transakcji w przypadku awarii zasobu. Z <xref:System.Guid> tego powodu, który jest dostarczany do początkowego wywołania rejestracji powinien być taki sam jak parametr *resourceManagerIdentifier* w <xref:System.Transactions.TransactionManager.Reenlist%2A> wywołaniu podczas odzyskiwania. W przeciwnym razie <xref:System.Transactions.TransactionException> zgłaszany. Aby uzyskać więcej informacji na temat trwałych rejestracji, zobacz temat [Rejestrowanie zasobów jako uczestników transakcji](enlisting-resources-as-participants-in-a-transaction.md) .  
  
 W fazie Prepare (faza 1) protokołu 2PC, gdy implementacja trwałego Menedżera zasobów odbierze <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> powiadomienie, powinien rejestrować swój rekord Prepare w tej fazie. Rekord powinien zawierać wszystkie informacje niezbędne do ukończenia transakcji po zatwierdzeniu. Można później uzyskać dostęp do rekordu przygotowania podczas odzyskiwania, pobierając <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> Właściwość wywołania zwrotnego *preparingEnlistment* . Rejestrowanie rekordu nie jest konieczne jest wykonywana w ramach <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metody jako Menedżera zasobów można to zrobić w wątku roboczego.  
  
 Proces odzyskiwania składa się z następujących dwóch kroków:  
  
### <a name="step-1---reenlist"></a>Krok 1 - ReEnlist  
 Menedżer zasobów sprawdza, czy prepare rekordu informacji dla każdej rejestracji, który jest w stanie wątPLiwości. Jest to wykonywane przez sprawdzenie <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> właściwości <xref:System.Transactions.PreparingEnlistment> wywołanie zwrotne, które są przekazywane do Menedżera zasobów w <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> powiadomień w fazie 1.  
  
 Dla każdego takiego rejestracji sprawdza, czy, wywołuje <xref:System.Transactions.TransactionManager.Reenlist%2A> na Menedżera transakcji. Ta metoda przekazuje unikatowego <xref:System.Guid> określający Menedżera zasobów, a także informacje o rejestracji w tablicy bajtów. Nowy <xref:System.Transactions.Enlistment> obiekt jest zwracany. Jeśli ponownej rejestracji nie powiedzie się z powodu wyjątku ponowić próbę później, konieczne będzie Menedżera zasobów.  
  
 Należy wywołać tylko <xref:System.Transactions.TransactionManager.Reenlist%2A> metody po uruchomieniu Menedżera zasobów po awarii. Ponadto należy tylko reenlist rozwiązane transakcje zarejestrowane przez Menedżera zasobów w fazie przygotowania początkowego dwufazowego zatwierdzania. Każda próba wywołania tej metody w czasie nieprawidłowy może utworzyć błędnych wyników.  
  
 Gdy uczestnika, który jest reenlisted za pomocą tej metody, metody Faza 2 <xref:System.Transactions.IEnlistmentNotification> odpowiada wyniku transakcji (oznacza to, że <xref:System.Transactions.IEnlistmentNotification.Commit%2A> , <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> lub <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> ) są nazywane odpowiednio.  
  
### <a name="step-2---completing-the-recovery"></a>Krok 2 — zakończenie odzyskiwania  
 Po zakończeniu wszystkich reenlistments, Menedżer zasobów wywołuje <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> metody. Ta metoda uzupełnia odzyskiwanie i informuje Menedżera transakcji, że Menedżer zasobów nie ma więcej wątpliwych transakcji. W ten sposób Menedżera zasobów gwarantuje, że nie będzie wywołania <xref:System.Transactions.TransactionManager.Reenlist%2A> ponownie metodą.  
  
 Menedżer zasobów nie jest wymagana, aby usunąć wszystkie transakcje w stanie wątPLiwości przed rejestrowanie w nowych transakcji. Pierwszy krok można wykonać w dowolnym momencie po ustanowieniu przez Menedżera zasobów relacji z menedżerem transakcji, ale po <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> wywołaniu (krok 2); Krok 1 nie można wykonać ponownie. Krok 2 można powtórzyć wiele razy bez wpływu na wynik transakcji.
