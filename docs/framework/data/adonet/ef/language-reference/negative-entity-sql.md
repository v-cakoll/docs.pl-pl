---
title: '- (Negatywna) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 343f53b2a6fc54a5be6f8673348384567b48262b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102846"
---
# <a name="--negative-entity-sql"></a>-(Ujemnej) (jednostka SQL)
Zwraca wartość ujemną wartość wyrażenia liczbowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
- expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie jeden z typów liczbowych.  
  
## <a name="result-types"></a>Typy wyników  
 Typ danych `expression`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `expression` jest typ bez znaku typu wyniku będzie typ ze znakiem, który najlepiej odnosi się do typu `expression`. Na przykład jeśli `expression` typu Byte, wartości typu Int16 zostaną zwrócone.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operator arytmetyczny, aby zwrócić wartość ujemną wartość wyrażenia liczbowego. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
