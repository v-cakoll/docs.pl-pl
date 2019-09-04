---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 8dd0e34a6669b2147052befb17b8f4ff8395aabc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248486"
---
# <a name="where-entity-sql"></a>WHERE (Entity SQL)
Klauzula WHERE jest stosowana bezpośrednio po klauzuli [from](from-entity-sql.md) .  
  
## <a name="syntax"></a>Składnia  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Typ wartości logicznej.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula WHERE ma tę samą semantykę, jak opisano w języku Transact-SQL. Ogranicza obiekty utworzone przez wyrażenie zapytania przez ograniczenie elementów kolekcji źródłowych do tych, które przechodzą warunek.  
  
```  
select c from cs as c where e  
```  
  
 Wyrażenie `e` musi mieć typ Boolean.  
  
 Klauzula WHERE jest stosowana bezpośrednio po klauzuli FROM i przed utworzeniem grupowania, porządkowania lub projekcji. Wszystkie nazwy elementów zdefiniowane w klauzuli FROM są widoczne dla wyrażenia klauzuli WHERE.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Wyrażenia zapytania](query-expressions-entity-sql.md)
