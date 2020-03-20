---
title: Jednofazowe i wielofazowe zatwierdzanie transakcji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: 8d6c51249f104d35573507a9477a24d66d770693
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174436"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a>Jednofazowe i wielofazowe zatwierdzanie transakcji
Poszczególne zasoby używane w transakcji jest zarządzane przez Menedżera zasobów (MB), w których działania są koordynowany przez Menedżera transakcji (TM). [Rejestrowanie zasobów jako uczestników w](enlisting-resources-as-participants-in-a-transaction.md) temacie Transakcja omawia, jak zasób (lub wiele zasobów) mogą być zarejestrowane w transakcji. W tym temacie opisano, jak można skoordynowanego między wyświetlone zasoby zobowiązaniom transakcji.  
  
 Na końcu transakcji aplikacja żąda transakcji do zaauconego lub wycofane. Menedżer transakcji musi wyeliminowania zagrożeń, takich jak niektórych menedżerów zasobów głosowanie zatwierdzić, podczas gdy inne głosowania można wycofać transakcji.  
  
 Transakcja wiąże się z więcej niż jeden zasób, należy wykonać dwufazowego (2PC). Protokół dwufazowego (fazy przygotowania i fazy rezerwacji) zapewnia, że po zakończeniu transakcji, wszystkie zmiany do wszystkich zasobów są całkowicie zadeklarowanej lub w pełni przywrócona. Wszyscy uczestnicy są następnie poinformowany o wyniku końcowego. Szczegółowe omówienie dwufazowego protokołu zatwierdzania można znaleźć w książce "*Transaction Processing : Concepts and Techniques (Morgan Kaufmann Series in Data Management Systems) ISBN:1558601902*" autorstwa Jima Graya.  
  
 Można także zoptymalizować wydajność Twojej transakcji przez biorących udział w protokole zatwierdzania jednego etapu. Aby uzyskać więcej informacji, zobacz [Optymalizacja przy użyciu zatwierdzania jednofazowego i powiadomienia jednofazowego zdatnym do promowania](optimization-spc-and-promotable-spn.md).  
  
 Jeśli po prostu chcesz informujące o wyniku transakcji i zrezygnować z uczestnictwa w głosowaniu, należy zarejestrować dla <xref:System.Transactions.Transaction.TransactionCompleted> zdarzenia.  
  
## <a name="two-phase-commit-2pc"></a>Dwufazowego (2PC)  
 W pierwszej fazy transakcji Menedżer transakcji pyta każdy zasób, aby ustalić, czy zatwierdzeniu lub wycofać transakcji. Drugi etap transakcji Menedżer transakcji powiadamia każdego zasobu wynik jego zapytań, dzięki któremu można wykonać wszelkie niezbędne czyszczenia.  
  
 Aby uczestniczyć w tego rodzaju transakcji, menedżer <xref:System.Transactions.IEnlistmentNotification> zasobów musi zaimplementować interfejs, który zawiera metody, które są wywoływane przez TM jako powiadomienia podczas 2PC.  Poniższy przykład przedstawia przykład takiej implementacji.  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a>Przygotuj faza (fazy 1)  
 Po otrzymaniu <xref:System.Transactions.CommittableTransaction.Commit%2A> żądania z aplikacji, menedżer transakcji rozpoczyna fazę przygotowania wszystkich ujęć uczestników, wywołując <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metodę na każdym zarejestrowanym zasobie, aby uzyskać głos każdego zasobu w sprawie transakcji.  
  
 Menedżer zasobów, który <xref:System.Transactions.IEnlistmentNotification> implementuje interfejs <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> należy najpierw zaimplementować metodę, jak pokazano w poniższym przykładzie proste.  
  
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
  
 Gdy menedżer zasobów trwałe odbiera to wywołanie, należy rejestrować informacje odzyskiwania <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> transakcji (dostępne przez pobieranie właściwości) i wszelkie informacje są niezbędne do ukończenia transakcji na zatwierdzenie. To nie jest konieczne jest wykonywana w ramach <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metoda, ponieważ Menedżer zasobów można to zrobić w wątku roboczego.  
  
 Po zakończeniu Menedżera zasobów jego przygotowania pracy, należy głosowania przekazać ani wycofać przez wywołanie metody <xref:System.Transactions.PreparingEnlistment.Prepared%2A> lub <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> metody. Należy zauważyć, że <xref:System.Transactions.PreparingEnlistment> klasa dziedziczy <xref:System.Transactions.Enlistment.Done%2A> metodę z <xref:System.Transactions.Enlistment> klasy. Wywołanie tej metody na <xref:System.Transactions.PreparingEnlistment> wywołania zwrotnego w fazie przygotowania, informuje Menedżer transakcji czy jest tylko do odczytu rejestracji (czyli menedżerów zasobów, które może być odczytany, ale nie można zaktualizować dane chronione przed transakcjami) i Menedżera zasobów odbiera żadne dalsze powiadomienia z menedżerem transakcji wyniku transakcji w fazie 2.  
  
 Aplikacja jest informowana o udanym zaangażowaniu transakcji <xref:System.Transactions.PreparingEnlistment.Prepared%2A>po głosowaniu wszystkich menedżerów zasobów .  
  
