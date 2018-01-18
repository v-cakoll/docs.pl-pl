---
title: Stronicowania (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6398edb34a2389b113970444d98eec33f4833b93
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
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
 [Porady: powoduje strony za pomocą kwerendy](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)
