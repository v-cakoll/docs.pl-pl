---
title: Optymalizacja za pomocą zatwierdzania jednofazowego i umożliwiającego awansowanie powiadomienia jednofazowego
ms.date: 03/30/2017
ms.assetid: 57beaf1a-fb4d-441a-ab1d-bc0c14ce7899
ms.openlocfilehash: f486315b8a8c90e6616ca95fb6be4b2ae3719b7e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205899"
---
# <a name="optimization-using-single-phase-commit-and-promotable-single-phase-notification"></a>Optymalizacja za pomocą zatwierdzania jednofazowego i umożliwiającego awansowanie powiadomienia jednofazowego

W tym temacie opisano mechanizmy udostępnione przez <xref:System.Transactions> infrastruktury w celu optymalizacji wydajności.

## <a name="promotable-single-phase-enlistment"></a>Rejestracja awansowanie jedna faza

<xref:System.Transactions> Infrastruktura administruje transakcją w jednej domenie aplikacji, która obejmuje co najwyżej jeden trwały zasób lub wiele zasobów lotnych. <xref:System.Transactions> Ponieważ infrastruktura używa tylko wywołań domeny wewnątrz aplikacji, zapewnia najlepszą przepływność i wydajność.

Jeśli jednak transakcja jest udostępniana innemu obiektowi w innej domenie aplikacji (w tym między granicami procesów i maszyn) na tym samym komputerze lub w przypadku rejestracji innego Menedżera zasobów trwałego, <xref:System.Transactions> infrastruktura automatycznie przekazuje transakcję, która ma być zarządzana przez usługę MSDTC. Zarządzane przez MSDTC transakcji nie jest performance-wise jako jeden zarządzane przez <xref:System.Transactions> infrastruktury.

W celu zoptymalizowania wydajności <xref:System.Transactions> infrastruktura zapewnia rejestrację z jednym etapem promocji (PSPE), która umożliwia pojedynczy zdalny zasób trwały, znajdujący się w innej domenie aplikacji, procesie lub maszynie, aby <xref:System.Transactions> uczestniczył w transakcja bez powodowania jego eskalacji do transakcji MSDTC. Ten Menedżer zasobu (MB) umożliwia przechowywanie i "własnością" transakcji, która później można przekazany do transakcji rozproszonych (lub transakcji MSDTC), jeśli to konieczne. Zmniejsza to prawdopodobieństwo za pomocą MSDTC.

Ten Menedżer określonego zasobu, zwykle ma własne wewnętrzne transakcje rozproszone bez i należy go obsługuje konwertowania tych transakcji na transakcje rozproszone w czasie wykonywania. Na przykład SQL Server 2005 to Menedżer zasobów. W takim przypadku <xref:System.Transactions> infrastruktury przyjmuje rolę Zarządzanie bierne po prostu Monitoruj transakcji na potrzeby eskalacji. Aby zapewnić obsługę interakcji między <xref:System.Transactions> usługą infrastruktury i menedżerem zasobów, ta ostatnia musi implementować interfejs. <xref:System.Transactions.IPromotableSinglePhaseNotification>

<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> Metoda służy do zarejestrować pojedynczy trwałe zasób, który może zostać przekazany później. Ta metoda zapewnia, że rejestracja może być przekazany zgodnie z potrzebami. Jeśli rejestracja zakończy się powodzeniem, Menedżer zasobów tworzy jego wewnętrznego transakcji i kojarzy ją z <xref:System.Transactions> transakcji. W przypadku niepowodzenia rejestracji PSPE Menedżera zasobów zamiast tego należy zarejestrować przy użyciu <xref:System.Transactions.Transaction.EnlistDurable%2A> metody. Błędów, aby zarejestrować PSPE może się zdarzyć, gdy transakcja została już transakcja rozproszona lub innego menedżera zasobów przeprowadził już rejestracji PSPE

Gdy zarejestrowana, wywołuje przez klientów, aby zatwierdzić lub przerwać <xref:System.Transactions> transakcji są konwertowane na wywołania na Menedżera zasobów, wywołując <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> metody lub <xref:System.Transactions.IPromotableSinglePhaseNotification.Rollback%2A> odpowiednio.

Jeśli <xref:System.Transactions> transakcji nigdy nie wymaga eskalacji, gdy transakcja zostanie zatwierdzone, Menedżer zasobów odbiera <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> powiadomienia. Można ją następnie Zatwierdź wewnętrzny transakcji, która została początkowo utworzona.

<xref:System.Transactions.IPromotableSinglePhaseNotification> <xref:System.Transactions.ITransactionPromoter> <xref:System.Transactions.ITransactionPromoter.Promote%2A> <xref:System.Transactions> Jeśli transakcja musi zostać przeeskalacjna (np. w celu obsługi wielu usług RMS), program informuje Menedżera zasobów przez wywołanie metody w interfejsie, z którego pochodzi interfejs. <xref:System.Transactions> Menedżer zasobów następnie konwertuje transakcji wewnętrznie z lokalnym transakcji (które nie wymagają rejestrowania) obiekt transakcji, który jest w stanie udział w transakcji usługi i kojarzy ją z już pracy. Gdy transakcja jest proszony o zatwierdzania, Menedżer transakcji nadal wysyła <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> powiadomienia do Menedżera zasobów, które zatwierdzeń transakcji rozproszonych, utworzony podczas eskalacji.

