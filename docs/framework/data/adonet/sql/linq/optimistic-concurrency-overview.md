---
title: 'Optymistyczna współbieżność: Omówienie'
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: a6e654ea1ae199cb086e9377454d05e6eaa03ad6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609966"
---
# <a name="optimistic-concurrency-overview"></a>Optymistyczna współbieżność: Omówienie
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje mechanizmu kontroli optymistycznej współbieżności. W poniższej tabeli opisano terminy, które dotyczą optymistycznej współbieżności w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentacji:  
  
|Warunki|Opis|  
|-----------|-----------------|  
|współbieżność|Sytuacja, w którym dwóch lub większej liczby użytkowników, w tym samym czasie próby zaktualizowania wiersza w tabeli o tej samej bazy danych.|  
|konflikt współbieżności|Sytuacja, w dwóch lub większej liczby użytkowników, w tym samym czasie spróbuj przesłać wartościami będącymi w konflikcie, na co najmniej jedna kolumna wiersza.|  
|formant współbieżności|Technika, używany do rozwiązywania konfliktów współbieżności.|  
|Mechanizmu kontroli optymistycznej współbieżności|Technika, która najpierw sprawdza, czy inne transakcje zostały zmienione wartości w wierszu przed pozwalające zmiany do przesłania.<br /><br /> Porównaj z *mechanizm kontroli pesymistycznej współbieżności*, która blokuje rekord w celu uniknięcia konfliktów współbieżności.<br /><br /> *Optymistyczna* kontroli więc jest określona, ponieważ uwzględniane szanse jedna transakcja nie zakłócają innej, aby być mało prawdopodobne.|  
|Rozwiązywanie konfliktów|Proces odświeżania powodującego konflikt elementu przez zapytanie do bazy danych ponownie, a następnie Uzgadnianie różnic.<br /><br /> Po odświeżeniu obiektu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] śledzenie zmian zawiera następujące dane:<br /><br /> — Sprawdź wartości pierwotnie pobrany z bazy danych i używany do aktualizacji.<br />-Nowej bazy danych wartości z kolejnych zapytań.<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] następnie ustala, czy obiekt jest w konflikcie, (oznacza to, czy co najmniej jeden z jego wartości składowych uległa zmianie). Jeśli obiekt jest w konflikcie, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obok Określa, które z jej elementów członkowskich są w konflikcie.<br /><br /> Konflikt dowolnego elementu członkowskiego, który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] odnajduje zostanie dodany do listy konfliktów.|  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelu obiektów *konflikt optymistycznej współbieżności* występuje, gdy są spełnione oba poniższe warunki:  
  
- Klient próbuje przesłać zmiany w bazie danych.  
  
- Co najmniej jednej wartości sprawdzania aktualizacji zostały zaktualizowane w bazie danych od klienta ostatniego odczytu je.  
  
 Rozwiązanie tego konfliktu zawiera odnajdywanie, które elementy członkowskie obiektu są w konflikcie, a następnie decydując, co chcesz zrobić na jego temat.  
  
> [!NOTE]
>  Tylko członkowie zamapowany jako <xref:System.Data.Linq.Mapping.UpdateCheck.Always> lub <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> uczestniczyć w kontroli optymistycznej współbieżności. Nie jest sprawdzane dla składowe oznaczone <xref:System.Data.Linq.Mapping.UpdateCheck.Never>. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## <a name="example"></a>Przykład  
 Na przykład w poniższym scenariuszu użytkownik User1 rozpoczyna się przygotować aktualizacji przy użyciu kwerend bazy danych na podstawie wiersza. Użytkownik1 odbiera wierszy z wartościami Alfreds, Maria i sprzedaż.  
  
 Użytkownik1 chce zmienić wartość kolumny Menedżera Alfred i wartość kolumnę działu marketingu. Zanim użytkownik User1 mogą przesyłać tych zmian, Użytkownik2 zostało przesłane zmiany w bazie danych. Teraz Joanna i wartość kolumny działu do usługi zmieniono wartość kolumny Asystenta ustawień.  
  
 Teraz Użytkownik1 próbuje przesłać zmiany, przesyłanie nie powiedzie się i <xref:System.Data.Linq.ChangeConflictException> wyjątku. Dzieje się tak, ponieważ wartości bazy danych dla kolumny Asystenta ustawień i działu nie te, które były one oczekiwane. Członkowie reprezentujący kolumny Asystenta ustawień i działu są w konflikcie. W poniższej tabeli przedstawiono tę sytuację.  
  
||maszyny wirtualnej|Asystenta ustawień|Dział|  
|------|-------------|---------------|----------------|  
|Oryginalny stan|Alfreds|Maria|Sprzedaż|  
|User1|Alfred||Marketing|  
|User2||Mary|Usługa|  
  
 Można rozwiązać konflikty takich na różne sposoby. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="conflict-detection-and-resolution-checklist"></a>Wykrywanie konfliktów i listę kontrolną rozwiązania  
 Można wykrywać i rozwiązywać konflikty na dowolnym poziomie szczegółowości. W skrajnej jeden, można rozwiązać wszystkie konflikty w jeden z trzech sposobów (zobacz <xref:System.Data.Linq.RefreshMode>) bez dodatkowego rozważenia. Y. można wyznaczyć określoną akcję dla każdego typu konfliktu na każdy element członkowski w konflikcie.  
  
- Określ lub Popraw <xref:System.Data.Linq.Mapping.UpdateCheck> opcje w modelu obiektu.  
  
     Aby uzyskać więcej informacji, zobacz [jak: Określ, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
- W bloku try/catch wywołania do <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, określić, w którym momencie wyjątki zostanie wygenerowany.  
  
     Aby uzyskać więcej informacji, zobacz [jak: Określ są zgłaszane wyjątki współbieżności podczas](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
- Określić ilość szczegółów konfliktu, które mają zostać pobrane i w związku z tym zawiera kod w swojej bloku try/catch.  
  
     Aby uzyskać więcej informacji, zobacz [jak: Pobieranie informacji o konflikcie jednostki](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md) i [jak: Pobieranie informacji o konflikcie elementu członkowskiego](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md).  
  
- Uwzględnić w swojej `try` / `catch` kodu, jak chcesz rozwiązać konflikty różnych odkryjesz.  
  
     Aby uzyskać więcej informacji, zobacz [jak: Rozwiązywanie konfliktów, zachowując wartości bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md), [jak: Rozwiązywanie konfliktów, zastępując wartości bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md), i [jak: Rozwiązywanie konfliktów, scalając wartości bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md).  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>LINQ do typów SQL, które obsługują wykrywania konfliktów i rozwiązania  
 Klasy i funkcje do obsługi Rozwiązywanie konfliktów w optymistycznej współbieżności w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obejmują następujące elementy:  
  
- <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
