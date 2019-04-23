---
title: Stronicowanie (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: dd6653c00c72697fa5e8ae896968ec2a9f09ae82
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167144"
---
# <a name="paging-entity-sql"></a>Stronicowanie (jednostka SQL)
Stronicowanie fizycznych można wykonać przy użyciu [POMIŃ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) i [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) podklauzul w [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli. Do wykonania, fizycznych stronicowania w sposób deterministyczny, należy używać SKIP i LIMIT. Jeśli chcesz ograniczyć liczbę wierszy w wyniku w sposób niejednoznaczny, należy użyć [GÓRNEJ](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md). TOP i SKIP/LIMIT wzajemnie się wykluczają.  
  
## <a name="top-overview"></a>GÓRNY — omówienie  
 Klauzula SELECT może mieć opcjonalny Podklauzula TOP następujące opcjonalny modyfikator właściwy ALL/DISTINCT. Podklauzula TOP Określa, że tylko pierwszy zestaw wierszy zostaną zwrócone w wyniku zapytania. Aby uzyskać więcej informacji, zobacz [GÓRNEJ](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>Omówienie limitu i POMIŃ  
 POMIŃ i LIMIT stanowią element klauzuli ORDER BY. Jeśli POMIŃ wyrażenie Podklauzula znajduje się w klauzuli ORDER BY, wyniki będą sortowane według specyfikacji sortowania i zestawu wyników będzie zawierać wiersze, począwszy od następnego wiersza od razu po wyrażeniu SKIP. Na przykład 5 POMIŃ Pomiń pierwsze pięć wierszy i zwraca od szóstego wierszy do przodu. Jeśli LIMIT wyrażenia Podklauzula znajduje się w klauzuli ORDER BY, zapytania będą sortowane według specyfikacji sortowania i wynikowa liczba wierszy, zostanie nałożone przez wyrażenie LIMIT. Na przykład LIMIT 5 ograniczyć zestaw wyników do pięciu wystąpień lub wiersze. POMIŃ i LIMIT nie muszą być używane razem; można użyć tylko POMIŃ lub po prostu OGRANICZYĆ przy użyciu klauzuli ORDER BY. Więcej informacji znajduje się w następujących tematach:  
  
-   [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Instrukcje: Przejrzyj wyniki zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
