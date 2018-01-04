---
title: "Wyrażenia zapytań (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8ad130797be55b33b319ca4e85de09ec3e00a554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="query-expressions-entity-sql"></a>Wyrażenia zapytań (jednostka SQL)
Wyrażenia zapytania łączy wielu operatorów innego zapytania w jednym składni. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zawiera różne rodzaje wyrażeń, takie jak: [literały](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parametry](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [zmienne](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), operatory, [funkcje](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), ustawienie operatory i tak dalej. Aby uzyskać więcej informacji, zobacz [odwołania do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).  
  
## <a name="clauses"></a>Klauzule  
 Wyrażenia zapytania składa się z szeregu klauzule dotyczące kolekcji obiektów kolejne czynności. Są one oparte na klauzule tego samego odnaleźć w standardzie instrukcję SQL select: [wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [gdzie](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [o](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), i [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).  
  
## <a name="scope"></a>Zakres  
 Nazwy określone w klauzuli FROM są wprowadzane do zakresu od w kolejności wyświetlania od lewej do prawej. Na liście łączenia wyrażenia mogą odwoływać się do zdefiniowanych wcześniej na liście nazw. Właściwości publiczne elementów określonych w klauzuli FROM nie są dodawane do zakresu od: muszą być zawsze przywoływane przez nazwę kwalifikowaną alias. Zwykle wszystkie części wyrażenie select są traktowane jako w zakresie od.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
