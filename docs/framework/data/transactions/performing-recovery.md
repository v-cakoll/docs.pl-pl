---
title: Odzyskiwanie systemu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dd17bf6-ba42-460a-a44b-8046f52b10d0
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a73e1b5c6cbb18e89b30550f02c0678e76d12ab4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="performing-recovery"></a>Odzyskiwanie systemu
Menedżer zasobów ułatwia rozwiązanie trwałych rejestracji w transakcji przez reenlisting uczestnika transakcji po awarii zasobu.  
  
## <a name="the-recovery-process"></a>Proces odzyskiwania  
 Można zarejestrować trwale zasobu (opisanego przez implementację <xref:System.Transactions.IEnlistmentNotification> interfejsu) który można później kwalifikować się do odzyskiwania, należy wywołać <xref:System.Transactions.Transaction.EnlistDurable%2A> metody. Ponadto należy podać <xref:System.Transactions.Transaction.EnlistDurable%2A> metody z identyfikatorem Menedżera zasobów ( <xref:System.Guid>) używany do stale etykiety uczestnika transakcji w przypadku awarii zasobu. Z tego powodu <xref:System.Guid> jest dostarczane do początkowej Enlist wywołania powinny być identyczne z *resourceManagerIdentifier* parametru w <xref:System.Transactions.TransactionManager.Reenlist%2A> wywołań podczas odzyskiwania. W przeciwnym razie <xref:System.Transactions.TransactionException> zgłaszany. Aby uzyskać więcej informacji o trwałych rejestracji, zobacz [rejestrowanie zasobów jako uczestnicy transakcji](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) .  
  
 W fazie przygotowywania (faza 1) protokołu 2PC, gdy otrzyma implementacji Menedżera zasobów trwałe <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> powiadomień, jego rekordu przygotowanie go powinien logować się w tej fazie. Rekord powinien zawierać wszystkie informacje, które są niezbędne do ukończenia transakcji w zatwierdzeniu. Rekord prepare później może uzyskać dostęp podczas odzyskiwania, pobierając <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> właściwość *preparingEnlistment* wywołania zwrotnego. Rejestrowanie rekordu nie jest konieczne jest wykonywana w ramach <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metody jako Menedżera zasobów można to zrobić w wątku roboczego.  
  
 Proces odzyskiwania składa się z następujących dwóch kroków:  
  
### <a name="step-1---reenlist"></a>Krok 1 - ReEnlist  
 Menedżer zasobów sprawdza, czy prepare rekordu informacji dla każdej rejestracji, który jest w stanie wątPLiwości. Jest to wykonywane przez sprawdzenie <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> właściwości <xref:System.Transactions.PreparingEnlistment> wywołanie zwrotne, które są przekazywane do Menedżera zasobów w <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> powiadomień w fazie 1.  
  
 Dla każdego takiego rejestracji sprawdza, czy, wywołuje <xref:System.Transactions.TransactionManager.Reenlist%2A> na Menedżera transakcji. Ta metoda przekazuje unikatowego <xref:System.Guid> określający Menedżera zasobów, a także informacje o rejestracji w tablicy bajtów. Nowy <xref:System.Transactions.Enlistment> obiekt jest zwracany. Jeśli ponownej rejestracji nie powiedzie się z powodu wyjątku ponowić próbę później, konieczne będzie Menedżera zasobów.  
  
 Należy wywołać tylko <xref:System.Transactions.TransactionManager.Reenlist%2A> metody po uruchomieniu Menedżera zasobów po awarii. Ponadto należy tylko reenlist rozwiązane transakcje zarejestrowane przez Menedżera zasobów w fazie przygotowania początkowego dwufazowego zatwierdzania. Każda próba wywołania tej metody w czasie nieprawidłowy może utworzyć błędnych wyników.  
  
 Gdy uczestnika, który jest reenlisted za pomocą tej metody, metody Faza 2 <xref:System.Transactions.IEnlistmentNotification> odpowiada wyniku transakcji (oznacza to, że <xref:System.Transactions.IEnlistmentNotification.Commit%2A> , <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> lub <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> ) są nazywane odpowiednio.  
  
### <a name="step-2---completing-the-recovery"></a>Krok 2 — wykonanie odzyskiwania  
 Po zakończeniu wszystkich reenlistments, Menedżer zasobów wywołuje <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> metody. Ta metoda kończy odzyskiwania i Menedżera transakcji informuje, że Menedżer zasobów ma już wątpliwych transakcji. W ten sposób Menedżera zasobów gwarantuje, że nie będzie wywołania <xref:System.Transactions.TransactionManager.Reenlist%2A> ponownie metodą.  
  
 Menedżer zasobów nie jest wymagana, aby usunąć wszystkie transakcje w stanie wątPLiwości przed rejestrowanie w nowych transakcji. Pierwszy krok można wykonać w dowolnym momencie po Menedżera zasobów ustanawia relację z menedżerem transakcji, natomiast po <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> została wywołana (krok 2); nie można ponownie wykonać krok 1. Krok 2 może być powtarza się wielokrotnie bez wpływu na wynik transakcji.
