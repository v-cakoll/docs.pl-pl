---
title: '! = (Nie równa się) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: c2ccadaa5801cac9c10241108f02ade223a8697f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249849"
---
# <a name="-not-equal-to-entity-sql"></a>! = (Nie równa się) (Entity SQL)
Porównuje dwa wyrażenia, aby określić, czy lewe wyrażenie nie jest równe wyrażeniu z prawej strony. Operator! = (nie równa się) jest funkcjonalnie równoważny operatorowi > <.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie. Oba wyrażenia muszą mieć niejawnie wymienialne typy danych.  
  
## <a name="result-types"></a>Typy wyników  
 `true`Jeśli wyrażenie po lewej stronie nie jest równe wyrażeniu z prawej strony; w przeciwnym razie. `false`  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora! = do porównywania dwóch wyrażeń, aby określić, czy lewe wyrażenie nie jest równe wyrażeniu z prawej strony. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