> [!NOTE]
> Ślady **TransactionCommitted** (które są generowane w przypadku wywołania zatwierdzenia dla transakcji eskalacji) zawierają identyfikator działania transakcji usługi DTC.

Aby uzyskać więcej informacji na temat eskalacji zarządzania, zobacz [Eskalacja zarządzania](transaction-management-escalation.md)transakcjami.

## <a name="transaction-management-escalation-scenario"></a>W tym scenariuszu eskalacji zarządzania transakcji

Następujący scenariusz pokazuje kontaktu z transakcji rozproszonych za pomocą <xref:System.Data> nazw jako "proxy" Menedżera zasobów. W tym scenariuszu przyjęto założenie <xref:System.Data> , że istnieje już jedno połączenie z bazą danych, CN1, biorąc udział w transakcji, a aplikacja <xref:System.Data> chce zaangażować inne połączenie, CN2. Transakcji musi zostać przekazany do usługi, jako transakcja pełną rozproszonej dwufazowe.

W tym scenariuszu

1. Wywołania CN1 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodę, aby zarejestrować transakcji. Następnie transakcja jest nadal lokalnego i nie ma żadnych awansowanie rejestracji w transakcji, więc <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> połączenie zakończy się powodzeniem.

2. Po drugie połączenie, CN2 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>, połączenie nie powiedzie się, ponieważ jest zaangażowane innego awansowanie rejestracji. W związku z tym CN2 musi uzyskać transakcję usługi, aby można było przekazać je do programu SQL. W tym celu używa jednej z metod dostarczonych przez <xref:System.Transactions.TransactionInterop> klasy w celu uzyskania formatu transakcji, która może być SQL.

3. <xref:System.Transactions><xref:System.Transactions.ITransactionPromoter.Promote%2A> wywołuje metodę <xref:System.Transactions.ITransactionPromoter> w interfejsie zaimplementowanym przez CN1.

4. W tym momencie CN1 Eskalowanie transakcji, niektóre mechanizm specyficzne dla SQL 2005 i <xref:System.Data>.

5. Wartość zwrócona przez <xref:System.Transactions.ITransactionPromoter.Promote%2A> metoda jest zawierający tokenu propagacji transakcji tablicy bajtów. <xref:System.Transactions>używa tego tokenu propagacji, aby utworzyć transakcję usługi DTC, którą może uwzględnić w transakcji lokalnej.

6. W tym momencie CN2 można użyć dane otrzymane z jednej z metod przez wywołanie <xref:System.Transactions.TransactionInterop> do przekazania transakcji SQL.

7. Teraz zarówno biorących udział w transakcji rozproszonych usługi.

## <a name="single-phase-commit-optimization"></a>Jedna faza zatwierdzania optymalizacji

Protokół zatwierdzania pojedynczej fazy jest bardziej wydajny w czasie wykonywania, ponieważ wszystkie aktualizacje są wykonywane bez żadnej bezpośredniej koordynacji. Aby skorzystać z tej optymalizacji, należy zaimplementować usługę Resource Manager za pomocą <xref:System.Transactions.ISinglePhaseNotification> interfejsu dla zasobu i zarejestrować w transakcji <xref:System.Transactions.Transaction.EnlistDurable%2A> przy użyciu metody lub <xref:System.Transactions.Transaction.EnlistVolatile%2A> . W odniesieniu do parametru *EnlistmentOptions* należy <xref:System.Transactions.EnlistmentOptions.None> upewnić się, że zostanie wykonane zatwierdzenie pojedynczej fazy.

Ponieważ <xref:System.Transactions.ISinglePhaseNotification> pochodzi od klasy interfejs <xref:System.Transactions.IEnlistmentNotification> interfejsu, jeśli Twój Menedżera zasobów jest nieodpowiedni dla jednego etapu zatwierdzania, może nadal odbierać fazy dwa powiadomienia zatwierdzania. W przypadku otrzymania swojego menedżera zasobów <xref:System.Transactions.ISinglePhaseNotification.SinglePhaseCommit%2A> powiadomienie z Menedżer transakcji, jego starać się wykonują pracę niezbędne do zatwierdzania i odpowiednio informują menedżera transakcji, jeśli transakcja ma zostać przekazana lub wycofana przez wywołanie metody <xref:System.Transactions.SinglePhaseEnlistment.Committed%2A>, <xref:System.Transactions.SinglePhaseEnlistment.Aborted%2A>, lub <xref:System.Transactions.SinglePhaseEnlistment.InDoubt%2A> metody w <xref:System.Transactions.SinglePhaseEnlistment> parametru. Odpowiedź <xref:System.Transactions.Enlistment.Done%2A> na rejestrację na tym etapie oznacza semantykę tylko do odczytu. W związku z tym nie należy <xref:System.Transactions.Enlistment.Done%2A> wysyłać odpowiedzi oprócz innych metod.

Jeśli istnieje tylko jedna nietrwała Rejestracja i nie ma trwałej rejestracji, nietrwała Rejestracja odbiera powiadomienie SPC. Jeśli istnieją jakieś nietrwałe rejestracje i tylko jedna trwała rejestracja, nietrwałe rejestracji odbierają 2PC. Po zakończeniu trwałej rejestracji odbiera SPC.

## <a name="see-also"></a>Zobacz także

- [Rejestrowanie zasobów jako uczestników transakcji](enlisting-resources-as-participants-in-a-transaction.md)
- [Zatwierdzanie transakcji jednofazowe i wielofazowe](committing-a-transaction-in-single-phase-and-multi-phase.md)
