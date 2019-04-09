---
title: (Modulo) (Jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: b08689b6f5b17950738c557e02f995fa85aeb35e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160488"
---
# <a name="modulo-entity-sql"></a>(Modulo) (Jednostka SQL)
Zwraca resztę z dzielenia jednego wyrażenia podzielona przez inny.  
  
## <a name="syntax"></a>Składnia  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Argumenty  
 `dividend`  
 Wyrażenie liczbowe, aby podzielić. `dividend` jest dowolne prawidłowe wyrażenie jednego z typów liczbowych.  
  
 `divisor`  
 Wyrażenie liczbowe do dzielenia dzielnej przez. `divisor` jest dowolne prawidłowe wyrażenie jednego z typów liczbowych.  
  
## <a name="result-types"></a>Typy wyników  
 Edm.Int32  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora arytmetycznego % do zwracania końca jedno wyrażenie podzielona przez inny. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
