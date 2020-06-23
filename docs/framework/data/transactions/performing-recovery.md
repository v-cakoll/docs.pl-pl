---
title: Odzyskiwanie systemu
description: Wykonaj odzyskiwanie na platformie .NET. Menedżer zasobów pomaga w rozwiązywaniu trwałych rejestracji transakcji przez ponowne zarejestrowanie uczestnika transakcji po awarii zasobu.
ms.date: 03/30/2017
ms.assetid: 6dd17bf6-ba42-460a-a44b-8046f52b10d0
ms.openlocfilehash: bb00d2f574cc2651b733f3308cf2ffc6b430cc31
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141968"
---
# <a name="performing-recovery"></a>Odzyskiwanie systemu
Menedżer zasobów ułatwia rozwiązanie trwałych rejestracji w transakcji przez reenlisting uczestnika transakcji po awarii zasobu.  
  
## <a name="the-recovery-process"></a>Proces odzyskiwania  
 Aby trwale zarejestrować zasób (opisany przez implementację <xref:System.Transactions.IEnlistmentNotification> interfejsu), który może być później możliwy do odzyskania, należy wywołać <xref:System.Transactions.Transaction.EnlistDurable%2A> metodę. Ponadto należy podać <xref:System.Transactions.Transaction.EnlistDurable%2A> metody z identyfikatorem Menedżera zasobów ( <xref:System.Guid>) używany do stale etykiety uczestnika transakcji w przypadku awarii zasobu. Z tego powodu, <xref:System.Guid> który jest dostarczany do początkowego wywołania rejestracji powinien być taki sam jak parametr *resourceManagerIdentifier* w <xref:System.Transactions.TransactionManager.Reenlist%2A> wywołaniu podczas odzyskiwania. W przeciwnym razie <xref:System.Transactions.TransactionException> zgłaszany. Aby uzyskać więcej informacji na temat trwałych rejestracji, zobacz temat [Rejestrowanie zasobów jako uczestników transakcji](enlisting-resources-as-participants-in-a-transaction.md) .  
  
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
