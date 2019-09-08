---
title: 'Instrukcje: Określanie, kiedy są zgłaszane wyjątki współbieżności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: c0f41d23264bbe5c9130cb5a0b03686331bc92b1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781621"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a>Instrukcje: Określanie, kiedy są zgłaszane wyjątki współbieżności
W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie <xref:System.Data.Linq.ChangeConflictException> wyjątek jest zgłaszany, gdy obiekty nie są aktualizowane z powodu nieoptymistycznych konfliktów współbieżności. Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](optimistic-concurrency-overview.md).  
  
 Przed przesłaniem zmian do bazy danych można określić, kiedy mają być zgłaszane wyjątki współbieżności:  
  
- Zgłoś wyjątek przy pierwszym błędzie (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).  
  
- Zakończ wszystkie próby aktualizacji, zakumulowanie wszystkich błędów i Zgłoś błędy skumulowane w wyjątku (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).  
  
 Gdy zostanie <xref:System.Data.Linq.ChangeConflictException> zgłoszony, wyjątek zapewnia dostęp <xref:System.Data.Linq.ChangeConflictCollection> do kolekcji. Ta kolekcja zawiera szczegółowe informacje dotyczące każdego konfliktu (zamapowane do pojedynczej nieudanej aktualizacji), w tym <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> dostęp do kolekcji. Konflikty każdego elementu członkowskiego są mapowane na pojedynczy element członkowski w aktualizacji, która nie mogła sprawdzić współbieżności.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykłady obu wartości.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md)
- [Tworzenie i przesyłanie zmian danych](making-and-submitting-data-changes.md)
