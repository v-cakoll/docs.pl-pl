---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: b551d15d7de2cf07afc7455b7fd0a0faf6436ccf
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319182"
---
# <a name="where-entity-sql"></a>WHERE (Entity SQL)
Klauzula WHERE jest stosowana bezpośrednio po klauzuli [from](from-entity-sql.md) .  
  
## <a name="syntax"></a>Składnia  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Typ wartości logicznej.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula WHERE ma tę samą semantykę, jak opisano w języku Transact-SQL. Ogranicza obiekty utworzone przez wyrażenie zapytania przez ograniczenie elementów kolekcji źródłowych do tych, które przechodzą warunek.  
  
```sql  
select c from cs as c where e  
```  
  
 Wyrażenie `e` musi mieć typ Boolean.  
  
 Klauzula WHERE jest stosowana bezpośrednio po klauzuli FROM i przed utworzeniem grupowania, porządkowania lub projekcji. Wszystkie nazwy elementów zdefiniowane w klauzuli FROM są widoczne dla wyrażenia klauzuli WHERE.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Wyrażenia zapytania](query-expressions-entity-sql.md)
