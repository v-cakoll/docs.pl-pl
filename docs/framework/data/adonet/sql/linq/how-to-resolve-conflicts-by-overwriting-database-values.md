---
title: "Porady: Rozwiązywanie konfliktów, zastępując wartości bazy danych"
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
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1cb128020964955937aae3d9e477a600085d4cdb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a>Porady: Rozwiązywanie konfliktów, zastępując wartości bazy danych
Uzgadnianie różnic pomiędzy wartościami oczekiwanymi i rzeczywistymi bazy danych, aby spróbować ponownie przesłać zmiany, umożliwia <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> zastąpić wartościami bazy danych. Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  We wszystkich przypadkach rekord klienta jest najpierw odświeżyć pobierając zaktualizowane dane z bazy danych. Ta akcja gwarantuje, że następnej próbie aktualizacji zakończy się niepowodzeniem na tym samym kontrolach współbieżności.  
  
## <a name="example"></a>Przykład  
 W tym scenariuszu <xref:System.Data.Linq.ChangeConflictException> wyjątek próba Użytkownik1 przesyłanie zmian, ponieważ Użytkownik2 w tym samym czasie została zmieniona kolumny Asystenta i działu. W poniższej tabeli przedstawiono tę sytuację.  
  
||Menedżer|Asystent|Dział|  
|------|-------------|---------------|----------------|  
|Oryginalny stan bazy danych po otrzymaniu kwerendy od użytkownika Użytkownik1 i Użytkownik2.|Alfreds|Maria|Sprzedaży|  
|Użytkownik1 przygotowuje się do przesyłania tych zmian.|Alfred||Marketing|  
|UŻYTKOWNIK2 zostało już przesłane tych zmian.||Joanna|Usługa|  
  
 Użytkownik1 decyduje o tym rozwiązać ten konflikt, zastępując wartości bazy danych z bieżącej wartości elementu członkowskiego klienta.  
  
 Gdy Użytkownik1 rozwiązuje konflikt przy użyciu <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, wynik w bazie danych jest w następującej tabeli:  
  
||Menedżer|Asystent|Dział|  
|------|-------------|---------------|----------------|  
|Nowy stan po rozwiązywania konfliktów.|Alfred<br /><br /> (z poziomu konta użytkownik1)|Maria<br /><br /> (oryginalny)|Marketing<br /><br /> (z poziomu konta użytkownik1)|  
  
 Poniższy przykład kodu pokazuje, jak zastąpić wartościami bazy danych z bieżącej wartości elementu członkowskiego klienta. (Nie inspekcji lub niestandardową obsługę wystąpił konflikt elementu członkowskiego poszczególnych występuje.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Zarządzanie konfliktów zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
