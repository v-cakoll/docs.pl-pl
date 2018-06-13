---
title: Stronicowania (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 946e7da12481eb7dac880d6ce8a56b546bdcd822
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764869"
---
# <a name="paging-entity-sql"></a>Stronicowania (jednostka SQL)
Stronicowanie fizycznych można wykonać za pomocą [POMIŃ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) i [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) podklauzul w [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli. Do wykonania fizycznego stronicowania w sposób niejednoznaczny, należy używać SKIP i LIMIT. Jeśli chcesz ograniczyć liczbę wierszy w wyniku w sposób z systemem innym niż determinsitic, należy użyć [GÓRNEJ](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md). TOP i SKIP/LIMIT wzajemnie się wykluczają.  
  
## <a name="top-overview"></a>TOP — omówienie  
 Klauzula SELECT może mieć opcjonalne TOP Podklauzula następujące opcjonalne modyfikator ALL/DISTINCT. Klauzul podrzędnych TOP Określa, że tylko pierwszy zestaw wierszy zostaną zwrócone w wyniku zapytania. Aby uzyskać więcej informacji, zobacz [GÓRNEJ](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>POMIŃ i LIMIT — omówienie  
 POMIŃ i LIMIT są częścią klauzuli ORDER BY. Jeśli klauzul podrzędnych SKIP w wyrażeniu znajduje się w klauzuli ORDER BY, będzie można posortować wyników według specyfikacji sortowania i zestaw wyników zawiera wiersze, zaczynając od następnego wiersza od razu po wyrażeniu SKIP. Na przykład 5 POMIŃ Pomiń pierwsze pięć wiersze i zwrócenia z wiersza szóstego do przodu. Jeśli LIMIT klauzul podrzędnych wyrażenia znajduje się w klauzuli ORDER BY, zapytanie będzie można sortować według specyfikacji sortowania i wynikowa liczba wierszy zostanie ograniczony przez wyrażenie LIMIT. Na przykład LIMIT 5 ogranicza zestaw wyników do pięciu wystąpień lub wierszy. POMIŃ i LIMIT nie muszą być używane razem; można użyć tylko POMIŃ lub po prostu ograniczenia z klauzuli ORDER BY. Więcej informacji znajduje się w następujących tematach:  
  
-   [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Porady: powoduje strony za pomocą kwerendy](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)
