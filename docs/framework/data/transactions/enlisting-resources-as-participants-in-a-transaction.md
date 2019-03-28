---
title: Rejestrowanie zasobów jako uczestników transakcji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 786a12c2-d530-49f4-9c59-5c973e15a11d
ms.openlocfilehash: 98872bd3ccddb1696b37eace0e28156cdbe002dc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366104"
---
# <a name="enlisting-resources-as-participants-in-a-transaction"></a>Rejestrowanie zasobów jako uczestników transakcji

Każdy zasób Udział w transakcji jest zarządzane przez Menedżera zasobów, których działania są koordynowany przez Menedżera transakcji. Koordynacja jest wykonywane za pośrednictwem powiadomienia do subskrybentów, którzy mają zarejestrowane w transakcji za pośrednictwem Menedżera transakcji.

W tym temacie opisano, jak (lub wiele zasobów) może być zarejestrowany w transakcji, a także różnych typów rejestracji. [Zatwierdzanie transakcji jednofazowe i wielofazowe](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md) temacie opisano, jak można skoordynowanego między wyświetlone zasoby zobowiązaniom transakcji.

## <a name="enlisting-resources-in-a-transaction"></a>Rejestrowanie zasobów w transakcji

Aby zasób, aby uczestniczyć w transakcji należy zarejestrować w transakcji. <xref:System.Transactions.Transaction> Klasa definiuje zestaw metod, których nazwy zaczynają się od **Enlist** , zapewnienia tej funkcji. Poszczególne **Enlist** metody odpowiada różnego rodzaju rejestracji, które mogą mieć Menedżera zasobów. W szczególności użyj <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody dla lotnych zasoby i <xref:System.Transactions.Transaction.EnlistDurable%2A> metody dla trwałego zasobów. Trwałość (lub odwrotnie niestabilności ich) zasobu menedżera odwołuje się do tego, czy Menedżera zasobów obsługuje odzyskiwanie po awarii. Jeśli Menedżera zasobów obsługuje odzyskiwanie po awarii, utrzymuje danych do trwałego magazynu podczas fazy 1. (przygotowanie) tak, aby w przypadku awarii Menedżera zasobów, można ponownie zarejestrować transakcji po odzyskiwania i wykonać właściwe działania w oparciu o powiadomienia otrzymane z Menedżer transakcji. Ogólnie rzecz biorąc menedżerów zasobów lotnych zarządzania lotnych zasoby, takie jak struktura danych w pamięci (na przykład w pamięci transacted skrótów) oraz menedżerów zasobów trwałego zarządzania zasobów, które mają więcej trwały zapasowy magazyn (na przykład Baza danych jest którego zapasowy magazyn dysku).

Dla prostotę, po podjęcie decyzji o użyciu <xref:System.Transactions.Transaction.EnlistDurable%2A> lub <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody, w zależności od pomocy technicznej trwałości Twoje zasobu, należy zarejestrować materiał brać udziału w dwóch faza zatwierdzania (2PC) przez zaimplementowanie <xref:System.Transactions.IEnlistmentNotification> interfejs na potrzeby usługi Menedżer zasobów. Aby uzyskać więcej informacji dotyczących 2PC, zobacz [Zatwierdzanie transakcji jednofazowe i wielofazowe](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md).

Pojedynczy uczestnika, który można zarejestrować więcej niż jednej z tych protokołów przez wywołanie metody <xref:System.Transactions.Transaction.EnlistDurable%2A> i <xref:System.Transactions.Transaction.EnlistVolatile%2A> wiele razy.

### <a name="durable-enlistment"></a>Trwałej rejestracji

<xref:System.Transactions.Transaction.EnlistDurable%2A> Metody są używane do zarejestrować Menedżera zasobów uczestniczący w transakcji jako trwałe zasobu.  Oczekuje się, że jeśli Menedżera zasobów trwałe jest obniżona środku transakcji, można wykonywać odzyskiwania po jego zostanie przełączony w tryb online przez reenlisting (przy użyciu <xref:System.Transactions.TransactionManager.Reenlist%2A> metody) we wszystkich transakcjach, w których zostało uczestnika i nie zmieniła się pełne fazy 2 i wywołania <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> po zakończeniu przetwarzania odzyskiwania. Aby uzyskać więcej informacji na temat odzyskiwania, zobacz [przeprowadzania odzyskiwania](../../../../docs/framework/data/transactions/performing-recovery.md).

<xref:System.Transactions.Transaction.EnlistDurable%2A> Podjąć wszystkie metody <xref:System.Guid> obiektu jako jego pierwszym parametrem. <xref:System.Guid> Jest używana przez Menedżera transakcji do skojarzenia trwałej rejestracji z menedżerem określonego zasobu. Jako takie, należy bezwzględnie Menedżera zasobów stale używany w taki sam <xref:System.Guid> do identyfikacji nawet przez inny zasób menedżerów przy ponownym uruchomieniu, w przeciwnym razie odzyskiwania może zakończyć się niepowodzeniem.

