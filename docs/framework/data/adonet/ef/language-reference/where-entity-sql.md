---
title: GDZIE (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2ad170500770bc370eb67a04ab29d0c9f9dcaabd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
