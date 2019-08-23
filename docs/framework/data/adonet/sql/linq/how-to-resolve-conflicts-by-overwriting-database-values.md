---
title: 'Instrukcje: Rozwiązywanie konfliktów z zastąpieniem wartości bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: f6721234d2d3920343bc72889c7683fb6ee662a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928759"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a>Instrukcje: Rozwiązywanie konfliktów z zastąpieniem wartości bazy danych
Aby uzgodnić różnice między oczekiwanymi i rzeczywistymi wartościami bazy danych przed próbą ponownego przesłania zmian, można użyć <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> do zastępowania wartości bazy danych. Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
> We wszystkich przypadkach rekord na kliencie jest najpierw odświeżany przez pobranie zaktualizowanych danych z bazy danych. Ta akcja zapewnia, że kolejna próba aktualizacji nie powiedzie się na tych samych kontrolach współbieżności.  
  
## <a name="example"></a>Przykład  
 W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek jest zgłaszany, gdy Użytkownik1 próbuje przesłać zmiany, ponieważ w międzyczasie została zmieniona kolumna asystenta i działu. W poniższej tabeli przedstawiono sytuację.  
  
||maszyny wirtualnej|Pomocnik|Dział|  
|------|-------------|---------------|----------------|  
|Oryginalny stan bazy danych podczas wykonywania zapytania przez Użytkownik1 i.|Alfreds|Maria|Sprzedaż|  
|Użytkownik1 przygotowuje się do przesłania tych zmian.|Alfred||Marketing|  
|Do tego celu zostały już przesłane te zmiany.||Anna|Usługa|  
  
 Użytkownik1 decyduje się rozwiązać ten konflikt przez zastąpienie wartości bazy danych bieżącymi wartościami członków klienta.  
  
 Gdy Użytkownik1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, wynik w bazie danych jest jak w poniższej tabeli:  
  
||maszyny wirtualnej|Pomocnik|Dział|  
|------|-------------|---------------|----------------|  
|Nowy stan po rozwiązaniu konfliktu.|Alfred<br /><br /> (od Użytkownik1)|Maria<br /><br /> oryginalnego|Marketing<br /><br /> (od Użytkownik1)|  
  
 Poniższy przykładowy kod pokazuje, jak zastąpić wartości bazy danych z bieżącymi wartościami członków klienta. (Żadna Inspekcja lub Niestandardowa obsługa konfliktów poszczególnych członków nie występuje).  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
