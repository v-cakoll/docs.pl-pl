---
title: Jednofazowe i wielofazowe zatwierdzanie transakcji
description: Przeczytaj o zatwierdzaniu transakcji w jednej lub dwóch fazach w programie .NET. Jeśli transakcja obejmuje więcej niż jeden zasób, należy wykonać dwufazowe zatwierdzenie (2PC).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: 2f4486998f347bf1db6d22433e6e48b553609c18
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141827"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a>Jednofazowe i wielofazowe zatwierdzanie transakcji
Poszczególne zasoby używane w transakcji jest zarządzane przez Menedżera zasobów (MB), w których działania są koordynowany przez Menedżera transakcji (TM). Zasoby związane z [rejestrowaniem w temacie transakcji](enlisting-resources-as-participants-in-a-transaction.md) omawiają sposób, w jaki zasób (lub wiele zasobów) może być zarejestrowany w transakcji. W tym temacie opisano, jak można skoordynowanego między wyświetlone zasoby zobowiązaniom transakcji.  
  
 Na końcu transakcji aplikacja żąda, aby transakcja została zatwierdzona lub wycofana. Menedżer transakcji musi wyeliminowania zagrożeń, takich jak niektórych menedżerów zasobów głosowanie zatwierdzić, podczas gdy inne głosowania można wycofać transakcji.  
  
 Transakcja wiąże się z więcej niż jeden zasób, należy wykonać dwufazowego (2PC). Protokół dwufazowego (fazy przygotowania i fazy rezerwacji) zapewnia, że po zakończeniu transakcji, wszystkie zmiany do wszystkich zasobów są całkowicie zadeklarowanej lub w pełni przywrócona. Wszyscy uczestnicy są następnie poinformowany o wyniku końcowego. Aby zapoznać się ze szczegółami dotyczącymi dwufazowego protokołu zatwierdzania, zapoznaj się z książką "*Przetwarzanie transakcji: koncepcje i techniki (seria Morgan Kaufmann w systemach zarządzanie danymi) ISBN: 1558601902*" przez Jim szare.  
  
 Można także zoptymalizować wydajność Twojej transakcji przez biorących udział w protokole zatwierdzania jednego etapu. Aby uzyskać więcej informacji, zobacz [Optymalizacja przy użyciu jednej fazy zatwierdzania i powiadomienia o pojedynczej fazie](optimization-spc-and-promotable-spn.md).  
  
 Jeśli po prostu chcesz informujące o wyniku transakcji i zrezygnować z uczestnictwa w głosowaniu, należy zarejestrować dla <xref:System.Transactions.Transaction.TransactionCompleted> zdarzenia.  
  
## <a name="two-phase-commit-2pc"></a>Dwufazowego (2PC)  
 W pierwszej fazy transakcji Menedżer transakcji pyta każdy zasób, aby ustalić, czy zatwierdzeniu lub wycofać transakcji. Drugi etap transakcji Menedżer transakcji powiadamia każdego zasobu wynik jego zapytań, dzięki któremu można wykonać wszelkie niezbędne czyszczenia.  
  
 Aby wziąć udział w tym rodzaju transakcji, Menedżer zasobów musi zaimplementować <xref:System.Transactions.IEnlistmentNotification> interfejs, który zapewnia metody wywoływane przez Menedżera TM jako powiadomienia podczas 2PC.  W poniższym przykładzie przedstawiono przykład takiej implementacji.  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a>Przygotuj faza (fazy 1)  
 Po odebraniu <xref:System.Transactions.CommittableTransaction.Commit%2A> żądania od aplikacji Menedżer transakcji rozpoczyna przygotowywanie wszystkich uczestników uczestniczących przez wywołanie <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metody dla każdego zarejestrowanego zasobu w celu uzyskania głosu każdego zasobu na transakcję.  
  
 Menedżer zasobów implementujący <xref:System.Transactions.IEnlistmentNotification> interfejs powinien najpierw zaimplementować <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> metodę, jak pokazano w poniższym przykładzie.  
  
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
  
 Po odebraniu tego wywołania przez Menedżera zasobów trwałych powinien on rejestrować informacje o odzyskiwaniu transakcji (dostępne przez pobranie <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> Właściwości) i informacje, które są niezbędne do ukończenia transakcji po zatwierdzeniu. To nie jest konieczne jest wykonywana w ramach <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> metoda, ponieważ Menedżer zasobów można to zrobić w wątku roboczego.  
  
 Po zakończeniu Menedżera zasobów jego przygotowania pracy, należy głosowania przekazać ani wycofać przez wywołanie metody <xref:System.Transactions.PreparingEnlistment.Prepared%2A> lub <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> metody. Należy zauważyć, że <xref:System.Transactions.PreparingEnlistment> klasa dziedziczy <xref:System.Transactions.Enlistment.Done%2A> metodę z <xref:System.Transactions.Enlistment> klasy. Wywołanie tej metody na <xref:System.Transactions.PreparingEnlistment> wywołania zwrotnego w fazie przygotowania, informuje Menedżer transakcji czy jest tylko do odczytu rejestracji (czyli menedżerów zasobów, które może być odczytany, ale nie można zaktualizować dane chronione przed transakcjami) i Menedżera zasobów odbiera żadne dalsze powiadomienia z menedżerem transakcji wyniku transakcji w fazie 2.  
  
 Aplikacja jest powiadamiana o pomyślnym zobowiązaniu transakcji po zagłosowaniu wszystkich menedżerów zasobów <xref:System.Transactions.PreparingEnlistment.Prepared%2A> .  
  
