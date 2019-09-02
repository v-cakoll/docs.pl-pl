---
title: Rejestrowanie zasobów jako uczestników transakcji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 786a12c2-d530-49f4-9c59-5c973e15a11d
ms.openlocfilehash: 83d83df0f747198e93dd64308b904cad5c7439ec
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205982"
---
# <a name="enlisting-resources-as-participants-in-a-transaction"></a>Rejestrowanie zasobów jako uczestników transakcji

Każdy zasób Udział w transakcji jest zarządzane przez Menedżera zasobów, których działania są koordynowany przez Menedżera transakcji. Koordynacja jest wykonywane za pośrednictwem powiadomienia do subskrybentów, którzy mają zarejestrowane w transakcji za pośrednictwem Menedżera transakcji.

W tym temacie opisano sposób, w jaki zasób (lub wiele zasobów) może być zarejestrowany w transakcji, a także różne typy rejestracji. [W temacie zatwierdzanie transakcji w ramach jednej fazy i](committing-a-transaction-in-single-phase-and-multi-phase.md) wielofazowej omówiono sposób koordynacji zobowiązania transakcji między zarejestrowanymi zasobami.

## <a name="enlisting-resources-in-a-transaction"></a>Rejestrowanie zasobów w transakcji

Aby zasób, aby uczestniczyć w transakcji należy zarejestrować w transakcji. Klasa definiuje zestaw metod, których nazwy zaczynają się od rejestracji, która zapewnia tę funkcję. <xref:System.Transactions.Transaction> Różne metody **rejestracji** odnoszą się do różnych typów rejestracji, które może mieć Menedżer zasobów. W szczególności użyj <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody dla lotnych zasoby i <xref:System.Transactions.Transaction.EnlistDurable%2A> metody dla trwałego zasobów. Trwałość (lub odwrotnie niestabilności ich) zasobu menedżera odwołuje się do tego, czy Menedżera zasobów obsługuje odzyskiwanie po awarii. Jeśli Menedżera zasobów obsługuje odzyskiwanie po awarii, utrzymuje danych do trwałego magazynu podczas fazy 1. (przygotowanie) tak, aby w przypadku awarii Menedżera zasobów, można ponownie zarejestrować transakcji po odzyskiwania i wykonać właściwe działania w oparciu o powiadomienia otrzymane z Menedżer transakcji. Ogólnie rzecz biorąc, Menedżerowie zasobów lotnych zarządzają zasobami nietrwałymi, takimi jak struktura danych w pamięci (na przykład w pamięci podręcznej), a trwałe Menedżerowie zasobów zarządzają zasobami, które mają bardziej trwały magazyn zapasowy (na przykład Baza danych, której magazyn zapasowy jest dyskiem).

Dla uproszczenia po podjęciu decyzji o tym, <xref:System.Transactions.Transaction.EnlistDurable%2A> czy <xref:System.Transactions.Transaction.EnlistVolatile%2A> użyć metody lub w oparciu o wsparcie trwałości zasobu, należy zarejestrować zasób, aby wziąć udział w dwóch fazach zatwierdzania ( <xref:System.Transactions.IEnlistmentNotification> 2PC) przez implementację interfejsu dla Resource Manager. Aby uzyskać więcej informacji na temat 2PC, zobacz temat [zatwierdzanie transakcji w ramach jednej fazy i](committing-a-transaction-in-single-phase-and-multi-phase.md)wielofazowej.

Pojedynczy uczestnik może zarejestrować się dla więcej niż jednego z tych protokołów przez <xref:System.Transactions.Transaction.EnlistDurable%2A> wywoływanie <xref:System.Transactions.Transaction.EnlistVolatile%2A> i wiele razy.

### <a name="durable-enlistment"></a>Trwałej rejestracji

<xref:System.Transactions.Transaction.EnlistDurable%2A> Metody są używane do zarejestrować Menedżera zasobów uczestniczący w transakcji jako trwałe zasobu.  Oczekuje się, że jeśli Menedżer zasobów trwałych zostanie wyłączony w trakcie transakcji, może wykonać odzyskiwanie po ponownym przełączeniu w tryb online przez ponowne zarejestrowanie (przy użyciu <xref:System.Transactions.TransactionManager.Reenlist%2A> metody) we wszystkich transakcjach, w których była uczestnikiem i nie Ukończ fazę 2 i Wywołaj <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> po zakończeniu przetwarzania odzyskiwania. Aby uzyskać więcej informacji o odzyskiwaniu, zobacz [odzyskiwanie](performing-recovery.md).

<xref:System.Transactions.Transaction.EnlistDurable%2A> Podjąć wszystkie metody <xref:System.Guid> obiektu jako jego pierwszym parametrem. <xref:System.Guid> Jest używana przez Menedżera transakcji do skojarzenia trwałej rejestracji z menedżerem określonego zasobu. Jako takie, należy bezwzględnie Menedżera zasobów stale używany w taki sam <xref:System.Guid> do identyfikacji nawet przez inny zasób menedżerów przy ponownym uruchomieniu, w przeciwnym razie odzyskiwania może zakończyć się niepowodzeniem.

