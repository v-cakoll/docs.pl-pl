---
title: 'Porady: Rozwiązywanie konfliktów, zachowując wartości bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: d0d59c520beaab2d6c8c1594ee81a3eaecf1d03e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361698"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a>Porady: Rozwiązywanie konfliktów, zachowując wartości bazy danych
Uzgadnianie różnic pomiędzy wartościami oczekiwanymi i rzeczywistymi bazy danych, aby spróbować ponownie przesłać zmiany, umożliwia <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> do zachowania na wartości znajdujące się w bazie danych. Bieżące wartości w modelu obiektów następnie zostaną zastąpione. Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  We wszystkich przypadkach rekord klienta jest najpierw odświeżyć pobierając zaktualizowane dane z bazy danych. Ta akcja gwarantuje, że następnej próbie aktualizacji zakończy się niepowodzeniem na tym samym kontrolach współbieżności.  
  
## <a name="example"></a>Przykład  
 W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek próba Użytkownik1 przesyłanie zmian, ponieważ Użytkownik2 w tym samym czasie została zmieniona kolumny Asystenta i działu. W poniższej tabeli przedstawiono tę sytuację.  
  
||Menedżer|Asystent|Dział|  
|------|-------------|---------------|----------------|  
|Oryginalny stan bazy danych po otrzymaniu kwerendy od użytkownika Użytkownik1 i Użytkownik2.|Alfreds|Maria|Sprzedaży|  
|Użytkownik1 przygotowuje się do przesyłania tych zmian.|Alfred||Marketing|  
|UŻYTKOWNIK2 zostało już przesłane tych zmian.||Joanna|Usługa|  
  
 Użytkownik1 decyduje o tym rozwiązać ten konflikt przez nowszą wartościami bazy danych zastąpić bieżące wartości w modelu obiektów.  
  
 Gdy Użytkownik1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, wynik w bazie danych jest następujący w tabeli:  
  
||Menedżer|Asystent|Dział|  
|------|-------------|---------------|----------------|  
|Nowy stan po rozwiązywania konfliktów.|Alfreds<br /><br /> (oryginalny)|Joanna<br /><br /> (z Użytkownik2)|Usługa<br /><br /> (z Użytkownik2)|  
  
 Poniższy przykład kodu pokazuje, jak zastąpić bieżące wartości w modelu obiektów z wartościami bazy danych. (Nie inspekcji lub niestandardową obsługę wystąpił konflikt elementu członkowskiego poszczególnych występuje.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
