---
title: Optymalizacja za pomocą zatwierdzania jednofazowego i awansowanie powiadomienia jednofazowego
ms.date: 03/30/2017
ms.assetid: 57beaf1a-fb4d-441a-ab1d-bc0c14ce7899
ms.openlocfilehash: 73340f5f65de1d743e046cf669258ab5f6c66298
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371206"
---
# <a name="optimization-using-single-phase-commit-and-promotable-single-phase-notification"></a>Optymalizacja za pomocą zatwierdzania jednofazowego i awansowanie powiadomienia jednofazowego

W tym temacie opisano mechanizmy udostępnione przez <xref:System.Transactions> infrastruktury w celu optymalizacji wydajności.

## <a name="promotable-single-phase-enlistment"></a>Rejestracja awansowanie jedna faza

<xref:System.Transactions> Transakcji wewnątrz domeny pojedynczej aplikacji, która wymaga co najwyżej pojedynczy zasób trwałego lub wiele zasobów lotnych administrates infrastruktury. Ponieważ <xref:System.Transactions> infrastruktury używa wywołań domeny tylko w obrębie aplikacji, jego daje najlepsze przepływności i wydajności.

Jednakże, jeśli transakcja jest przekazywany do innego obiektu w innej domenie aplikacji (w tym granic procesu i maszynowo) na tym samym komputerze lub gdyby zarejestrować innego menedżera zasobów trwałe <xref:System.Transactions> infrastruktury automatycznie Eskalowanie transakcji, które mają być zarządzane przez MSDTC. Zarządzane przez MSDTC transakcji nie jest performance-wise jako jeden zarządzane przez <xref:System.Transactions> infrastruktury.

Aby zoptymalizować wydajność, <xref:System.Transactions> infrastruktury udostępnia awansowanie jednego etapu rejestracji (PSPE) umożliwiający pojedynczy trwałe zasób zdalny, znajduje się w domenie innej aplikacji, proces lub komputera, aby uczestniczyć w <xref:System.Transactions> transakcji bez powodowania zostać przekazany do transakcji MSDTC. Ten Menedżer zasobu (MB) umożliwia przechowywanie i "własnością" transakcji, która później można przekazany do transakcji rozproszonych (lub transakcji MSDTC), jeśli to konieczne. Zmniejsza to prawdopodobieństwo za pomocą MSDTC.

Ten Menedżer określonego zasobu, zwykle ma własne wewnętrzne transakcje rozproszone bez i należy go obsługuje konwertowania tych transakcji na transakcje rozproszone w czasie wykonywania. Na przykład SQL Server 2005 jest Menedżera zasobów. W takim przypadku <xref:System.Transactions> infrastruktury przyjmuje rolę Zarządzanie bierne po prostu Monitoruj transakcji na potrzeby eskalacji. Do obsługi interakcji między <xref:System.Transactions> manager infrastruktury i zasobów, ostatnie musi implementować interfejs <xref:System.Transactions.IPromotableSinglePhaseNotification>.

<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> Metoda służy do zarejestrować pojedynczy trwałe zasób, który może zostać przekazany później. Ta metoda zapewnia, że rejestracja może być przekazany zgodnie z potrzebami. Jeśli rejestracja zakończy się powodzeniem, Menedżer zasobów tworzy jego wewnętrznego transakcji i kojarzy ją z <xref:System.Transactions> transakcji. W przypadku niepowodzenia rejestracji PSPE Menedżera zasobów zamiast tego należy zarejestrować przy użyciu <xref:System.Transactions.Transaction.EnlistDurable%2A> metody. Błędów, aby zarejestrować PSPE może się zdarzyć, gdy transakcja została już transakcja rozproszona lub innego menedżera zasobów przeprowadził już rejestracji PSPE

Gdy zarejestrowana, wywołuje przez klientów, aby zatwierdzić lub przerwać <xref:System.Transactions> transakcji są konwertowane na wywołania na Menedżera zasobów, wywołując <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> metody lub <xref:System.Transactions.IPromotableSinglePhaseNotification.Rollback%2A> odpowiednio.

Jeśli <xref:System.Transactions> transakcji nigdy nie wymaga eskalacji, gdy transakcja zostanie zatwierdzone, Menedżer zasobów odbiera <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> powiadomienia. Można ją następnie Zatwierdź wewnętrzny transakcji, która została początkowo utworzona.

Jeśli <xref:System.Transactions> transakcji musi zostać przekazany (np. do obsługi wielu usług RMs), <xref:System.Transactions> informuje Menedżera zasobów przez wywołanie metody <xref:System.Transactions.ITransactionPromoter.Promote%2A> metody <xref:System.Transactions.ITransactionPromoter> interfejsu, z którego <xref:System.Transactions.IPromotableSinglePhaseNotification> efektów interfejsu. Menedżer zasobów następnie konwertuje transakcji wewnętrznie z lokalnym transakcji (które nie wymagają rejestrowania) obiekt transakcji, który jest w stanie udział w transakcji usługi i kojarzy ją z już pracy. Gdy transakcja jest proszony o zatwierdzania, Menedżer transakcji nadal wysyła <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> powiadomienia do Menedżera zasobów, które zatwierdzeń transakcji rozproszonych, utworzony podczas eskalacji.

