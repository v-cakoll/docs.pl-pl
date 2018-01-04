---
title: "Porady: Rozwiązywanie konfliktów przez scalanie z wartościami bazy danych"
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
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ee1016a6dc20e58bfafc434617a36f8f8703a3bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>Porady: Rozwiązywanie konfliktów przez scalanie z wartościami bazy danych
Uzgadnianie różnic pomiędzy wartościami oczekiwanymi i rzeczywistymi bazy danych, aby spróbować ponownie przesłać zmiany, umożliwia <xref:System.Data.Linq.RefreshMode.KeepChanges> do scalenia wartościami bazy danych z bieżącej wartości elementu członkowskiego klienta. Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  We wszystkich przypadkach rekord klienta jest najpierw odświeżyć pobierając zaktualizowane dane z bazy danych. Ta akcja gwarantuje, że następnej próbie aktualizacji zakończy się niepowodzeniem na tym samym kontrolach współbieżności.  
  
## <a name="example"></a>Przykład  
 W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek próba Użytkownik1 przesyłanie zmian, ponieważ Użytkownik2 w tym samym czasie została zmieniona kolumny Asystenta i działu. W poniższej tabeli przedstawiono tę sytuację.  
  
||Menedżer|Asystent|Dział|  
|------|-------------|---------------|----------------|  
|Oryginalny stan bazy danych po otrzymaniu kwerendy od użytkownika Użytkownik1 i Użytkownik2.|Alfreds|Maria|Sprzedaży|  
|Użytkownik1 przygotowuje się do przesyłania tych zmian.|Alfred||Marketing|  
|UŻYTKOWNIK2 zostało już przesłane tych zmian.||Joanna|Usługa|  
  
 Użytkownik1 decyduje o tym rozwiązać ten konflikt przez scalenie wartościami bazy danych z bieżącej wartości elementu członkowskiego klienta. Wynik będzie tej bazy danych, które wartości są zastępowane tylko wtedy, gdy bieżący zestaw zmian zmodyfikował również tej wartości.  
  
 Gdy Użytkownik1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.KeepChanges>, wynik w bazie danych jest w następującej tabeli:  
  
||Menedżer|Asystent|Dział|  
|------|-------------|---------------|----------------|  
|Nowy stan po rozwiązywania konfliktów.|Alfred<br /><br /> (z poziomu konta użytkownik1)|Joanna<br /><br /> (z Użytkownik2)|Marketing<br /><br /> (z poziomu konta użytkownik1)|  
  
 Poniższy przykład przedstawia sposób scalania wartościami bazy danych z bieżącej wartości elementu członkowskiego klienta (chyba że klient został zmieniony tej wartości). Występuje, nie inspekcji lub niestandardową obsługę konfliktów poszczególnych elementów członkowskich.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Rozwiązywanie konfliktów, zastępując wartości bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 [Instrukcje: Rozwiązywanie konfliktów, zachowując wartości bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
