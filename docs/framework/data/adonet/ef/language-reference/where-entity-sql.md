---
title: GDZIE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 0b9cf9bdb211a74acd8fc229c53f3565b48e5ddd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670579"
---
# <a name="where-entity-sql"></a>GDZIE (jednostka SQL)
Bezpośrednio po zastosowaniu klauzuli WHERE [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) klauzuli.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Typ Boolean.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula WHERE ma tą samą semantyką zgodnie z opisem dla [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Ogranicza obiekty utworzone przez wyrażenie zapytania, ograniczając elementy kolekcji źródłowej do tych, które upłynąć warunek.  
  
```  
select c from cs as c where e  
```  
  
 Wyrażenie `e` musi być typu Boolean.  
  
 Klauzula WHERE jest stosowany bezpośrednio po elemencie klauzuli FROM a przed dowolnego grupowania, porządkowanie lub projekcji ma miejsce. Wszystkie nazwy elementów, które określono w klauzuli FROM są widoczne dla wyrażenia w klauzuli WHERE.  
  
## <a name="see-also"></a>Zobacz także
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Wyrażenia zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
