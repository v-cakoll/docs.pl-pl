---
title: Buforowanie planu kwerend (entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: a0e84f40aed2cff146e4e203cca73a9110de0e2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149989"
---
# <a name="query-plan-caching-entity-sql"></a>Buforowanie planu kwerend (entity SQL)
Za każdym razem, gdy podejmowana jest próba wykonania kwerendy, potok zapytań wyszukuje swoją pamięć podręczną planu kwerend, aby zobaczyć, czy dokładna kwerenda jest już skompilowana i dostępna. Jeśli tak, używa ponownie buforowanego planu, a nie tworzenie nowego. Jeśli dopasowanie nie zostanie znalezione w pamięci podręcznej planu kwerendy, kwerenda jest kompilowana i buforowana. Kwerenda jest identyfikowana przez jego kolekcję [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tekstu i parametrów (nazwy i typy). We wszystkich porównaniach tekstu rozróżniana jest wielkość liter.  
  
## <a name="configuration"></a>Konfigurowanie  
 Buforowanie planu kwerend można konfigurować za pomocą pliku <xref:System.Data.EntityClient.EntityCommand>.  
  
 Aby włączyć lub wyłączyć buforowanie <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>planu kwerend `true` za `false`pośrednictwem , ustaw tę właściwość na lub . Wyłączenie buforowania planu dla poszczególnych zapytań dynamicznych, które są mało prawdopodobne, aby być używane więcej niż raz zwiększa wydajność.  
  
 Można włączyć buforowanie planu <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>kwerend za pośrednictwem programu .  
  
## <a name="recommended-practice"></a>Zalecana praktyka  
 Ogólnie należy unikać zapytań dynamicznych. Poniższy przykład zapytania dynamicznego jest podatny na ataki iniekcji SQL, ponieważ pobiera dane wejściowe użytkownika bezpośrednio bez sprawdzania poprawności.  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```

 Jeśli używasz kwerend generowanych dynamicznie, należy rozważyć wyłączenie buforowania planu kwerend, aby uniknąć niepotrzebnego zużycia pamięci dla wpisów pamięci podręcznej, które są mało prawdopodobne, aby być ponownie używane.  
  
 Buforowanie planu kwerend w kwerendach statycznych i kwerendach sparametryzowanych może zapewnić korzyści z wydajności. Poniżej przedstawiono przykład kwerendy statycznej:  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 Aby kwerendy były prawidłowo dopasowane przez pamięć podręczną planu kwerend, powinny one spełniać następujące wymagania:  
  
- Tekst kwerendy powinien być stałym wzorcem, najlepiej stałym ciągiem lub zasobem.  
  
- <xref:System.Data.EntityClient.EntityParameter>lub <xref:System.Data.Objects.ObjectParameter> powinny być używane wszędzie tam, gdzie musi zostać przekazana wartość dostarczona przez użytkownika.  
  
 Należy unikać następujących wzorców zapytań, które niepotrzebnie zużywają gniazda w pamięci podręcznej planu kwerendy:  
  
- Zmiany w literze w tekście.  
  
- Zmiany w odstępie.  
  
- Zmiany wartości literału.  
  
- Zmiany w tekście wewnątrz komentarzy.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie jednostki SQL](entity-sql-overview.md)