### <a name="commit-phase-phase-2"></a>Zatwierdź fazy (faza 2)  
 W drugiej fazy transakcji, gdy Menedżer transakcji odbiera pomyślne przygotowuje z wszystkich menedżerów zasobów (wywoływane ma wszystkich menedżerów zasobów <xref:System.Transactions.PreparingEnlistment.Prepared%2A> na końcu fazy 1), wywołuje ono <xref:System.Transactions.IEnlistmentNotification.Commit%2A> metody dla każdego Menedżera zasobów. Menedżerowie zasobów można następnie wprowadzić zmiany trwałe i zakończyć zatwierdzanie.  
  
 Jeśli dowolny menedżer zasobów zgłosił niepowodzenie przygotowania w fazie 1, menedżer transakcji wywołuje <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> metodę dla każdego menedżera zasobów i wskazuje niepowodzenie zatwierdzenia aplikacji.  
  
 W związku z tym menedżer zasobów należy zaimplementować następujące metody.  
  
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
  
 Menedżer zasobów powinien wykonać wszelkie prace niezbędne do zakończenia transakcji na podstawie typu powiadomień i informuje Menedżer transakcji, który zakończył się przez wywołanie metody <xref:System.Transactions.Enlistment.Done%2A> metody w <xref:System.Transactions.Enlistment> parametru. Tej pracy można wykonać na wątku roboczego. Należy pamiętać, że powiadomieniami 2 może się tak zdarzyć tekście w tym samym wątku, który wywołał <xref:System.Transactions.PreparingEnlistment.Prepared%2A> metody w fazie 1. W związku z tym nie należy <xref:System.Transactions.PreparingEnlistment.Prepared%2A> wykonywać żadnej pracy po wywołaniu (na przykład zwalnianie blokad), które można oczekiwać, że zostały zakończone przed odebraniem powiadomień fazy 2.  
  
### <a name="implementing-indoubt"></a>Wdrażanie indoubt  
 Na koniec należy zaimplementować <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> metodę dla menedżera zasobów nietrwałych. Ta metoda jest wywoływana, gdy Menedżer transakcji traci kontaktu z jednego lub więcej uczestników, więc ich stan jest nieznany. W takim przypadku powinni wylogować się ten fakt tak, aby można było zbadać później czy wszystkich uczestników transakcji pozostały w niespójnym stanie.  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a>Jedna faza zatwierdzania optymalizacji  
 Protokół zatwierdzania jednofazowego jest bardziej wydajny w czasie wykonywania, ponieważ wszystkie aktualizacje są wykonywane bez jawną koordynację. Aby uzyskać więcej informacji na temat tego protokołu, zobacz [Optymalizacja przy użyciu zatwierdzania jednofazowego i powiadomienia jednofazowego zdatnym do promowania](optimization-spc-and-promotable-spn.md).  
  
## <a name="see-also"></a>Zobacz też

- [Optymalizacja za pomocą zatwierdzania jednofazowego i umożliwiającego awansowanie powiadomienia jednofazowego](optimization-spc-and-promotable-spn.md)
- [Rejestrowanie zasobów jako uczestników transakcji](enlisting-resources-as-participants-in-a-transaction.md)
