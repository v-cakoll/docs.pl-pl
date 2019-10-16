---
title: Buforowanie planu zapytania (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 020b2b3f08262fc15ace8603c26e2d6c059baafd
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319406"
---
# <a name="query-plan-caching-entity-sql"></a>Buforowanie planu zapytania (Entity SQL)
Za każdym razem, gdy podejmowana jest próba wykonania zapytania, potok zapytania wyszukuje w pamięci podręcznej planu zapytania, aby sprawdzić, czy dokładne zapytanie jest już skompilowane i dostępne. Jeśli tak, ponownie używa buforowanego planu, zamiast tworzyć nowy. Jeśli dopasowanie nie zostanie odnalezione w pamięci podręcznej planu zapytania, zapytanie jest kompilowane i buforowane. Zapytanie jest identyfikowane za pomocą jego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tekstu i kolekcji parametrów (nazw i typów). Wszystkie porównania tekstu uwzględniają wielkość liter.  
  
## <a name="configuration"></a>Konfiguracja  
 Buforowanie planu zapytania można skonfigurować za pomocą <xref:System.Data.EntityClient.EntityCommand>.  
  
 Aby włączyć lub wyłączyć buforowanie planu zapytania przy użyciu <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, należy ustawić tę właściwość na `true` lub `false`. Wyłączenie pamięci podręcznej planu dla indywidualnych zapytań dynamicznych, które prawdopodobnie nie będą używane więcej, po zwiększeniu wydajności.  
  
 Buforowanie planu zapytania można włączyć za <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.  
  
## <a name="recommended-practice"></a>Zalecane rozwiązanie  
 Zapytania dynamiczne należy unikać w ogóle. Następujący przykład zapytania dynamicznego jest narażony na ataki z iniekcją SQL, ponieważ pobiera dane wprowadzane przez użytkownika bezpośrednio bez sprawdzania poprawności.  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```
 
 W przypadku użycia dynamicznie generowanych zapytań należy rozważyć wyłączenie buforowania planu zapytania, aby uniknąć niepotrzebnego zużycia pamięci dla wpisów pamięci podręcznej, które nie są prawdopodobnie ponownie używane.  
  
 Buforowanie planu zapytania dla zapytań statycznych i zapytań parametrycznych może zapewniać korzyści z wydajności. Poniżej znajduje się przykład kwerendy statycznej:  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 Aby zapytania były odpowiednio dopasowane przez pamięć podręczną planu zapytania, powinny spełniać następujące wymagania:  
  
- Tekst zapytania powinien być stałym wzorcem, najlepiej ciągiem lub zasobem.  
  
- należy używać <xref:System.Data.EntityClient.EntityParameter> lub <xref:System.Data.Objects.ObjectParameter>, wszędzie tam, gdzie wartość dostarczona przez użytkownika musi zostać przekazana.  
  
 Należy unikać następujących wzorców zapytań, które niekoniecznie zużywają gniazda w pamięci podręcznej planu zapytania:  
  
- Zmiany do wielkości liter w tekście.  
  
- Zmiany w białych znakach.  
  
- Zmiany w wartościach literału.  
  
- Zmiany tekstu w komentarzach.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
