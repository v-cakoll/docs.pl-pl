---
title: '> (Większe niż) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: 0b57f36681575ccbe3239220e89804c804f13f39
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250882"
---
# <a name="-greater-than-entity-sql"></a>> (Większe niż) (Entity SQL)
Porównuje dwa wyrażenia, aby określić, czy lewe wyrażenie ma wartość większą niż prawo wyrażenie.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie. Oba wyrażenia muszą mieć niejawnie wymienialne typy danych.  
  
## <a name="result-types"></a>Typy wyników  
 `true`Jeśli lewe wyrażenie ma wartość większą niż wyrażenie Right; w przeciwnym razie. `false`  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora porównania > do porównywania dwóch wyrażeń, aby określić, czy lewe wyrażenie ma wartość większą niż prawe wyrażenie. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
