---
title: '! = (Nie równa się) (jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: d5e59fe61dbc05a48e98f5720dca446482b9968e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568139"
---
# <a name="-not-equal-to-entity-sql"></a>! = (Nie równa się) (jednostka SQL)
Porównuje dwa wyrażenia w celu ustalenia, czy po lewej stronie wyrażenia nie jest równa wyrażenie prawej krawędzi. ! = — Operator (nie równa się) jest funkcjonalnym odpowiednikiem < > — operator.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie. Oba wyrażenia muszą mieć niejawnej konwersji typów.  
  
## <a name="result-types"></a>Typy wyników  
 `true` Jeśli po lewej stronie wyrażenia nie jest równa wyrażenie prawej krawędzi; w przeciwnym razie `false`.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa! = — operator do porównywania dwóch wyrażeń w celu ustalenia, czy po lewej stronie wyrażenia nie jest równa wyrażenie prawej krawędzi. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a>Zobacz także
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
