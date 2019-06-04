---
title: Aggregate Functions (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: b01c7dca675e79c61b87bcc1fb30455286db3118
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489965"
---
# <a name="aggregate-functions-entity-sql"></a>Aggregate Functions (Entity SQL)
Wartość zagregowana jest konstrukcją języka, która zmniejsza objętość kolekcji do skalaru jako część operacji grupy. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] agregacje są dostępne w dwóch formach:  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Funkcje kolekcji, które mogą być używane w dowolnym miejscu w wyrażeniu. W tym za pomocą funkcji agregujących w projekcji oraz predykatów, które działają w kolekcjach. Kolekcja funkcji jest preferowany tryb, określania wartości zagregowanych umieszczonych w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
- Grupy agregacje w wyrażeniach zapytań, które zawierać klauzuli GROUP BY. Tak jak w języku Transact-SQL agregacje grupy Zaakceptuj DISTINCT, a wszystkie jako modyfikatory do agregacji danych wejściowych.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] po raz pierwszy próbuje można zinterpretować wyrażenia w funkcji kolekcji i jeśli wyrażenie ma w kontekście wyrażenia wybierz je zinterpretuje ją jako agregację grupy.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] definiuje specjalny aggregate-operator o nazwie [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md). Ten operator można uzyskać odwołanie do zestawu pogrupowanych danych wejściowych. Umożliwia to bardziej zaawansowanych zapytań, grupowanie, której wyniki w klauzuli GROUP BY może służyć w miejsc innych niż agregacji grup lub kolekcji funkcji.  
  
## <a name="collection-functions"></a>Kolekcja funkcji  
 Funkcje kolekcji działają w kolekcjach i zwracać wartość skalarną. Na przykład jeśli `orders` to zbiór wszystkich `orders`, można obliczyć Najwcześniejsza data wysyłki za pomocą następującego wyrażenia:  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a>Agregacje grupy  
 Agregacje grupy są obliczane w wyniku grupy, zgodnie z definicją w klauzuli GROUP BY. W klauzuli GROUP BY partycjonowania danych w grupy. Dla każdej grupy w wyniku zastosowaniu funkcji agregującej i oddzielnych agregacji jest obliczana przy użyciu elementów w każdej grupie jako dane wejściowe do obliczania agregacji. Gdy klauzula GROUP BY jest używany w wyrażeniu wybierz tylko grupowanie nazwy wyrażeń, agregacje lub wyrażeń stałych może znajdować się w projekcji, problemy, lub klauzula ORDER BY.  
  
 W poniższym przykładzie oblicza średnią ilość uporządkowane dla każdego produktu.  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 Istnieje możliwość mają grupy agregacji bez jawnej klauzuli GROUP BY w wyrażeniu SELECT. Wszystkie elementy są traktowane jako pojedynczej grupy odpowiednikiem w przypadku określenia grupowanie oparte na stałą.  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 Wyrażenia używane w klauzuli GROUP BY są oceniane przy użyciu tego samego zakresu rozpoznawania nazw, które będą widoczne dla wyrażenie klauzuli WHERE.  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
