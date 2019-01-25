---
title: Planu zapytania z pamięci podręcznej (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 75c097d66ae23d32465b5a717ae627d35cdc003f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671138"
---
# <a name="query-plan-caching-entity-sql"></a>Planu zapytania z pamięci podręcznej (jednostka SQL)
Zawsze, gdy podejmowana jest próba, aby wykonać zapytanie, potok zapytanie wyszukuje pamięci podręcznej planu zapytania Czy dokładne zapytanie jest już skompilowane i dostępne. Jeśli tak, używa buforowanego planu zamiast tworzenia nowej. Jeśli dopasowanie nie zostanie znaleziony w pamięci podręcznej planu zapytania, kwerenda jest skompilowany i pamięci podręcznej. Zapytanie jest identyfikowane za pomocą jego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kolekcji tekstu i parametrów (nazw i typy). Wszystkie porównania tekstu jest rozróżniana wielkość liter.  
  
## <a name="configuration"></a>Konfiguracja  
 Buforowanie planu zapytania jest konfigurowane za pomocą <xref:System.Data.EntityClient.EntityCommand>.  
  
 Aby włączyć lub wyłączyć buforowanie planu zapytania za pomocą <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, ustaw tę właściwość na `true` lub `false`. Wyłączanie buforowanie planu dla poszczególnych zapytań dynamicznych, które prawdopodobnie celu można użyć więcej niż jeden raz poprawia wydajność.  
  
 Aby umożliwić buforowanie planu zapytania za pomocą <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.  
  
## <a name="recommended-practice"></a>Zalecana praktyka  
 Zapytania dynamiczne należy unikać, ogólnie rzecz biorąc. W poniższym przykładzie zapytanie dynamiczne jest narażony na ataki przez wstrzyknięcie kodu SQL, ponieważ zajmuje trochę danych wejściowych użytkownika bezpośrednio, bez żadnych sprawdzania poprawności.  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 Jeśli używasz dynamicznie generowanych zapytań, należy rozważyć wyłączenie, buforowanie planu zapytania w celu uniknięcia zużycie pamięci niepotrzebne dla wpisów pamięci podręcznej, które prawdopodobnie mogą być ponownie używane.  
  
 Plan zapytania w pamięci podręcznej zapytań statycznych i sparametryzowane zapytania może zapewnić korzyści wydajności. Oto przykład kwerendy statyczne:  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 Dla zapytań, które mają być dopasowywane prawidłowo o pamięci podręcznej planu zapytania mogą spełniać następujące wymagania:  
  
-   Tekst zapytania należy wzór stałej, najlepiej stałym ciągiem lub zasobu.  
  
-   <xref:System.Data.EntityClient.EntityParameter> lub <xref:System.Data.Objects.ObjectParameter> powinny być używane wszędzie tam, gdzie muszą być przekazywane wartości dostarczone przez użytkownika.  
  
 Należy unikać następujące wzorce zapytań, które zużywają niepotrzebnego miejsca w pamięci podręcznej planu zapytania:  
  
-   Zmiany do rozróżniania wielkości liter w tekście.  
  
-   Zmiany biały znak.  
  
-   Zmiany wartości literału.  
  
-   Zmiany tekstu w komentarzach.  
  
## <a name="see-also"></a>Zobacz także
- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
