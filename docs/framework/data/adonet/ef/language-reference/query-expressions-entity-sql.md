---
title: Wyrażenia zapytań (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 4428286890f41573a02daf31a4593d0c8f9ad34b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249274"
---
# <a name="query-expressions-entity-sql"></a>Wyrażenia zapytań (Entity SQL)
Wyrażenie zapytania łączy wiele różnych operatorów zapytań w jedną składnię. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]oferuje różne rodzaje wyrażeń, w tym następujące: [literały](literals-entity-sql.md), [Parametry](parameters-entity-sql.md), [zmienne](variables-entity-sql.md), operatory, [funkcje](functions-entity-sql.md), operatory ustawiające itd. Aby uzyskać więcej informacji, zobacz [Entity SQL Reference](entity-sql-reference.md).  
  
## <a name="clauses"></a>Klauzule  
 Wyrażenie zapytania składa się z serii klauzul, które stosują kolejne operacje do kolekcji obiektów. Są one oparte na tych samych klauzulach, które znajdują się w standardowej instrukcji SELECT języka SQL: [SELECT](select-entity-sql.md), [from](from-entity-sql.md), [WHERE](where-entity-sql.md), [Group by](group-by-entity-sql.md), [HAVING](having-entity-sql.md)i [order by](order-by-entity-sql.md).  
  
## <a name="scope"></a>Scope  
 Nazwy zdefiniowane w klauzuli FROM są wprowadzane do zakresu od w kolejności wyglądu, od lewej do prawej. Na liście SPRZĘŻENIa wyrażenia mogą odwoływać się do nazw zdefiniowanych wcześniej na liście. Właściwości publiczne elementów zidentyfikowanych w klauzuli FROM nie są dodawane do zakresu od: Muszą zawsze być przywoływane przez nazwę kwalifikowaną aliasem. Zwykle wszystkie części wyrażenia SELECT są uwzględniane w zakresie od.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
