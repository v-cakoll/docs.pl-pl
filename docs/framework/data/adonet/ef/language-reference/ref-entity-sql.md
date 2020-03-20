---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 40a5afd7eb99dba7cae8fe14ed0a45213fda94a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149950"
---
# <a name="ref-entity-sql"></a>REF (Entity SQL)
Zwraca odwołanie do wystąpienia jednostki.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
REF( expression )
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie, które daje wystąpienie typu jednostki.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do określonego wystąpienia jednostki.  
  
## <a name="remarks"></a>Uwagi  
 Odwołanie do jednostki składa się z klucza jednostki i nazwy zestawu jednostek. Ponieważ różne zestawy jednostek mogą być oparte na tym samym typie encji, klucz określonej jednostki może pojawić się w wielu zestawach jednostek. Jednak odwołanie do jednostki jest zawsze unikatowe. Jeśli wyrażenie wejściowe reprezentuje utrwaloną jednostkę, zostanie zwrócone odwołanie do tej jednostki. Jeśli wyrażenie wejściowe nie jest utrwaloną jednostką, zostanie zwrócone odwołanie null.  
  
 Jeśli operator wyodrębniania właściwości (.) jest używany do uzyskiwania dostępu do właściwości jednostki, odwołanie jest automatycznie wyłuskiwane.  
  
## <a name="example"></a>Przykład  
 Następująca kwerenda SQL jednostki używa operatora REF do zwrócenia odwołania dla argumentu jednostki wejściowej. Ta sama kwerenda wyłuduje odwołanie, ponieważ używamy operacji wyodrębniania właściwości (.) w celu uzyskania dostępu do właściwości Product jednostki. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą [w : Jak wykonać kwerendę, która zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Przekaż następującą kwerendę jako `ExecutePrimitiveTypeQuery` argument do metody:  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a>Zobacz też

- [DEREF](deref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [Klucz](key-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Definicje typu](type-definitions-entity-sql.md)
