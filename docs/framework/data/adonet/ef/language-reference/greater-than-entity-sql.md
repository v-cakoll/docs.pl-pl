---
title: '> (Większe niż) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: e1d13fa863eb79982d239f4e2dc298f7fcd1346f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328559"
---
# <a name="-greater-than-entity-sql"></a>> (Większe niż) (jednostka SQL)
Porównuje dwa wyrażenia w celu określenia, czy lewe wyrażenie ma wartość większą niż wyrażenie prawej krawędzi.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie. Oba wyrażenia muszą mieć niejawnej konwersji typów.  
  
## <a name="result-types"></a>Typy wyników  
 `true` Jeśli po lewej stronie wyrażenie ma wartość większą niż wyrażenie prawej krawędzi; w przeciwnym razie `false`.  
  
## <a name="example"></a>Przykład  
 Używa następującego zapytania SQL jednostki > operator porównania do porównywania dwóch wyrażeń w celu ustalenia, czy lewe wyrażenie ma wartość większą niż wyrażenie prawej krawędzi. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
