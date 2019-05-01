---
title: 'Instrukcje: Rozwiązywanie konfliktów ze scaleniem wartości bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: 429bca7501bd58440ee894345855141a2a2ed12c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033712"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>Instrukcje: Rozwiązywanie konfliktów ze scaleniem wartości bazy danych
Aby uzgodnić różnice między wartościami oczekiwanymi i rzeczywistymi bazy danych, zanim spróbujesz ponownie prześlij zmiany, możesz użyć <xref:System.Data.Linq.RefreshMode.KeepChanges> scalić wartości bazy danych przy użyciu bieżących wartości elementu członkowskiego klienta. Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  We wszystkich przypadkach rekordu na komputerze klienckim najpierw są odświeżane poprzez pobranie zaktualizowanych danych z bazy danych. Ta akcja gwarantuje, że następnej próbie aktualizacji zakończy się niepowodzeniem na tych samych kontroli współbieżności.  
  
## <a name="example"></a>Przykład  
 W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek jest zgłaszany, gdy użytkownik User1 próbuje przesłać zmiany, ponieważ użytkownik2, w tym samym czasie została zmieniona kolumny Asystenta ustawień i działu. W poniższej tabeli przedstawiono tę sytuację.  
  
||maszyny wirtualnej|Asystenta ustawień|Dział|  
|------|-------------|---------------|----------------|  
|Oryginalny stan bazy danych po otrzymaniu kwerendy od użytkownika Użytkownik1 i Użytkownik2.|Alfreds|Maria|Sprzedaż|  
|Użytkownik1 przygotowuje się do przesyłania tych zmian.|Alfred||Marketing|  
|UŻYTKOWNIK2 zostało już przesłane te zmiany.||Mary|Usługa|  
  
 Aby rozwiązać ten konflikt, scalając wartości bazy danych przy użyciu bieżących wartości elementu członkowskiego klient decyduje o User1. Wynik będzie tej bazy danych, których wartości są zastępowane, tylko wtedy, gdy bieżący zestaw zmian zmodyfikował również tej wartości.  
  
 Gdy użytkownik User1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.KeepChanges>, wynik w bazie danych jest tak jak w poniższej tabeli:  
  
||maszyny wirtualnej|Asystenta ustawień|Dział|  
|------|-------------|---------------|----------------|  
|Nowy stan po rozwiązywania konfliktów.|Alfred<br /><br /> (od użytkownika Użytkownik1)|Mary<br /><br /> (od Użytkownik2)|Marketing<br /><br /> (od użytkownika Użytkownik1)|  
  
 Poniższy przykład pokazuje, jak można scalić wartości bazy danych przy użyciu bieżących wartości elementu członkowskiego klienta (chyba że klient został zmieniony tej wartości). Występuje, nie inspekcji lub niestandardową obsługę konflikty poszczególnych elementów członkowskich.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Rozwiązywanie konfliktów, zastępując wartości bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)
- [Instrukcje: Rozwiązywanie konfliktów, zachowując wartości bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)
- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