Drugi parametr <xref:System.Transactions.Transaction.EnlistDurable%2A> metoda jest odwołanie do obiektu, który implementuje Menedżera zasobów, aby otrzymywać powiadomienia o transakcji. Przeciążenie, którego używasz informuje menedżera transakcji, czy Menedżera zasobów obsługuje optymalizacji jednego etapu zatwierdzania (SPC). W większości przypadków umożliwi wdrożenie <xref:System.Transactions.IEnlistmentNotification> interfejs do wzięcia udziału w dwufazowy proces zatwierdzania (2PC). Jednakże, jeśli chcesz zoptymalizować proces zatwierdzania, można rozważyć wykonania <xref:System.Transactions.ISinglePhaseNotification> interfejs dla SPC. Aby uzyskać więcej informacji dotyczących SPC, zobacz [Zatwierdzanie transakcji jednofazowe i wielofazowe](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md) i [Optymalizacja za pomocą zatwierdzania jednofazowego i awansowanie powiadomienia jednofazowego](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).

Trzeci parametr jest <xref:System.Transactions.EnlistmentOptions> wyliczenia, którego wartość może być <xref:System.Transactions.EnlistmentOptions.None> lub <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>. Jeśli wartość jest równa <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>, rejestracja może zarejestrować menedżerów dodatkowych zasobów po otrzymaniu zawiadomienia Prepare z menedżerem transakcji. Należy jednak pamiętać, że tego typu rejestracji jest nieodpowiedni dla pojedynczego Zatwierdź faza optymalizacji.

### <a name="volatile-enlistment"></a>Rejestracja lotnych

Uczestnicy zarządzania zasobami lotnych, takich jak pamięci podręcznej należy zarejestrować przy użyciu <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody. Takie obiekty mogą nie można uzyskać wynik transakcji lub odzyskać stan każdej transakcji, które uczestniczą w po awarii systemu.

W sposób opisany wcześniej, Menedżera zasobów spowodowałoby lotnych rejestracji, jeśli zarządza w pamięci, lotnych zasobu. Jedną z zalet za pomocą <xref:System.Transactions.Transaction.EnlistVolatile%2A> jest, że nie wymusza niepotrzebne eskalacji transakcji. Aby uzyskać więcej informacji na eskalacji transakcji, zobacz [Eskalacja zarządzania transakcjami](../../../../docs/framework/data/transactions/transaction-management-escalation.md) tematu. Rejestrowanie zmienności oznacza zarówno różnica w sposób rejestracji jest obsługiwany przez Menedżera transakcji, a także oczekiwano Menedżera zasobów przez Menedżera transakcji. Jest to spowodowane Menedżera zasobów lotnych nie wykonuje odzyskiwania. <xref:System.Transactions.Transaction.EnlistVolatile%2A> Metody nie przyjmują <xref:System.Guid> parametru, ponieważ Menedżer zasobów lotnych nie wykonuje odzyskiwania i nie może wywołać <xref:System.Transactions.TransactionManager.Reenlist%2A> metodę, którą <xref:System.Guid>.

Podobnie jak w przypadku trwałych rejestracji, niezależnie od metody przeciążenie umożliwia rejestrowanie oznacza menedżera transakcji czy Menedżera zasobów obsługuje optymalizacji Zatwierdź jednego etapu. Ponieważ Menedżer zasobów lotnych nie może wykonać odzyskiwania, żadne informacje odzyskiwania jest przeznaczony dla lotnych rejestracji w fazie Prepare. Dlatego wywołanie <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> metoda nie powoduje <xref:System.InvalidOperationException>.

Poniższy przykład przedstawia sposób zarejestrować obiektu jako uczestnika transakcji przy użyciu <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody.

[!code-csharp[Tx_Enlist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#1)]
[!code-vb[Tx_Enlist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#1)]

### <a name="optimizing-performance"></a>Optymalizacja wydajności

<xref:System.Transactions.Transaction> Klasa udostępnia także <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodę, aby zarejestrować awansowanie jednego etapu rejestracji (PSPE). Dzięki temu trwałe zasobu manager (MB), hosta i "własnością" transakcji, która może zostać później przekazany do były zarządzane przez MSDTC, jeśli to konieczne. Aby uzyskać więcej informacji na temat tego, zobacz [Optymalizacja za pomocą zatwierdzania jednofazowego i awansowanie powiadomienia jednofazowego](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).

## <a name="see-also"></a>Zobacz także

- [Optymalizacja za pomocą zatwierdzania jednofazowego i umożliwiającego awansowanie powiadomienia jednofazowego](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)
- [Zatwierdzanie transakcji jednofazowe i wielofazowe](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)
