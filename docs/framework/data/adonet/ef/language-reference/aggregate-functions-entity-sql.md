---
title: Funkcje agregujące (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: c79071e73763b56c0dde906499f3eef1d296ce0c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251339"
---
# <a name="aggregate-functions-entity-sql"></a>Funkcje agregujące (Entity SQL)
Agregacja jest konstrukcja języka, która przekształca kolekcję do skalarnej jako część operacji grupy. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]agregacje są dostępne w dwóch formach:  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)]funkcje kolekcji, które mogą być używane w dowolnym miejscu w wyrażeniu. Obejmuje to używanie funkcji agregujących w projekcjach i predykatach, które działają na kolekcjach. Funkcje kolekcji są preferowanym trybem określania wartości zagregowanych [!INCLUDE[esql](../../../../../../includes/esql-md.md)]w elemencie.  
  
- Grupowanie agregacji w wyrażeniach zapytania, które mają klauzulę GROUP BY. Podobnie jak w języku Transact-SQL, agregacje grup akceptują różne i wszystkie jako modyfikatory do zagregowanych danych wejściowych.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]najpierw próbuje zinterpretować wyrażenie jako funkcję kolekcji, a jeśli wyrażenie znajduje się w kontekście wyrażenia SELECT, interpretuje je jako agregację grupy.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]definiuje specjalny operator agregujący o nazwie [GROUPPARTITION](grouppartition-entity-sql.md). Ten operator umożliwia uzyskanie odwołania do pogrupowanego zestawu danych wejściowych. Pozwala to na bardziej zaawansowane zapytania grupujące, gdzie wyniki klauzuli GROUP BY mogą być używane w miejscach innych niż agregacja lub funkcje kolekcji grupy.  
  
## <a name="collection-functions"></a>Funkcje kolekcji  
 Funkcje kolekcji działają na kolekcjach i zwracają wartość skalarną. Na przykład jeśli `orders` jest kolekcją wszystkich `orders`, można obliczyć najwcześniejszą datę wysyłki przy użyciu następującego wyrażenia:  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a>Agregacje grup  
 Agregacje grup są obliczane na podstawie wyniku grupy zgodnie z definicją w klauzuli GROUP BY. Klauzula GROUP BY dzieli dane na grupy. Dla każdej grupy w wyniku stosowana jest funkcja agregująca i oddzielna wartość zagregowana jest obliczana przy użyciu elementów w każdej grupie jako dane wejściowe obliczenia agregacji. Gdy klauzula GROUP BY jest używana w wyrażeniu SELECT, w klauzuli projekcji, HAVING lub ORDER BY może występować tylko nazwa wyrażenia grupującego, agregacje lub wyrażenia stałe.  
  
 Poniższy przykład oblicza średnią ilość zamówioną dla każdego produktu.  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 Możliwe jest posiadanie agregacji grupowej bez jawnej klauzuli GROUP BY w wyrażeniu SELECT. Wszystkie elementy będą traktowane jako pojedyncze grupy, równoważne przypadku określania grupowania na podstawie stałej.  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 Wyrażenia używane w klauzuli GROUP BY są oceniane przy użyciu tego samego zakresu rozpoznawania nazw, który byłby widoczny dla wyrażenia klauzuli WHERE.  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje](functions-entity-sql.md)
