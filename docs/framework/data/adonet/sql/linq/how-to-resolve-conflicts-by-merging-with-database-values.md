---
title: 'Instrukcje: Rozwiązywanie konfliktów ze scaleniem wartości bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: ccd2e37457e686bc5faed6d8979c2b266d05c829
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943434"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>Instrukcje: Rozwiązywanie konfliktów ze scaleniem wartości bazy danych
Aby uzgodnić różnice między oczekiwanymi i rzeczywistymi wartościami bazy danych przed próbą ponownego przesłania zmian, można użyć <xref:System.Data.Linq.RefreshMode.KeepChanges> programu do scalania wartości bazy danych z bieżącymi wartościami członków klienta. Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
> We wszystkich przypadkach rekord na kliencie jest najpierw odświeżany przez pobranie zaktualizowanych danych z bazy danych. Ta akcja zapewnia, że kolejna próba aktualizacji nie powiedzie się na tych samych kontrolach współbieżności.  
  
## <a name="example"></a>Przykład  
 W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek jest zgłaszany, gdy Użytkownik1 próbuje przesłać zmiany, ponieważ w międzyczasie została zmieniona kolumna asystenta i działu. W poniższej tabeli przedstawiono sytuację.  
  
||maszyny wirtualnej|Pomocnik|Dział|  
|------|-------------|---------------|----------------|  
|Oryginalny stan bazy danych podczas wykonywania zapytania przez Użytkownik1 i.|Alfreds|Maria|Sprzedaż|  
|Użytkownik1 przygotowuje się do przesłania tych zmian.|Alfred||Marketing|  
|Do tego celu zostały już przesłane te zmiany.||Anna|Usługa|  
  
 Użytkownik1 decyduje się rozwiązać ten konflikt przez scalenie wartości bazy danych z bieżącymi wartościami członków klienta. Wynikiem tego jest to, że wartości bazy danych są zastępowane tylko wtedy, gdy bieżąca Grupa zmian również zmodyfikował tę wartość.  
  
 Gdy Użytkownik1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.KeepChanges>, wynik w bazie danych jest jak w poniższej tabeli:  
  
||maszyny wirtualnej|Pomocnik|Dział|  
|------|-------------|---------------|----------------|  
|Nowy stan po rozwiązaniu konfliktu.|Alfred<br /><br /> (od Użytkownik1)|Anna<br /><br /> (od b do)|Marketing<br /><br /> (od Użytkownik1)|  
  
 Poniższy przykład pokazuje, jak scalić wartości bazy danych z bieżącymi wartościami członków klienta (chyba że klient również zmienił tę wartość). Nie występuje żadna Inspekcja ani Niestandardowa obsługa konfliktów poszczególnych członków.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Rozwiązywanie konfliktów przez zastępowanie wartości bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)
- [Instrukcje: Rozwiązywanie konfliktów przez zachowywanie wartości bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)
- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
