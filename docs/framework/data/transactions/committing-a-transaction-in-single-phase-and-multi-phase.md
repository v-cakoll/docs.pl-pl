---
title: Jednofazowe i wielofazowe zatwierdzanie transakcji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: cbe00fb792ab5f2a7586a958ddbe5bdf004656dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875969"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a>Jednofazowe i wielofazowe zatwierdzanie transakcji
Poszczególne zasoby używane w transakcji jest zarządzane przez Menedżera zasobów (MB), w których działania są koordynowany przez Menedżera transakcji (TM). [Rejestrowanie zasobów jako uczestników transakcji](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) temacie omówiono, jak (lub wiele zasobów) może być zarejestrowany w transakcji. W tym temacie opisano, jak można skoordynowanego między wyświetlone zasoby zobowiązaniom transakcji.  
  
 Na koniec transakcji aplikacji żądań transakcji można zadeklarowane lub wycofana. Menedżer transakcji musi wyeliminowania zagrożeń, takich jak niektórych menedżerów zasobów głosowanie zatwierdzić, podczas gdy inne głosowania można wycofać transakcji.  
  
 Transakcja wiąże się z więcej niż jeden zasób, należy wykonać dwufazowego (2PC). Protokół dwufazowego (fazy przygotowania i fazy rezerwacji) zapewnia, że po zakończeniu transakcji, wszystkie zmiany do wszystkich zasobów są całkowicie zadeklarowanej lub w pełni przywrócona. Wszyscy uczestnicy są następnie poinformowany o wyniku końcowego. Szczegółowe omówienie protokołu dwufazowego, można znaleźć w książce "*przetwarzania transakcji: Pojęcia i techniki (Morgan Kaufmann serie danych systemów zarządzania) ISBN: 1558601902*"przez Jim szary.  
  
 Można także zoptymalizować wydajność Twojej transakcji przez biorących udział w protokole zatwierdzania jednego etapu. Aby uzyskać więcej informacji, zobacz [Optymalizacja za pomocą zatwierdzania jednofazowego i awansowanie powiadomienia jednofazowego](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
 Jeśli po prostu chcesz informujące o wyniku transakcji i zrezygnować z uczestnictwa w głosowaniu, należy zarejestrować dla <xref:System.Transactions.Transaction.TransactionCompleted> zdarzenia.  
  
## <a name="two-phase-commit-2pc"></a>Dwufazowego (2PC)  
 W pierwszej fazy transakcji Menedżer transakcji pyta każdy zasób, aby ustalić, czy zatwierdzeniu lub wycofać transakcji. Drugi etap transakcji Menedżer transakcji powiadamia każdego zasobu wynik jego zapytań, dzięki któremu można wykonać wszelkie niezbędne czyszczenia.  
  
 Aby uczestniczyć w tego rodzaju transakcji, Menedżer zasobów musi implementować <xref:System.Transactions.IEnlistmentNotification> interfejs, który udostępnia metody, które są wywoływane przez Menedżer transakcji jako powiadomienia podczas 2PC.  Poniższy przykład pokazuje przykład takich realizacji.  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a>Przygotuj faza (fazy 1)  
 Odebrane <xref:System.Transactions.CommittableTransaction.Commit%2A> żądania od aplikacji, Menedżer transakcji rozpoczyna fazy Prepare wszystkich uczestników biorących udział przez wywołanie metody <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metody na każdym zarejestrowany zasobów, w celu uzyskania każdego zasobu użytkownika Zagłosuj transakcja.  
  
 Twoje usługi resource manager, który implementuje <xref:System.Transactions.IEnlistmentNotification> najpierw należy zaimplementować interfejs <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> metody, co ilustruje poniższy przykład.  
  
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
  
 Jeśli Menedżera zasobów trwałe odbierający to wywołanie, jego powinni wylogować informacji o odzyskiwaniu transakcji (dostępne pobierając <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> właściwości) i wszelkich informacji, jakie jest niezbędny do zrealizowania transakcji na zatwierdzania. To nie jest konieczne jest wykonywana w ramach <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metoda, ponieważ Menedżer zasobów można to zrobić w wątku roboczego.  
  
 Po zakończeniu Menedżera zasobów jego przygotowania pracy, należy głosowania przekazać ani wycofać przez wywołanie metody <xref:System.Transactions.PreparingEnlistment.Prepared%2A> lub <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> metody. Należy zauważyć, że <xref:System.Transactions.PreparingEnlistment> klasa dziedziczy <xref:System.Transactions.Enlistment.Done%2A> metodę z <xref:System.Transactions.Enlistment> klasy. Wywołanie tej metody na <xref:System.Transactions.PreparingEnlistment> wywołania zwrotnego w fazie przygotowania, informuje Menedżer transakcji czy jest tylko do odczytu rejestracji (czyli menedżerów zasobów, które może być odczytany, ale nie można zaktualizować dane chronione przed transakcjami) i Menedżera zasobów odbiera żadne dalsze powiadomienia z menedżerem transakcji wyniku transakcji w fazie 2.  
  
 Aplikacja jest poinformował pomyślne zobowiązania transakcji po głosowania wszystkich menedżerów zasobów <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.  
  
### <a name="commit-phase-phase-2"></a>Zatwierdź fazy (faza 2)  
 W drugiej fazy transakcji, gdy Menedżer transakcji odbiera pomyślne przygotowuje z wszystkich menedżerów zasobów (wywoływane ma wszystkich menedżerów zasobów <xref:System.Transactions.PreparingEnlistment.Prepared%2A> na końcu fazy 1), wywołuje ono <xref:System.Transactions.IEnlistmentNotification.Commit%2A> metody dla każdego Menedżera zasobów. Menedżerowie zasobów można zmieniać trwałe i ukończyć zatwierdzania.  
  
 Jeśli którykolwiek z menedżerów zasobów zgłosił niepowodzenie przygotowania w fazie 1, Menedżer transakcji wywołuje <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> metody dla każdego Menedżera zasobów i wskazuje niepowodzeniem zatwierdzania do aplikacji.  
  
 W związku z tym Menedżera zasobów zaimplementować następujące metody.  
  
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
  
 Menedżer zasobów powinien wykonać wszelkie prace niezbędne do zakończenia transakcji na podstawie typu powiadomień i informuje Menedżer transakcji, który zakończył się przez wywołanie metody <xref:System.Transactions.Enlistment.Done%2A> metody w <xref:System.Transactions.Enlistment> parametru. Tej pracy można wykonać na wątku roboczego. Należy pamiętać, że powiadomieniami 2 może się tak zdarzyć tekście w tym samym wątku, który wywołał <xref:System.Transactions.PreparingEnlistment.Prepared%2A> metody w fazie 1. W efekcie nie powinien wykonać pracę po <xref:System.Transactions.PreparingEnlistment.Prepared%2A> wywołania (na przykład uwalniający blokady), które powinny być została ukończona przed odbierał powiadomienia fazy 2.  
  
### <a name="implementing-indoubt"></a>Wykonania wątpliwych  
 Na koniec należy zaimplementować <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> metodę dla Menedżera zasobów lotnych. Ta metoda jest wywoływana, gdy Menedżer transakcji traci kontaktu z jednego lub więcej uczestników, więc ich stan jest nieznany. W takim przypadku powinni wylogować się ten fakt tak, aby można było zbadać później czy wszystkich uczestników transakcji pozostały w niespójnym stanie.  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a>Jedna faza zatwierdzania optymalizacji  
 Zatwierdź faza pojedynczy protokół jest bardziej wydajne w czasie wykonywania, ponieważ wszystkie aktualizacje są wykonywane bez jawnego koordynacji. Aby uzyskać więcej informacji dotyczących tego protokołu, zobacz [Optymalizacja za pomocą zatwierdzania jednofazowego i awansowanie powiadomienia jednofazowego](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
## <a name="see-also"></a>Zobacz także

- [Optymalizacja za pomocą zatwierdzania jednofazowego i umożliwiającego awansowanie powiadomienia jednofazowego](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)
- [Rejestrowanie zasobów jako uczestników transakcji](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)