### <a name="commit-phase-phase-2"></a>Zatwierdź fazy (faza 2)  
 W drugiej fazy transakcji, gdy Menedżer transakcji odbiera pomyślne przygotowuje z wszystkich menedżerów zasobów (wywoływane ma wszystkich menedżerów zasobów <xref:System.Transactions.PreparingEnlistment.Prepared%2A> na końcu fazy 1), wywołuje ono <xref:System.Transactions.IEnlistmentNotification.Commit%2A> metody dla każdego Menedżera zasobów. Menedżerowie zasobów mogą następnie wprowadzić trwałe zmiany i zakończyć zatwierdzenie.  
  
 Jeśli którykolwiek z menedżerów zasobów zgłosił niepowodzenie przygotowania w fazie 1, Menedżer transakcji wywołuje <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> metodę dla każdego Menedżera zasobów i wskazuje niepowodzenie zatwierdzenia aplikacji.  
  
 W tym celu Menedżer zasobów powinien zaimplementować następujące metody.  
  
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
  
 Menedżer zasobów powinien wykonać wszelkie prace niezbędne do zakończenia transakcji na podstawie typu powiadomień i informuje Menedżer transakcji, który zakończył się przez wywołanie metody <xref:System.Transactions.Enlistment.Done%2A> metody w <xref:System.Transactions.Enlistment> parametru. Tej pracy można wykonać na wątku roboczego. Należy pamiętać, że powiadomieniami 2 może się tak zdarzyć tekście w tym samym wątku, który wywołał <xref:System.Transactions.PreparingEnlistment.Prepared%2A> metody w fazie 1. W związku z tym nie należy wykonywać żadnej pracy po <xref:System.Transactions.PreparingEnlistment.Prepared%2A> wywołaniu (na przykład zwalniać blokad), które należy wykonać przed odebraniem powiadomień fazy 2.  
  
### <a name="implementing-indoubt"></a>Zaimplementowanie wątpliwości  
 Na koniec należy zaimplementować <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> metodę dla Menedżera zasobów lotnych. Ta metoda jest wywoływana, gdy Menedżer transakcji traci kontaktu z jednego lub więcej uczestników, więc ich stan jest nieznany. W takim przypadku powinni wylogować się ten fakt tak, aby można było zbadać później czy wszystkich uczestników transakcji pozostały w niespójnym stanie.  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a>Jedna faza zatwierdzania optymalizacji  
 Protokół zatwierdzania pojedynczej fazy jest bardziej wydajny w czasie wykonywania, ponieważ wszystkie aktualizacje są wykonywane bez jawnej koordynacji. Aby uzyskać więcej informacji na temat tego protokołu, zobacz [Optymalizacja przy użyciu jednej fazy zatwierdzania i powiadomienia o pojedynczej fazie](optimization-spc-and-promotable-spn.md).  
  
## <a name="see-also"></a>Zobacz też

- [Optymalizacja za pomocą zatwierdzania jednofazowego i umożliwiającego awansowanie powiadomienia jednofazowego](optimization-spc-and-promotable-spn.md)
- [Rejestrowanie zasobów jako uczestników transakcji](enlisting-resources-as-participants-in-a-transaction.md)
