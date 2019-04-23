---
title: 'Instrukcje: Rozwiązywanie konfliktów z zastąpieniem wartości bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 7b8d7cf8ab2335c064062ed3ab4072d81e8042fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189121"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a>Instrukcje: Rozwiązywanie konfliktów z zastąpieniem wartości bazy danych
Aby uzgodnić różnice między wartościami oczekiwanymi i rzeczywistymi bazy danych, zanim spróbujesz ponownie prześlij zmiany, możesz użyć <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> zastąpić wartości bazy danych. Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  We wszystkich przypadkach rekordu na komputerze klienckim najpierw są odświeżane poprzez pobranie zaktualizowanych danych z bazy danych. Ta akcja gwarantuje, że następnej próbie aktualizacji zakończy się niepowodzeniem na tych samych kontroli współbieżności.  
  
## <a name="example"></a>Przykład  
 W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek jest zgłaszany, gdy użytkownik User1 próbuje przesłać zmiany, ponieważ użytkownik2, w tym samym czasie została zmieniona kolumny Asystenta ustawień i działu. W poniższej tabeli przedstawiono tę sytuację.  
  
||maszyny wirtualnej|Asystenta ustawień|Dział|  
|------|-------------|---------------|----------------|  
|Oryginalny stan bazy danych po otrzymaniu kwerendy od użytkownika Użytkownik1 i Użytkownik2.|Alfreds|Maria|Sprzedaż|  
|Użytkownik1 przygotowuje się do przesyłania tych zmian.|Alfred||Marketing|  
|UŻYTKOWNIK2 zostało już przesłane te zmiany.||Mary|Usługa|  
  
 Aby rozwiązać ten konflikt, zastępując wartości bazy danych przy użyciu bieżących wartości elementu członkowskiego klient decyduje o User1.  
  
 Gdy użytkownik User1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, wynik w bazie danych jest tak jak w poniższej tabeli:  
  
||maszyny wirtualnej|Asystenta ustawień|Dział|  
|------|-------------|---------------|----------------|  
|Nowy stan po rozwiązywania konfliktów.|Alfred<br /><br /> (od użytkownika Użytkownik1)|Maria<br /><br /> (oryginalny)|Marketing<br /><br /> (od użytkownika Użytkownik1)|  
  
 Poniższy przykład kodu pokazuje, jak zastąpić wartości bazy danych przy użyciu bieżących wartości elementu członkowskiego klienta. (Nie inspekcji lub niestandardową obsługę konflikty poszczególnym członkom występuje.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
