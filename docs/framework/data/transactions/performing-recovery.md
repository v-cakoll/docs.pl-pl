---
title: Odzyskiwanie systemu
ms.date: 03/30/2017
ms.assetid: 6dd17bf6-ba42-460a-a44b-8046f52b10d0
ms.openlocfilehash: 149ac6b6162893de830f59b3d18008d8298eab56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793617"
---
# <a name="performing-recovery"></a>Odzyskiwanie systemu
Menedżer zasobów ułatwia rozwiązanie trwałych rejestracji w transakcji przez reenlisting uczestnika transakcji po awarii zasobu.  
  
## <a name="the-recovery-process"></a>Proces odzyskiwania  
 Aby zarejestrować trwale zasób (opisanego przez implementację <xref:System.Transactions.IEnlistmentNotification> interfejsu) który może być później mogą korzystać odzyskiwania, należy wywołać <xref:System.Transactions.Transaction.EnlistDurable%2A> metody. Ponadto należy podać <xref:System.Transactions.Transaction.EnlistDurable%2A> metody z identyfikatorem Menedżera zasobów ( <xref:System.Guid>) używany do stale etykiety uczestnika transakcji w przypadku awarii zasobu. Z tego powodu <xref:System.Guid> to pod warunkiem do początkowego Enlist wywołanie powinno być taka sama jak *resourceManagerIdentifier* parametru w <xref:System.Transactions.TransactionManager.Reenlist%2A> podczas odzyskiwania. W przeciwnym razie <xref:System.Transactions.TransactionException> zgłaszany. Aby uzyskać więcej informacji na trwałych rejestracji, zobacz [rejestrowanie zasobów jako uczestników transakcji](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) .  
  
 W fazie przygotowania (faza 1) protokołu 2PC, po odebraniu implementacja Menedżera zasobów trwałe <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> powiadomienia, jego powinni wylogować swój rekord prepare podczas tej fazy. Rekord powinien zawierać wszystkie informacje, które są niezbędne do zrealizowania transakcji na zatwierdzania. Rekord prepare później może uzyskać dostęp podczas odzyskiwania pobierając <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> właściwość *preparingEnlistment* wywołania zwrotnego. Rejestrowanie rekordu nie jest konieczne jest wykonywana w ramach <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metody jako Menedżera zasobów można to zrobić w wątku roboczego.  
  
 Proces odzyskiwania składa się z następujących dwóch kroków:  
  
### <a name="step-1---reenlist"></a>Krok 1 - ReEnlist  
 Menedżer zasobów sprawdza, czy prepare rekordu informacji dla każdej rejestracji, który jest w stanie wątPLiwości. Jest to wykonywane przez sprawdzenie <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> właściwości <xref:System.Transactions.PreparingEnlistment> wywołanie zwrotne, które są przekazywane do Menedżera zasobów w <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> powiadomień w fazie 1.  
  
 Dla każdego takiego rejestracji sprawdza, czy, wywołuje <xref:System.Transactions.TransactionManager.Reenlist%2A> na Menedżera transakcji. Ta metoda przekazuje unikatowego <xref:System.Guid> określający Menedżera zasobów, a także informacje o rejestracji w tablicy bajtów. Nowy <xref:System.Transactions.Enlistment> obiekt jest zwracany. Jeśli ponownej rejestracji nie powiedzie się z powodu wyjątku ponowić próbę później, konieczne będzie Menedżera zasobów.  
  
 Należy wywołać tylko <xref:System.Transactions.TransactionManager.Reenlist%2A> metody po uruchomieniu Menedżera zasobów po awarii. Ponadto należy tylko reenlist rozwiązane transakcje zarejestrowane przez Menedżera zasobów w fazie przygotowania początkowego dwufazowego zatwierdzania. Każda próba wywołania tej metody w czasie nieprawidłowy może utworzyć błędnych wyników.  
  
 Gdy uczestnika, który jest reenlisted za pomocą tej metody, metody Faza 2 <xref:System.Transactions.IEnlistmentNotification> odpowiada wyniku transakcji (oznacza to, że <xref:System.Transactions.IEnlistmentNotification.Commit%2A> , <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> lub <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> ) są nazywane odpowiednio.  
  
### <a name="step-2---completing-the-recovery"></a>Krok 2 - ukończenie odzyskiwania  
 Po zakończeniu wszystkich reenlistments, Menedżer zasobów wywołuje <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> metody. Ta metoda kończy odzyskiwania i informuje menedżera transakcji, Menedżer zasobów jest już w stanie wątpliwości transakcji. W ten sposób Menedżera zasobów gwarantuje, że nie będzie wywołania <xref:System.Transactions.TransactionManager.Reenlist%2A> ponownie metodą.  
  
 Menedżer zasobów nie jest wymagana, aby usunąć wszystkie transakcje w stanie wątPLiwości przed rejestrowanie w nowych transakcji. Pierwszym krokiem można wykonać w dowolnej chwili po Menedżera zasobów ustanawia relacje z menedżerem transakcji, ale po <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> został wywołany (krok 2); krok 1 nie można wykonać ponownie. Krok 2 można powtarzać wielokrotnie bez wywierania wpływu na wyniki transakcji.
