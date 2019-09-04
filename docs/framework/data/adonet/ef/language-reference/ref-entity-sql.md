---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 9d35306d1299e91ecaa55a7d2818ee1e2982793f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249194"
---
# <a name="ref-entity-sql"></a>REF (Entity SQL)
Zwraca odwołanie do wystąpienia jednostki.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-primitivetype-results.md)typu pierwotnego.  
  
2. Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a>Zobacz także

- [DEREF](deref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Definicje typu](type-definitions-entity-sql.md)
