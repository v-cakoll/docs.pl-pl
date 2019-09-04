---
title: Istnieje (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 20e18bf536f2b89eca9515b3c5dca7ca7fbd6fe5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250987"
---
# <a name="exists-entity-sql"></a>Istnieje (Entity SQL)
Określa, czy kolekcja jest pusta.  
  
## <a name="syntax"></a>Składnia  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie zwracające kolekcję.  
  
 NIEMOŻLIWE  
 Określa, że wynik istnieje jest negacją.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli kolekcja nie jest pusta; w przeciwnym razie. `false`  
  
## <a name="remarks"></a>Uwagi  
 Istnieje, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest jednym z operatorów zestawu. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej. Aby uzyskać informacje o pierwszeństwie dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu, zobacz [except](except-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora EXISTS, aby określić, czy kolekcja jest pusta. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
