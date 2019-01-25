---
title: W (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: a8c028bf0fc2890b932c62aa9efe94cab153503d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693493"
---
# <a name="in-entity-sql"></a>W (jednostka SQL)
Określa, czy wartość pasuje do dowolnej wartości w kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `value`  
 Dowolne prawidłowe wyrażenie zwracające wartość do dopasowania.  
  
 [ NOT ]  
 Określa, że `Boolean` wynik w być ujemna.  
  
 `expression`  
 Dowolne prawidłowe wyrażenie, które zwraca kolekcję do testowania pod kątem dopasowania. Wszystkie wyrażenia musi być tego samego typu lub wspólnej podstawowej lub pochodny typ jako `value`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli wartość zostanie znaleziony w kolekcji; wartość null, jeśli ma wartość null lub kolekcji mają wartość null; w przeciwnym razie `false`. Za pomocą NOT IN neguje wyniki cali  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora w celu ustalenia, czy wartość pasuje do dowolnej wartości w kolekcji. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a>Zobacz także
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