Drugi parametr <xref:System.Transactions.Transaction.EnlistDurable%2A> metody jest odwołaniem do obiektu, który jest implementowany przez Menedżera zasobów, aby otrzymywać powiadomienia o transakcjach. Przeciążenie, którego używasz informuje menedżera transakcji, czy Menedżera zasobów obsługuje optymalizacji jednego etapu zatwierdzania (SPC). Większość czasu implementowania interfejsu, <xref:System.Transactions.IEnlistmentNotification> który ma być częścią zatwierdzania dwufazowego (2PC). Jeśli jednak chcesz zoptymalizować proces zatwierdzania, możesz rozważyć zaimplementowanie <xref:System.Transactions.ISinglePhaseNotification> interfejsu dla SPC. Aby uzyskać więcej informacji na temat połączenia SPC, zobacz temat [zatwierdzanie transakcji w ramach jednej fazy i](committing-a-transaction-in-single-phase-and-multi-phase.md) wieloetapowej i [optymalizacji przy użyciu powiadomienia o](optimization-spc-and-promotable-spn.md)pojedynczej fazie zatwierdzania i promocji jednofazowej.

Trzeci parametr jest <xref:System.Transactions.EnlistmentOptions> wyliczenia, którego wartość może być <xref:System.Transactions.EnlistmentOptions.None> lub <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>. Jeśli wartość jest równa <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>, rejestracja może zarejestrować menedżerów dodatkowych zasobów po otrzymaniu zawiadomienia Prepare z menedżerem transakcji. Należy jednak pamiętać, że tego typu rejestracji jest nieodpowiedni dla pojedynczego Zatwierdź faza optymalizacji.

### <a name="volatile-enlistment"></a>Rejestracja lotnych

Uczestnicy zarządzania zasobami lotnych, takich jak pamięci podręcznej należy zarejestrować przy użyciu <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody. Takie obiekty mogą nie można uzyskać wynik transakcji lub odzyskać stan każdej transakcji, które uczestniczą w po awarii systemu.

W sposób opisany wcześniej, Menedżera zasobów spowodowałoby lotnych rejestracji, jeśli zarządza w pamięci, lotnych zasobu. Jedną z zalet za pomocą <xref:System.Transactions.Transaction.EnlistVolatile%2A> jest, że nie wymusza niepotrzebne eskalacji transakcji. Aby uzyskać więcej informacji na temat eskalacji transakcji, zobacz temat [Eskalacja zarządzania](transaction-management-escalation.md) transakcjami. Zarejestrowanie zmienności oznacza różnicę w sposobie obsługi rejestracji przez Menedżera transakcji, a także to, czego oczekuje Menedżer zasobów przez Menedżera transakcji. Jest to spowodowane Menedżera zasobów lotnych nie wykonuje odzyskiwania. <xref:System.Transactions.Transaction.EnlistVolatile%2A> Metody nie przyjmują <xref:System.Guid> parametru, ponieważ Menedżer zasobów lotnych nie wykonuje odzyskiwania i nie może wywołać <xref:System.Transactions.TransactionManager.Reenlist%2A> metodę, którą <xref:System.Guid>.

Podobnie jak w przypadku trwałych rejestracji, niezależnie od metody przeciążenie umożliwia rejestrowanie oznacza menedżera transakcji czy Menedżera zasobów obsługuje optymalizacji Zatwierdź jednego etapu. Ponieważ Menedżer zasobów lotnych nie może wykonać odzyskiwania, żadne informacje odzyskiwania jest przeznaczony dla lotnych rejestracji w fazie Prepare. Dlatego wywołanie <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> metoda nie powoduje <xref:System.InvalidOperationException>.

Poniższy przykład pokazuje, jak zarejestrować taki obiekt jako uczestnik transakcji przy użyciu <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody.

[!code-csharp[Tx_Enlist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#1)]
[!code-vb[Tx_Enlist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#1)]

### <a name="optimizing-performance"></a>Optymalizacja wydajności

<xref:System.Transactions.Transaction> Klasa udostępnia także <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodę, aby zarejestrować awansowanie jednego etapu rejestracji (PSPE). Dzięki temu trwałe zasobu manager (MB), hosta i "własnością" transakcji, która może zostać później przekazany do były zarządzane przez MSDTC, jeśli to konieczne. Aby uzyskać więcej informacji na ten temat, zobacz [Optymalizacja przy użyciu jednej fazy zatwierdzania i powiadomienia o pojedynczej fazie](optimization-spc-and-promotable-spn.md).

## <a name="see-also"></a>Zobacz także

- [Optymalizacja za pomocą zatwierdzania jednofazowego i umożliwiającego awansowanie powiadomienia jednofazowego](optimization-spc-and-promotable-spn.md)
- [Zatwierdzanie transakcji jednofazowe i wielofazowe](committing-a-transaction-in-single-phase-and-multi-phase.md)
