---
title: '>= (Większe niż lub równe) (jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 1e2eef7c98aefd93c6ef388888661ac758fd8e30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166117"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a>> = (większe niż lub równe) (jednostka SQL)
Porównuje dwa wyrażenia w celu określenia, czy lewe wyrażenie ma wartość większą niż lub równa wyrażenie prawej krawędzi.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie. Oba wyrażenia muszą mieć niejawnej konwersji typów.  
  
## <a name="result-types"></a>Typy wyników  
 `true` Jeśli lewe wyrażenie ma wartość większą niż lub równa wyrażenie prawej krawędzi; w przeciwnym razie `false`.  
  
## <a name="example"></a>Przykład  
 Używa następującego zapytania SQL jednostki > =, operator porównania do porównywania dwóch wyrażeń w celu ustalenia, czy lewe wyrażenie ma wartość większą niż lub równa wyrażenie prawej krawędzi. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
