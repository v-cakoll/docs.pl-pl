---
title: Funkcje agregujące (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: 63e366f323b38a24c4d067681b47d8a8b96125b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="aggregate-functions-entity-sql"></a>Funkcje agregujące (jednostka SQL)
Wartość zagregowana jest konstrukcji języka, który pozwala zapisać kolekcji do skalarnej w ramach operacji grupy. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] agregacje są dostępne w dwóch formach:  
  
-   [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Kolekcja funkcji, które mogą być używane w dowolnym miejscu w wyrażeniu. W tym za pomocą funkcji agregujących w projekcjach i predykatów, które działają w kolekcjach. Funkcji kolekcji jest preferowanym trybem określania wartości zagregowanych w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
-   Grupuj wartości zagregowanych w wyrażeniach zapytań, które mają klauzuli GROUP BY. Podobnie jak w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], agregacje grupy Zaakceptuj DISTINCT, a wszystkie jako modyfikatory do agregacji danych wejściowych.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] po raz pierwszy próbuje zinterpretować wyrażenia w funkcji kolekcji i jeśli wyrażenie jest w kontekście wyrażenia SELECT zinterpretuje ją jako agregacja grupy.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Definiuje specjalne operatora agregacji o nazwie [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md). Ten operator pozwala uzyskać odwołania do zestawu wejściowego grupowanych. Umożliwia to bardziej zaawansowanych zapytań, grupowanie, gdzie można wyniki w klauzuli GROUP BY w miejscach innych niż agregacji grup lub kolekcji funkcji.  
  
## <a name="collection-functions"></a>Kolekcja funkcji  
 Kolekcja funkcji działać w kolekcjach i zwracać wartość skalarną. Na przykład jeśli `orders` to zbiór wszystkich `orders`, można obliczyć Najwcześniejsza data wysyłki z następującym wyrażeniem:  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a>Agreguje grupy  
 Agreguje grupy są obliczane w wyniku grupy, zgodnie z definicją w klauzuli GROUP BY. W klauzuli GROUP BY partycje danych w grupach. Dla każdej grupy w wyniku zastosowaniu funkcji agregującej i oddzielne agregacji jest obliczana przy użyciu elementów w każdej grupie jako danych wejściowych w celu obliczania agregacji. Po klauzuli GROUP BY jest używany w wyrażeniu Wybierz grupowanie tylko nazwy wyrażeń, agregacje lub wyrażenia stałe może znajdować się w projekcji, mając, lub klauzula ORDER BY.  
  
 W poniższym przykładzie oblicza średnią ilość uporządkowane dla każdego produktu.  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 Jest możliwe w wyrażeniu wybierz grupę agregacji bez jawnej klauzuli GROUP BY. Wszystkie elementy będą traktowane jako pojedynczej grupy odpowiednikiem w przypadku określania grupowanie oparte na stałą.  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 Wyrażenia używane w klauzuli GROUP BY są oceniane przy użyciu tego samego zakresu rozpoznawania nazw, które będą widoczne dla wyrażenia klauzuli WHERE.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
