---
title: 'Optymistyczna współbieżność: Omówienie'
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: fa7d423c0abc07e0d97f7d0d4d557aa11d675ee4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792925"
---
# <a name="optimistic-concurrency-overview"></a>Optymistyczna współbieżność: Omówienie
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje optymistyczną kontrolę współbieżności. W poniższej tabeli opisano terminy, które dotyczą optymistycznej współbieżności [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] w dokumentacji:  
  
|Odsetk|Opis|  
|-----------|-----------------|  
|współbieżność|Sytuacja, w której co najmniej dwóch użytkowników w tym samym czasie próbuje zaktualizować ten sam wiersz bazy danych.|  
|konflikt współbieżności|Sytuacja, w której dwóch lub więcej użytkowników w tym samym czasie próbuje przesłać wartości powodujące konflikt do jednej lub kilku kolumn w wierszu.|  
|formant współbieżności|Technika służąca do rozwiązywania konfliktów współbieżności.|  
|Optymistyczna kontrola współbieżności|Technika, która najpierw sprawdza, czy inne transakcje zmieniły wartości w wierszu przed umożliwieniem przesłania zmian.<br /><br /> Różni się od *pesymistycznej kontroli współbieżności*, która blokuje rekord, aby uniknąć konfliktów współbieżności.<br /><br /> Kontrola *optymistyczna* jest w ten sposób uznawana, ponieważ uwzględnia szanse jednej transakcji zakłócające, że jest to mało prawdopodobne.|  
|Rozwiązywanie konfliktów|Proces odświeżania elementu powodującego konflikt przez ponowne wykonywanie zapytania względem bazy danych, a następnie Uzgadnianie różnic.<br /><br /> Po odświeżeniu obiektu narzędzie do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] śledzenia zmian zawiera następujące dane:<br /><br /> — Wartości początkowo pobrane z bazy danych i używane do sprawdzania aktualizacji.<br />— Nowe wartości bazy danych z kolejnego zapytania.<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]następnie decyduje o tym, czy obiekt jest w konflikcie (czyli czy co najmniej jedna jego wartość członkowska została zmieniona). Jeśli obiekt jest w konflikcie, następnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] należy określić, który z jego elementów członkowskich jest w konflikcie.<br /><br /> Wszelkie konflikty elementów [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Członkowskich, które są odnajdywane, zostaną dodane do listy konfliktów.|  
  
 W modelu obiektów występuje *konflikt optymistycznej współbieżności* , gdy spełniony jest oba z następujących warunków: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
- Klient próbuje przesłać zmiany do bazy danych.  
  
- Co najmniej jedna wartość sprawdzania aktualizacji została zaktualizowana w bazie danych od czasu ostatniego odczytu przez klienta.  
  
 Rozwiązanie tego konfliktu obejmuje odnajdywanie, które elementy członkowskie obiektu są w konflikcie, a następnie decydowanie o tym, co chcesz zrobić.  
  
> [!NOTE]
> Tylko członkowie zamapowane <xref:System.Data.Linq.Mapping.UpdateCheck.Always> jako <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> lub uczestniczą w sprawdzaniu współbieżności optymistycznej. Nie jest wykonywane żadne sprawdzenie dla elementów <xref:System.Data.Linq.Mapping.UpdateCheck.Never>członkowskich oznaczonych. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## <a name="example"></a>Przykład  
 Na przykład w poniższym scenariuszu Użytkownik1 rozpocznie się przygotowywanie aktualizacji przez przeszukiwanie wiersza w bazie danych. Użytkownik1 odbiera wiersz o wartościach Alfreds, Maria i Sales.  
  
 Użytkownik1 chce zmienić wartość kolumny Manager na Alfred i wartość kolumny działu na marketing. Zanim Użytkownik1 będzie mógł przesłać te zmiany, nastąpiło przesłanie zmian do bazy danych. W związku z tym teraz wartość kolumny asystenta została zmieniona na Mary i wartość kolumny dział na usługa.  
  
 Gdy Użytkownik1 podejmie teraz próbę przesłania zmian, przesłanie nie powiedzie się i <xref:System.Data.Linq.ChangeConflictException> zostanie zgłoszony wyjątek. Ten wynik występuje, ponieważ wartości bazy danych dla kolumny asystenta i działu nie są oczekiwane. Elementy członkowskie reprezentujące kolumny asystenta i działu są w konflikcie. Poniższa tabela zawiera podsumowanie sytuacji.  
  
||maszyny wirtualnej|Pomocnik|Dział|  
|------|-------------|---------------|----------------|  
|Stan pierwotny|Alfreds|Maria|Sprzedaż|  
|Użytkownik1|Alfred||Marketing|  
|Użytkownik2||Anna|Usługa|  
  
 Można rozwiązać konflikty, takie jak na różne sposoby. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie konfliktami](how-to-manage-change-conflicts.md)zmian.  
  
## <a name="conflict-detection-and-resolution-checklist"></a>Lista kontrolna wykrywania i rozwiązywania konfliktów  
 Możesz wykrywać i rozwiązywać konflikty na dowolnym poziomie szczegółowości. Z jednej najwyższej klasy można rozwiązać wszystkie konflikty na jeden z trzech sposobów (zobacz <xref:System.Data.Linq.RefreshMode>) bez dodatkowych zagadnień. Z drugiej najwyższej klasy można wyznaczyć określoną akcję dla każdego typu konfliktu dla każdego elementu członkowskiego powodującego konflikt.  
  
- Określ lub skoryguj <xref:System.Data.Linq.Mapping.UpdateCheck> opcje w modelu obiektów.  
  
     Aby uzyskać więcej informacji, zobacz [jak: Określ, które elementy członkowskie są testowane pod](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)kątem konfliktów współbieżności.  
  
- W bloku try/catch wywołania do <xref:System.Data.Linq.DataContext.SubmitChanges%2A>Określ, w którym punkcie mają być zgłaszane wyjątki.  
  
     Aby uzyskać więcej informacji, zobacz [jak: Określ, kiedy są zgłaszane](how-to-specify-when-concurrency-exceptions-are-thrown.md)wyjątki współbieżności.  
  
- Określ, ile szczegółów konfliktów chcesz pobrać, i odpowiednio Dołącz kod w bloku try/catch.  
  
     Aby uzyskać więcej informacji, zobacz [jak: Pobierz informacje o](how-to-retrieve-entity-conflict-information.md) konflikcie jednostki [i instrukcje: Pobierz informacje o](how-to-retrieve-member-conflict-information.md)konflikcie elementu członkowskiego.  
  
- Uwzględnij w `try` /kodziesposób, wjakichceszrozwiązaćróżneodnajdywanekonflikty.`catch`  
  
     Aby uzyskać więcej informacji, zobacz [jak: Rozwiązywanie konfliktów przez zachowywanie wartości](how-to-resolve-conflicts-by-retaining-database-values.md)bazy [danych, jak: Rozwiąż konflikty, zastępując wartości](how-to-resolve-conflicts-by-overwriting-database-values.md)bazy danych i [instrukcje: Rozwiązywanie konfliktów przez scalanie z](how-to-resolve-conflicts-by-merging-with-database-values.md)wartościami bazy danych.  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>Typy LINQ to SQL obsługujące wykrywanie i rozwiązywanie konfliktów  
 Klasy i funkcje do obsługi rozwiązywania konfliktów w optymistycznej współbieżności w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] programie obejmują następujące elementy:  
  
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

- [Instrukcje: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md)
