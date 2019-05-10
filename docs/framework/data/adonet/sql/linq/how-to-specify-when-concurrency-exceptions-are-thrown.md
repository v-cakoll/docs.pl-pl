---
title: 'Instrukcje: Określanie, kiedy są zgłaszane wyjątki współbieżności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: 0be17e7ceb6a5e5230d2619be350266d0282078c
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910809"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a>Instrukcje: Określanie, kiedy są zgłaszane wyjątki współbieżności
W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.ChangeConflictException> wyjątek jest zgłaszany, gdy obiekty nie są uaktualniane z powodu konfliktów optymistycznej współbieżności. Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Przed przesłaniem zmian do bazy danych można określić podczas powinny zostać zgłoszone wyjątki współbieżności:  
  
- Zgłoszenie wyjątku w pierwszym niepowodzeniu (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).  
  
- Zakończenie wszystkich prób aktualizacji, są gromadzone wszystkie błędy i zgłaszać narastająco błędy w wyjątku (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).  
  
 Jeśli zgłoszony, <xref:System.Data.Linq.ChangeConflictException> wyjątek zapewnia dostęp do <xref:System.Data.Linq.ChangeConflictCollection> kolekcji. Ta kolekcja zawiera szczegółowe informacje dla wszystkich konfliktów (mapowane na blok try jednej aktualizacji nie powiodło się), łącznie z dostępem do <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> kolekcji. Każdy konflikt składowej jest mapowany na jeden element członkowski w aktualizacji, który uległ awarii sprawdzania współbieżności.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykładowe obu wartości.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
