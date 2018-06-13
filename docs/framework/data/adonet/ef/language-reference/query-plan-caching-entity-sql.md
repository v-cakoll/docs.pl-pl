---
title: Plan zapytania buforowania (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 0e00d7f9382fca2af630a8e1d50a5cde5178da05
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762039"
---
# <a name="query-plan-caching-entity-sql"></a>Plan zapytania buforowania (jednostka SQL)
Zawsze, gdy podejmowana jest próba mógł wykonać zapytania, potoku zapytanie wyszukuje pamięci podręcznej planu zapytania Czy dokładne kwerendy jest już skompilowane i dostępne. Jeśli tak, używany jest buforowany plan zamiast tworzenia nowej. Jeśli dopasowanie nie zostanie znaleziony w pamięci podręcznej planu zapytania, zapytanie jest skompilowany i pamięci podręcznej. Zapytanie jest identyfikowany przez jego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tekstu i parametru kolekcji (nazwy i typy). Wszystkie porównywania tekstu jest rozróżniana wielkość liter.  
  
## <a name="configuration"></a>Konfiguracja  
 Buforowanie plan zapytania jest konfigurowany za pomocą <xref:System.Data.EntityClient.EntityCommand>.  
  
 Aby włączyć lub wyłączyć zapytania planu buforowanie za pośrednictwem <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, ustawić tę właściwość na `true` lub `false`. Wyłączenie buforowania planu dla poszczególnych zapytań dynamicznych, które prawdopodobnie nie można użyć więcej niż jeden raz — do poprawia wydajność.  
  
 Można włączyć zapytania planu buforowanie za pośrednictwem <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.  
  
## <a name="recommended-practice"></a>Zalecana praktyka  
 Zapytania dynamiczne należy unikać, ogólnie. W poniższym przykładzie zapytanie dynamicznej jest narażony na ataki, z powodu danych wejściowych użytkownika bezpośrednio, bez żadnych sprawdzania poprawności.  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 Jeśli używasz dynamicznie generowanym zapytania, rozważ wyłączenie buforowanie planu zapytania, aby uniknąć zużycie pamięci niepotrzebne wpisy w pamięci podręcznej, które prawdopodobnie nie zostanie ponownie.  
  
 Planu zapytania, buforowanie na zapytania statycznych i sparametryzowanych zapytań zapewniają korzyści wydajności. Poniżej przedstawiono przykład statyczne kwerendy:  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 Dla zapytania do dopasowania poprawnie przez pamięć podręczną planu zapytania one spełniać następujące wymagania:  
  
-   Tekst zapytania powinien być stałe wzorzec, najlepiej ciągiem stałym lub zasobu.  
  
-   <xref:System.Data.EntityClient.EntityParameter> lub <xref:System.Data.Objects.ObjectParameter> powinny być używane wszędzie tam, gdzie muszą być przekazywane wartości dostarczone przez użytkownika.  
  
 Należy unikać następujące wzorców zapytań, które niepotrzebnie zużywają miejsca w pamięci podręcznej planu zapytania:  
  
-   Zmiany do rozróżniania wielkości liter w tekście.  
  
-   Zmiany biały znak.  
  
-   Zmiany w wartości literału.  
  
-   Zmiany tekstu wewnątrz komentarzy.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
