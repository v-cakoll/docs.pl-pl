---
title: "Optymistycznej współbieżności: omówienie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 52e83f443c0ae74587b4585beb51ddbeb093486a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="optimistic-concurrency-overview"></a>Optymistycznej współbieżności: omówienie
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje optymistyczne sterowanie współbieżnością. W poniższej tabeli opisano terminy, które dotyczą optymistycznej współbieżności w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentacji:  
  
|Warunki|Opis|  
|-----------|-----------------|  
|współbieżność|Sytuację, w którym dwóch lub więcej użytkowników jednocześnie spróbuj zaktualizować tego samego wiersza bazy danych.|  
|konflikt współbieżności|Sytuacja dwóch lub więcej użytkowników jednocześnie spróbuj przesłać wartości powodujące konflikt do jednej lub kilku kolumn w wierszu.|  
|formant współbieżności|Technika, używany do rozwiązywania konfliktów współbieżności.|  
|optymistyczne sterowanie współbieżnością|Tę metodę, która najpierw sprawdza, czy inne transakcje zostały zmienione wartości w wierszu przed umożliwiający zmiany do przesłania.<br /><br /> Natomiast z *sterowania współbieżnością pesymistyczne*, która blokuje rekord, aby zapobiec konfliktom współbieżności.<br /><br /> *Optymistyczne* kontroli tak jest określona, ponieważ traktuje szanse jedna transakcja konfliktu z inną za mało prawdopodobne.|  
|Rozwiązywanie konfliktów|Proces odświeżania powodującego konflikt elementu ponownie zapytanie bazy danych, a następnie Uzgadnianie różnic.<br /><br /> Po odświeżeniu obiektu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] śledzący zmiany zawiera następujące dane:<br /><br /> -Sprawdź wartości pierwotnie pobrane z bazy danych i używany do aktualizacji.<br />-Nowej bazy danych wartości w kolejnych zapytania.<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Określa, czy obiekt jest w konflikcie (to znaczy czy co najmniej jedna z wartości jego elementów członkowskich uległa zmianie). Jeśli obiekt jest w konflikcie, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obok Określa, które z jego elementów członkowskich są w konflikcie.<br /><br /> Każdy członek konfliktu, który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] odnajduje zostanie dodany do listy konfliktów.|  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] model obiektów *konflikt optymistycznej współbieżności* występuje, gdy są spełnione oba poniższe warunki:  
  
-   Klient próbuje przesłać zmiany w bazie danych.  
  
-   Co najmniej jedna wartość sprawdzenie dostępności aktualizacji zostały zaktualizowane w bazie danych od czasu ich odczytu ostatnio klienta.  
  
 Rozwiązanie tego konfliktu obejmuje wykrywania, które elementy członkowskie obiektu są w konflikcie, a następnie podejmowaniu decyzji co chcesz zrobić informacji na ten temat.  
  
> [!NOTE]
>  Tylko elementy członkowskie <xref:System.Data.Linq.Mapping.UpdateCheck.Always> lub <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> uczestniczyć w kontroli optymistycznej współbieżności. Nie jest sprawdzane dla elementy członkowskie oznaczone <xref:System.Data.Linq.Mapping.UpdateCheck.Never>. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## <a name="example"></a>Przykład  
 Na przykład w poniższym scenariuszu Użytkownik1 rozpoczyna przygotowania aktualizacji przez zapytanie bazy danych dla wiersza. Użytkownik1 odbiera na wiersz z wartości Alfreds, Maria i sprzedaży.  
  
 Użytkownik1 chce zmienić wartość kolumny Menedżera Alfred i wartość kolumnę działu marketingu. Zanim Użytkownik1 może wysyłać te zmiany, Użytkownik2 przesłał zmiany w bazie danych. Wartość kolumny Asystenta zmieniono tak teraz Joanna i wartość kolumny działu do usługi.  
  
 Teraz Użytkownik1 próbuje przesłać zmian, przesyłania nie powiedzie się i <xref:System.Data.Linq.ChangeConflictException> wyjątku. Ten wynik występuje, ponieważ wartości bazy danych dla kolumny Asystenta i działu nie są te, które zostały wprowadzone. Członkowie reprezentujący kolumn i działu Asystenta są w konflikcie. W poniższej tabeli przedstawiono tę sytuację.  
  
||Menedżer|Asystent|Dział|  
|------|-------------|---------------|----------------|  
|Oryginalny stan|Alfreds|Maria|Sprzedaży|  
|Użytkownik1|Alfred||Marketing|  
|UŻYTKOWNIK2||Joanna|Usługa|  
  
 Na różne sposoby, można rozwiązać konflikty, takich jak ta. Aby uzyskać więcej informacji, zobacz [porady: Zarządzanie konfliktów zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="conflict-detection-and-resolution-checklist"></a>Wykrywanie konfliktów i listę kontrolną rozwiązania  
 Mogą wykrywać i rozwiązywania konfliktów na dowolnym poziomie szczegółowości. W jednym extreme można rozwiązać wszystkie konflikty w jeden z trzech sposobów (zobacz <xref:System.Data.Linq.RefreshMode>) bez dodatkowego rozważenia. Y. Możesz określić konkretną akcję dla każdego typu konfliktów na każdy element członkowski, powoduje konflikt.  
  
-   Określ lub Popraw <xref:System.Data.Linq.Mapping.UpdateCheck> opcje w modelu obiektu.  
  
     Aby uzyskać więcej informacji, zobacz [porady: Określ, które elementy członkowskie są sprawdzane pod kątem konfliktom współbieżności](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
-   W bloku try/catch wywołania do <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, określić, w jakim punkcie wyjątki zostanie wygenerowany.  
  
     Aby uzyskać więcej informacji, zobacz [porady: Określ podczas współbieżności wyjątki są zgłaszane](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
-   Określić, ile szczegółów konflikt, które ma zostać pobrane i odpowiednio zawiera kod w Twojej bloku try/catch.  
  
     Aby uzyskać więcej informacji, zobacz [jak: pobrać informacje o konfliktach jednostki](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md) i [porady: pobieranie informacji konflikt elementu członkowskiego](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md).  
  
-   Uwzględnione w Twojej `try` / `catch` kodu, w jaki chcesz rozwiązać konflikty różnych odnajdywania.  
  
     Aby uzyskać więcej informacji, zobacz [jak: rozwiązać konflikty przy zachowaniu wartościami bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md), [porady: Rozwiązywanie konfliktów przez zastąpienie wartości bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md), i [porady: Rozwiązywanie konfliktów przez scalanie z bazy danych wartości](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md).  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>LINQ do SQL typów, które obsługują wykrywania konfliktów i rozwiązania  
 Klasy i funkcje do obsługi rozpoznawania konfliktów w optymistycznej współbieżności w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] są następujące:  
  
-   <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Zarządzanie konfliktów zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
