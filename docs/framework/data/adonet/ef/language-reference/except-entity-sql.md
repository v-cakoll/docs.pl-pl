---
title: Z wyjątkiem (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: d00fdeed01de80e441d28e2bcd5da084571b0361
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251045"
---
# <a name="except-entity-sql"></a>Z wyjątkiem (Entity SQL)
Zwraca kolekcję wszystkich odrębnych wartości z wyrażenia zapytania na lewo od operandu EXCEPT, które nie są zwracane z wyrażenia zapytania z prawej strony operandu EXCEPT. Wszystkie wyrażenia muszą być tego samego typu lub według `expression`wspólnego typu podstawowego lub pochodnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję do porównania z kolekcją zwróconą z innego wyrażenia zapytania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja tego samego typu lub typowego typu podstawowego lub pochodnego jako `expression`.  
  
## <a name="remarks"></a>Uwagi  
 Oprócz tego jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej. W poniższej tabeli przedstawiono pierwszeństwo [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu.  
  
|Pierwszeństwo|Operatory|  
|----------------|---------------|  
|Najwyższy|INTERSECT|  
||UNION<br /><br /> UNION WSZYSTKO|  
||EXCEPT|  
|Okreolon|EXISTS<br /><br /> OVERLAPS<br /><br /> FLATTEN<br /><br /> SET|  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora EXCEPT do zwrócenia kolekcji wszelkich odrębnych wartości z dwóch wyrażeń zapytań. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