> [!NOTE]
> **TransactionCommitted** śledzenia (które są generowane, gdy jest wywoływana zatwierdzania eskalowanych transakcji) zawierają identyfikator działania transakcji usługi DTC.

Aby uzyskać więcej informacji na eskalacji zarządzania, zobacz [Eskalacja zarządzania transakcjami](../../../../docs/framework/data/transactions/transaction-management-escalation.md).

## <a name="transaction-management-escalation-scenario"></a>W tym scenariuszu eskalacji zarządzania transakcji

Następujący scenariusz pokazuje kontaktu z transakcji rozproszonych za pomocą <xref:System.Data> nazw jako "proxy" Menedżera zasobów. W tym scenariuszu przyjęto założenie, że istnieje już <xref:System.Data> połączenia z bazą danych, cn1, biorących udział w transakcji, a aplikacja będzie obejmować innego <xref:System.Data> połączenia, CN2. Transakcji musi zostać przekazany do usługi, jako transakcja pełną rozproszonej dwufazowe.

W tym scenariuszu

1. Wywołania CN1 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodę, aby zarejestrować transakcji. Następnie transakcja jest nadal lokalnego i nie ma żadnych awansowanie rejestracji w transakcji, więc <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> połączenie zakończy się powodzeniem.

2. Po drugie połączenie, CN2 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>, połączenie nie powiedzie się, ponieważ jest zaangażowane innego awansowanie rejestracji. W związku z tym CN2 musi uzyskać transakcję usługi, aby można było przekazać je do programu SQL. W tym celu używa jednej z metod dostarczonych przez <xref:System.Transactions.TransactionInterop> klasy w celu uzyskania formatu transakcji, która może być SQL.

3. <xref:System.Transactions> wywołania <xref:System.Transactions.ITransactionPromoter.Promote%2A> metody <xref:System.Transactions.ITransactionPromoter> interfejs implementowany przez CN1.

4. W tym momencie CN1 Eskalowanie transakcji, niektóre mechanizm specyficzne dla SQL 2005 i <xref:System.Data>.

5. Wartość zwrócona przez <xref:System.Transactions.ITransactionPromoter.Promote%2A> metoda jest zawierający tokenu propagacji transakcji tablicy bajtów. <xref:System.Transactions> używa tego tokenu propagacji, aby utworzyć transakcji usługi DTC, które można uwzględnić w lokalnym transakcję.

6. W tym momencie CN2 można użyć dane otrzymane z jednej z metod przez wywołanie <xref:System.Transactions.TransactionInterop> do przekazania transakcji SQL.

7. Teraz zarówno biorących udział w transakcji rozproszonych usługi.

## <a name="single-phase-commit-optimization"></a>Jedna faza zatwierdzania optymalizacji

Zatwierdź faza pojedynczy protokół jest bardziej wydajne w czasie wykonywania, ponieważ wszystkie aktualizacje są wykonywane bez jawnego koordynacji. Aby skorzystać z tego rodzaju optymalizacji, należy zaimplementować Menedżera zasobów przy użyciu <xref:System.Transactions.ISinglePhaseNotification> interfejs dla zasobu i zarejestrować się przy użyciu transakcji <xref:System.Transactions.Transaction.EnlistDurable%2A> lub <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody. W szczególności *EnlistmentOptions* powinna być równa parametr <xref:System.Transactions.EnlistmentOptions.None> do zapewnienia zatwierdzania jedna faza będzie można wykonać.

Ponieważ <xref:System.Transactions.ISinglePhaseNotification> pochodzi od klasy interfejs <xref:System.Transactions.IEnlistmentNotification> interfejsu, jeśli Twój Menedżera zasobów jest nieodpowiedni dla jednego etapu zatwierdzania, może nadal odbierać fazy dwa powiadomienia zatwierdzania. W przypadku otrzymania swojego menedżera zasobów <xref:System.Transactions.ISinglePhaseNotification.SinglePhaseCommit%2A> powiadomienie z Menedżer transakcji, jego starać się wykonują pracę niezbędne do zatwierdzania i odpowiednio informują menedżera transakcji, jeśli transakcja ma zostać przekazana lub wycofana przez wywołanie metody <xref:System.Transactions.SinglePhaseEnlistment.Committed%2A>, <xref:System.Transactions.SinglePhaseEnlistment.Aborted%2A>, lub <xref:System.Transactions.SinglePhaseEnlistment.InDoubt%2A> metody w <xref:System.Transactions.SinglePhaseEnlistment> parametru. Odpowiedź <xref:System.Transactions.Enlistment.Done%2A> na rejestracji na tym etapie oznacza semantyki tylko do odczytu. W związku z tym, nie powinien odpowiedź <xref:System.Transactions.Enlistment.Done%2A> dodatek do wszelkich innych metod.

Jeśli istnieje tylko jeden lotnych rejestracji i nie trwałej rejestracji, rejestracja lotnych odbiera powiadomienie SPC. W przypadku wszelkich nietrwałe i tylko jeden trwałej rejestracji, nietrwałe odbierać 2PC. Po zakończeniu, trwałej rejestracji odbiera SPC.

## <a name="see-also"></a>Zobacz także

- [Rejestrowanie zasobów jako uczestników transakcji](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)
- [Zatwierdzanie transakcji jednofazowe i wielofazowe](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)
