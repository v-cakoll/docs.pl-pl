---
title: '&lt;= (Mniejsze niż lub równe) (jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: 66eb2dc5d4b23ea2f4e00888237b36c950c80602
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604031"
---
# <a name="lt-less-than-or-equal-to-entity-sql"></a>&lt;= (Mniejsze niż lub równe) (jednostka SQL)
Porównuje dwa wyrażenia, aby ustalić, czy lewe wyrażenie ma wartość mniejszą niż lub równe wyrażenie prawej krawędzi.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression <= expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie. Oba wyrażenia muszą mieć niejawnej konwersji typów.  
  
## <a name="result-types"></a>Typy wyników  
 `true` Jeśli po lewej stronie wyrażenie ma wartość mniejszą niż lub równe wyrażenie prawej krawędzi; w przeciwnym razie `false`.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa < =, operator porównania do porównywania dwóch wyrażeń w celu ustalenia, czy lewe wyrażenie ma wartość mniejszą niż lub równe wyrażenie prawej krawędzi. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less_or_equals)]  
  
## <a name="see-also"></a>Zobacz także
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
