---
title: W (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: 5a07ee79d5452da4341d391fae7c997c33b603a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250658"
---
# <a name="in-entity-sql"></a>W (Entity SQL)
Określa, czy wartość jest zgodna z dowolną wartością w kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `value`  
 Dowolne prawidłowe wyrażenie zwracające wartość do dopasowania.  
  
 NIEMOŻLIWE  
 Określa, że `Boolean` wynik jest negacji.  
  
 `expression`  
 Dowolne prawidłowe wyrażenie zwracające kolekcję do przetestowania w celu dopasowania. Wszystkie wyrażenia muszą być tego samego typu lub według `value`wspólnego typu podstawowego lub pochodnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli wartość zostanie znaleziona w kolekcji; wartość null, jeśli wartość jest równa null lub kolekcja ma wartość null; w przeciwnym razie. `false` Użycie nie jest w wyniku negacji wyników w.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora IN, aby określić, czy wartość pasuje do dowolnej wartości w kolekcji. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
