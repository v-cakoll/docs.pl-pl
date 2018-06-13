---
title: GDZIE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 43c038e9ff0acfdeff88492aa2ca34fbf4ada94a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764317"
---
# <a name="where-entity-sql"></a>GDZIE (jednostka SQL)
Klauzula WHERE jest stosowana bezpośrednio po [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) klauzuli.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Typ Boolean.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula WHERE ma tej samej semantyki zgodnie z opisem dla [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Ogranicza obiekty utworzone przez wyrażenie zapytania dzięki ograniczeniu liczby elementów kolekcji źródłowej do tych, które przekazują warunku.  
  
```  
select c from cs as c where e  
```  
  
 Wyrażenie `e` musi być typu Boolean.  
  
 Klauzula WHERE jest stosowana bezpośrednio po klauzuli FROM a przed grupowania, porządkowanie ani projekcji ma miejsce. Wszystkie nazwy elementów zdefiniowanych w klauzuli FROM są widoczne dla wyrażenia w klauzuli WHERE.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Wyrażenia zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
