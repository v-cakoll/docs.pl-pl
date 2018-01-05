---
title: "Za pomocą (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: cc69dba9e70bb6bcc870b1cb92e98cb656cad98e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-entity-sql"></a>Za pomocą (jednostka SQL)
Określa obszarów nazw używanych w wyrażeniu zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Argumenty  
 `alias`  
 Określa krótszą alias na kwalifikować się obszar nazw o.  
  
 `namespace`  
 Dowolny prawidłowy obszar nazw.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora USING do określania przestrzeni nazw używany w wyrażeniu zapytania. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzenie nazw](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
