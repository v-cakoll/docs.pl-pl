---
title: 'Porady: Określanie, kiedy są zgłaszane wyjątki współbieżności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: 6890cc130f4f4101c02bb88c5f5666bcd5cf9b98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a>Porady: Określanie, kiedy są zgłaszane wyjątki współbieżności
W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.ChangeConflictException> jest zgłaszany wyjątek, jeśli obiekty nie będą aktualizowane z powodu konfliktów optymistycznej współbieżności. Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Przed przesłaniem zmiany do bazy danych, można określić podczas wyjątków współbieżności powinien zostać zgłoszony:  
  
-   Zgłoszenie wyjątku w pierwszym niepowodzeniu (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).  
  
-   Zakończ wszystkie próby aktualizacji, accumulate wszystkie błędy oraz tworzenie raportów narastająco błędy w wyjątek (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).  
  
 Gdy zgłoszone, <xref:System.Data.Linq.ChangeConflictException> wyjątek zapewnia dostęp do <xref:System.Data.Linq.ChangeConflictCollection> kolekcji. Ta kolekcja zawiera szczegółowe informacje dla wszystkich konfliktów (przypisane do bloku try jednej aktualizacji nie powiodło się), łącznie z dostępem do <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> kolekcji. Każdy element członkowski konflikt mapuje do jednego elementu członkowskiego w aktualizacji nie powiodło się sprawdzanie współbieżności.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykłady obu wartości.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
