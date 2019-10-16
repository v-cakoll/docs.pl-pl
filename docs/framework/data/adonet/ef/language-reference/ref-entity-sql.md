---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 08bcaad4fdc0cf5324ff9976fcf48c23b206e72f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319392"
---
# <a name="ref-entity-sql"></a>REF (Entity SQL)
Zwraca odwołanie do wystąpienia jednostki.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
REF( expression )   
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie zwracające wystąpienie typu jednostki.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do określonego wystąpienia jednostki.  
  
## <a name="remarks"></a>Uwagi  
 Odwołanie do jednostki składa się z klucza jednostki i nazwy zestawu jednostek. Ponieważ różne zestawy jednostek mogą opierać się na tym samym typie jednostki, określony klucz jednostki może pojawić się w wielu zestawach jednostek. Odwołanie do jednostki jest jednak zawsze unikatowe. Jeśli wyrażenie danych wejściowych reprezentuje obiekt utrwalony, odwołanie do tej jednostki zostanie zwrócone. Jeśli wyrażenie wejściowe nie jest utrwaloną jednostką, zostanie zwrócone odwołanie o wartości null.  
  
 Jeśli operator wyodrębniania właściwości (.) jest używany w celu uzyskania dostępu do właściwości jednostki, odwołanie zostanie automatycznie wywoływać.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora REF do zwrócenia odwołania dla argumentu jednostki wejściowej. To samo zapytanie odwołuje się do odwołania, ponieważ używamy operacji wyodrębniania właściwości (.) w celu uzyskania dostępu do właściwości jednostki produktu. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [instrukcje: wykonywanie zapytania, które zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecutePrimitiveTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a>Zobacz także

- [DEREF](deref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Definicje typu](type-definitions-entity-sql.md)
