---
title: Za pomocą (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 6a5b374bc253cb2deb7a9e1de942c32d8e8bbfcf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168028"
---
# <a name="using-entity-sql"></a>Za pomocą (jednostka SQL)
Określa przestrzeń nazw używaną w wyrażeniu zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Argumenty  
 `alias`  
 Określa krótszy alias do kwalifikowania przestrzeni nazw za pomocą.  
  
 `namespace`  
 Dowolny prawidłowy obszar nazw.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora USING do określania przestrzeni nazw używany w wyrażeniu zapytania. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Zobacz także

- [Namespaces](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)
- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
