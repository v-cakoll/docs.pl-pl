---
title: Wyrażenia zapytań (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 5f89028b9c501dd840f1dc9445418e4757967db8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614625"
---
# <a name="query-expressions-entity-sql"></a>Wyrażenia zapytań (jednostka SQL)
Wyrażenie zapytania łączy wiele operatorów zapytań różnych w jednej składni. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zawiera różne rodzaje wyrażeń, w tym następujące: [literały](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parametry](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [zmienne](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), operatory, [funkcje](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)operatory zestawu i tak dalej. Aby uzyskać więcej informacji, zobacz [odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).  
  
## <a name="clauses"></a>Klauzule  
 Wyrażenie zapytania składa się z szeregu klauzul, które dotyczą kolejnych czynności kolekcji obiektów. Są one oparte na tych samych klauzul znaleźć w standardzie instrukcję select SQL: [Wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [gdzie](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [Grupuj według](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), i [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).  
  
## <a name="scope"></a>Zakres  
 Nazwy zdefiniowane w klauzuli FROM są wprowadzane do zakresu od w kolejności występowania, od lewej do prawej. Na liście sprzężenia wyrażenia mogą odwoływać się do nazwy zdefiniowanej wcześniej na liście. Właściwości publiczne elementy określone w klauzuli FROM nie są dodawane do zakresu od: One muszą być zawsze przywoływane za pośrednictwem nazwy kwalifikowanej aliasu. Zwykle wszystkie części Wybierz wyrażenie są uwzględniane w zakresie od.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
