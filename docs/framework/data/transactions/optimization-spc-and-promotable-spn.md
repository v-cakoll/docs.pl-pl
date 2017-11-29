---
title: "Optymalizacja za pomocą pojedynczego zatwierdzić fazy i awansowanie pojedyncze powiadomienia fazy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57beaf1a-fb4d-441a-ab1d-bc0c14ce7899
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 66f60ba31983a6cfbfda0238d80a6e8ad81d30ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="optimization-using-single-phase-commit-and-promotable-single-phase-notification"></a>Optymalizacja za pomocą pojedynczego zatwierdzić fazy i awansowanie pojedyncze powiadomienia fazy
W tym temacie opisano mechanizmy udostępnione przez <xref:System.Transactions> infrastruktury w celu optymalizacji wydajności.  
  
## <a name="promotable-single-phase-enlistment"></a>Rejestracja awansowanie jedna faza  
 <xref:System.Transactions> Transakcji wewnątrz domeny pojedynczej aplikacji, która obejmuje co najwyżej jednego zasobu trwałe lub wiele zasobów volatile przez infrastrukturę. Ponieważ <xref:System.Transactions> infrastruktura używa wywołania tylko wewnątrz aplikacji domeny, go zapewni najlepszą przepływności i wydajności.  
  
 Jednakże, jeśli transakcja jest dostarczany do innego obiektu w innej domenie aplikacji (w tym w granicach procesu i komputera) na tym samym komputerze lub jeśli były można zarejestrować innego menedżera zasobów trwałe, <xref:System.Transactions> infrastruktury automatycznie Eskalowanie transakcji, które mają być zarządzane przez usługi MSDTC. Zarządzane przez MSDTC transakcji nie jest performance-wise jako jeden zarządzane przez <xref:System.Transactions> infrastruktury.  
  
 Aby zoptymalizować wydajność, <xref:System.Transactions> infrastruktura zapewnia awansowanie jednej fazie rejestracji (PSPE) umożliwiający jednego zdalnego zasobu trwałe, znajduje się w domenie innej aplikacji, proces lub komputera, aby uczestniczyć w <xref:System.Transactions> transakcja bez powodowania zostać przekazany do transakcji usługi MSDTC.  Ten Menedżer zasobu (MB) umożliwia przechowywanie i "własnością" transakcji, która później można przekazany do transakcji rozproszonych (lub transakcji MSDTC), jeśli to konieczne. Zmniejsza to prawdopodobieństwo za pomocą MSDTC.  
  
 Ten Menedżer określonego zasobu, zwykle ma własne wewnętrzne transakcje rozproszone bez i należy go obsługuje konwertowania tych transakcji na transakcje rozproszone w czasie wykonywania. Na przykład SQL Server 2005 jest Menedżera zasobów. W takim przypadku <xref:System.Transactions> infrastruktury przyjmuje rolę Zarządzanie bierne po prostu Monitoruj transakcji na potrzeby eskalacji. Do obsługi interakcji między <xref:System.Transactions> Menedżera infrastruktury i zasobów, ostatnie musi implementować interfejs <xref:System.Transactions.IPromotableSinglePhaseNotification>.  
  
 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> Metoda służy do zarejestrować pojedynczy trwałe zasób, który może zostać przekazany później. Ta metoda zapewnia, że rejestracja może być przekazany zgodnie z potrzebami. Jeśli rejestracja zakończy się powodzeniem, Menedżer zasobów tworzy jego wewnętrznego transakcji i kojarzy ją z <xref:System.Transactions> transakcji. W przypadku niepowodzenia rejestracji PSPE Menedżera zasobów zamiast tego należy zarejestrować przy użyciu <xref:System.Transactions.Transaction.EnlistDurable%2A> metody. Błędów, aby zarejestrować PSPE może się zdarzyć, gdy transakcja została już transakcja rozproszona lub innego menedżera zasobów przeprowadził już rejestracji PSPE  
  
 Gdy zarejestrowana, wywołuje przez klientów, aby zatwierdzić lub przerwać <xref:System.Transactions> transakcji są konwertowane na wywołania na Menedżera zasobów, wywołując <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> metody lub <xref:System.Transactions.IPromotableSinglePhaseNotification.Rollback%2A> odpowiednio.  
  
 Jeśli <xref:System.Transactions> transakcji nigdy nie wymaga eskalacji, gdy transakcja zostanie zatwierdzone, Menedżer zasobów odbiera <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> powiadomienia. Można ją następnie Zatwierdź wewnętrzny transakcji, która została początkowo utworzona.  
  
 Jeśli <xref:System.Transactions> transakcji musi być przekazany (np. do obsługi wielu RMs), <xref:System.Transactions> informuje Menedżera zasobów przez wywołanie metody <xref:System.Transactions.ITransactionPromoter.Promote%2A> metoda <xref:System.Transactions.ITransactionPromoter> interfejsu, z którego <xref:System.Transactions.IPromotableSinglePhaseNotification> pochodzi interfejsu. Menedżer zasobów następnie konwertuje transakcji wewnętrznie z lokalnym transakcji (które nie wymagają rejestrowania) obiekt transakcji, który jest w stanie udział w transakcji usługi i kojarzy ją z już pracy. Gdy transakcja jest proszony o zatwierdzania, Menedżer transakcji nadal wysyła <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> powiadomienia do Menedżera zasobów, które zatwierdzeń transakcji rozproszonych, utworzony podczas eskalacji.  
  
