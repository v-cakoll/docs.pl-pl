---
title: 'Instrukcje: Rozwiązywanie konfliktów, zachowując wartości bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: f647dad951acfbc309257212018db32e655169df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531268"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a>Instrukcje: Rozwiązywanie konfliktów, zachowując wartości bazy danych
Aby uzgodnić różnice między wartościami oczekiwanymi i rzeczywistymi bazy danych, zanim spróbujesz ponownie prześlij zmiany, możesz użyć <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> do przechowywania wartości znajdujących się w bazie danych. Bieżące wartości w modelu obiektów następnie zostaną zastąpione. Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  We wszystkich przypadkach rekordu na komputerze klienckim najpierw są odświeżane poprzez pobranie zaktualizowanych danych z bazy danych. Ta akcja gwarantuje, że następnej próbie aktualizacji zakończy się niepowodzeniem na tych samych kontroli współbieżności.  
  
## <a name="example"></a>Przykład  
 W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek jest zgłaszany, gdy użytkownik User1 próbuje przesłać zmiany, ponieważ użytkownik2, w tym samym czasie została zmieniona kolumny Asystenta ustawień i działu. W poniższej tabeli przedstawiono tę sytuację.  
  
||maszyny wirtualnej|Asystenta ustawień|Dział|  
|------|-------------|---------------|----------------|  
|Oryginalny stan bazy danych po otrzymaniu kwerendy od użytkownika Użytkownik1 i Użytkownik2.|Alfreds|Maria|Sprzedaż|  
|Użytkownik1 przygotowuje się do przesyłania tych zmian.|Alfred||Marketing|  
|UŻYTKOWNIK2 zostało już przesłane te zmiany.||Mary|Usługa|  
  
 Użytkownik1 decyduje rozwiązać ten konflikt przez nowszą wartości z bazy danych, zastąpienie bieżących wartości w modelu obiektów.  
  
 Gdy użytkownik User1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, wynik w bazie danych jest w następujący sposób w tabeli:  
  
||maszyny wirtualnej|Asystenta ustawień|Dział|  
|------|-------------|---------------|----------------|  
|Nowy stan po rozwiązywania konfliktów.|Alfreds<br /><br /> (oryginalny)|Mary<br /><br /> (od Użytkownik2)|Usługa<br /><br /> (od Użytkownik2)|  
  
 Poniższy przykład kodu pokazuje, jak zastąpić bieżące wartości w modelu obiektów z wartościami bazy danych. (Nie inspekcji lub niestandardową obsługę konflikty poszczególnym członkom występuje.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
