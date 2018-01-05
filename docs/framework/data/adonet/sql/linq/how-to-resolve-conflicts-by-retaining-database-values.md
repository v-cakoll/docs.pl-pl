---
title: "Porady: Rozwiązywanie konfliktów, zachowując wartości bazy danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1271d7b287dacdae0dd46f084ba21d0dc901bd49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