> [!NOTE]
>  **TransactionCommitted** śladów (które są generowane po wywołaniu zatwierdzenie transakcji eskalowane) zawierać identyfikator działania transakcji usługi DTC.  
  
 Aby uzyskać więcej informacji, zarządzanie eskalacją, zobacz [eskalacji zarządzania transakcji](../../../../docs/framework/data/transactions/transaction-management-escalation.md).  
  
## <a name="transaction-management-escalation-scenario"></a>W tym scenariuszu eskalacji zarządzania transakcji  
 Następujący scenariusz pokazuje kontaktu z transakcji rozproszonych za pomocą <xref:System.Data> nazw jako "proxy" Menedżera zasobów. W tym scenariuszu przyjęto założenie, że istnieje już <xref:System.Data> połączenia z bazą danych, CN1, biorących udział w transakcji, a aplikacja będzie obejmować innego <xref:System.Data> połączenia, CN2. Transakcji musi zostać przekazany do usługi, jako transakcja pełną rozproszonej dwufazowe.  
  
 W tym scenariuszu  
  
1.  Wywołania CN1 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodę, aby zarejestrować transakcji. Następnie transakcja jest nadal lokalnego i nie ma żadnych awansowanie rejestracji w transakcji, więc <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> połączenie zakończy się powodzeniem.  
  
2.  Po drugie połączenie, CN2 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>, połączenie nie powiedzie się, ponieważ jest zaangażowane innego awansowanie rejestracji. W związku z tym CN2 musi uzyskać transakcję usługi, aby można było przekazać je do programu SQL. W tym celu używa jednej z metod dostarczonych przez <xref:System.Transactions.TransactionInterop> klasy w celu uzyskania formatu transakcji, która może być SQL.  
  
3.  <xref:System.Transactions>wywołania <xref:System.Transactions.ITransactionPromoter.Promote%2A> metoda <xref:System.Transactions.ITransactionPromoter> interfejsu implementowanego przez CN1.  
  
4.  W tym momencie CN1 Eskalowanie transakcji, niektóre mechanizm specyficzne dla SQL 2005 i <xref:System.Data>.  
  
5.  Wartość zwrócona przez <xref:System.Transactions.ITransactionPromoter.Promote%2A> metoda jest zawierający tokenu propagacji transakcji tablicy bajtów. <xref:System.Transactions>używa tego tokenu propagaition do utworzenia transakcji usługi, które można uwzględnić w lokalnym transakcję.  
  
6.  W tym momencie CN2 można użyć dane otrzymane z jednej z metod przez wywołanie <xref:System.Transactions.TransactionInterop> do przekazania transakcji SQL.  
  
7.  Teraz zarówno biorących udział w transakcji rozproszonych usługi.  
  
## <a name="single-phase-commit-optimization"></a>Jedna faza zatwierdzania optymalizacji  
 Protokół zatwierdzić jednej fazie jest bardziej wydajne w czasie wykonywania, ponieważ wszystkie aktualizacje są przeprowadzane bez jawnego koordynacji. Aby móc korzystać z tego rodzaju optymalizacji, należy zaimplementować za pomocą Menedżera zasobów <xref:System.Transactions.ISinglePhaseNotification> interfejsu dla zasobu i zarejestrować się w transakcji za pomocą <xref:System.Transactions.Transaction.EnlistDurable%2A> lub <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody. W szczególności *EnlistmentOptions* powinna być równa parametru <xref:System.Transactions.EnlistmentOptions.None> aby upewnić się na zatwierdzenie jednej fazie zostałoby przeprowadzone.  
  
 Ponieważ <xref:System.Transactions.ISinglePhaseNotification> pochodzi od klasy interfejs <xref:System.Transactions.IEnlistmentNotification> interfejsu, jeśli Twój Menedżera zasobów jest nieodpowiedni dla jednego etapu zatwierdzania, może nadal odbierać fazy dwa powiadomienia zatwierdzania.  W przypadku otrzymania swojego menedżera zasobów <xref:System.Transactions.ISinglePhaseNotification.SinglePhaseCommit%2A> powiadomienie z Menedżer transakcji, jego starać się wykonują pracę niezbędne do zatwierdzania i odpowiednio informują menedżera transakcji, jeśli transakcja ma zostać przekazana lub wycofana przez wywołanie metody <xref:System.Transactions.SinglePhaseEnlistment.Committed%2A>, <xref:System.Transactions.SinglePhaseEnlistment.Aborted%2A>, lub <xref:System.Transactions.SinglePhaseEnlistment.InDoubt%2A> metody w <xref:System.Transactions.SinglePhaseEnlistment> parametru. Odpowiedź <xref:System.Transactions.Enlistment.Done%2A> na tym etapie rejestracji oznacza semantyki tylko do odczytu. W związku z tym nie należy odpowiedzi <xref:System.Transactions.Enlistment.Done%2A> oprócz innych metod.  
  
 Jeśli istnieje tylko jeden volatile rejestracji i nie trwałych rejestracji, volatile rejestracji otrzymuje powiadomienia SPC.  Jeśli istnieją wszystkie rejestracje nietrwałe i tylko jeden trwałych rejestracji, Rejestracje nietrwałe odbierać 2PC. Po jego ukończeniu rejestracji trwałe odbiera SPC.  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestrowanie zasobów jako uczestnicy transakcji](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)  
 [Zatwierdzanie transakcji w jednofazowy i wielu fazy](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)
