---
title: 'Instrukcje: Rozwiązywanie konfliktów z zachowaniem wartości bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: e42f48a188741c3ddff44f6444fa351192c8175f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793338"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a>Instrukcje: Rozwiązywanie konfliktów z zachowaniem wartości bazy danych
Aby uzgodnić różnice między oczekiwanymi i rzeczywistymi wartościami bazy danych przed próbą ponownego przesłania zmian, można użyć <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> programu w celu zachowania wartości znalezionych w bazie danych. Bieżące wartości w modelu obiektów są następnie zastępowane. Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](optimistic-concurrency-overview.md).  
  
> [!NOTE]
> We wszystkich przypadkach rekord na kliencie jest najpierw odświeżany przez pobranie zaktualizowanych danych z bazy danych. Ta akcja zapewnia, że kolejna próba aktualizacji nie powiedzie się na tych samych kontrolach współbieżności.  
  
## <a name="example"></a>Przykład  
 W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek jest zgłaszany, gdy Użytkownik1 próbuje przesłać zmiany, ponieważ w międzyczasie została zmieniona kolumna asystenta i działu. W poniższej tabeli przedstawiono sytuację.  
  
||maszyny wirtualnej|Pomocnik|Dział|  
|------|-------------|---------------|----------------|  
|Oryginalny stan bazy danych podczas wykonywania zapytania przez Użytkownik1 i.|Alfreds|Maria|Sprzedaż|  
|Użytkownik1 przygotowuje się do przesłania tych zmian.|Alfred||Marketing|  
|Do tego celu zostały już przesłane te zmiany.||Anna|Usługa|  
  
 Użytkownik1 decyduje się rozwiązać ten konflikt, mając nowsze wartości bazy danych zastępują bieżące wartości w modelu obiektów.  
  
 Gdy Użytkownik1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, wynik w bazie danych jest następujący w tabeli:  
  
||maszyny wirtualnej|Pomocnik|Dział|  
|------|-------------|---------------|----------------|  
|Nowy stan po rozwiązaniu konfliktu.|Alfreds<br /><br /> oryginalnego|Anna<br /><br /> (od b do)|Usługa<br /><br /> (od b do)|  
  
 Poniższy przykładowy kod pokazuje, jak zastąpić bieżące wartości w modelu obiektów wartościami bazy danych. (Żadna Inspekcja lub Niestandardowa obsługa konfliktów poszczególnych członków nie występuje).  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md)
