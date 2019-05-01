---
title: REF (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 05e687f951930d92797a863410181585278b067d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797764"
---
# <a name="ref-entity-sql"></a>REF (jednostka SQL)
Zwraca odwołanie do wystąpienia jednostki.  
  
## <a name="syntax"></a>Składnia  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie, które zwracają wystąpienia typu jednostki.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do wystąpienia określonej jednostki.  
  
## <a name="remarks"></a>Uwagi  
 Odwołania do jednostki, który składa się z klucza podmiotu i nazwy zestawu jednostek. Ponieważ zestawy jednostek innej mogą opierać się na ten sam typ jednostki klucza określonej jednostki mogą być wyświetlane w wielu zestawach jednostki. Jednak odwołania do jednostki jest zawsze unikatowa. Jeśli wyrażenie wejściowe reprezentuje utrwalonych jednostki, zostaną zwrócone odwołanie do tej jednostki. Jeśli wyrażenie wejściowe nie jest utrwalona jednostki, zostaną zwrócone odwołanie o wartości null.  
  
 Operator wyodrębniania właściwości (.) jest używane do dostępu do właściwości jednostki, odwołanie jest automatycznie wyłuskiwany.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora REF zwrócić odwołanie do argumentu wejściowego jednostki. Tego samego zapytania wyłuskań odwołanie, ponieważ używamy operacji wyodrębniania właściwości (.) do dostępu do właściwości jednostki produktu. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a>Zobacz także

- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
- [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Definicje typu](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
