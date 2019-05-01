---
title: Z wyjątkiem (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 32b5148e43a38e5cf8dcce0ae16260d7a6b6a018
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034219"
---
# <a name="except-entity-sql"></a>Z wyjątkiem (jednostka SQL)
Zwraca kolekcję wszystkie unikatowe wartości w wyrażeniu zapytania do lewego operandu EXCEPT, które nie są również zwracany z wyrażenia zapytania po prawej stronie operandu EXCEPT. Wszystkie wyrażenia musi być tego samego typu lub wspólnej podstawowej lub pochodny typ jako `expression`.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję do porównania z tą kolekcją zwrócony z innego wyrażenia zapytania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcji tego samego typu lub wspólnej podstawowej lub pochodny typ jako `expression`.  
  
## <a name="remarks"></a>Uwagi  
 Z wyjątkiem jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są przetwarzane od lewej do prawej. W poniższej tabeli przedstawiono pierwszeństwo [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.  
  
|Pierwszeństwo|Operatory|  
|----------------|---------------|  
|Najwyższy|INTERSECT|  
||UNION<br /><br /> UNION ALL|  
||EXCEPT|  
|Najniższy|EXISTS<br /><br /> OVERLAPS<br /><br /> FLATTEN<br /><br /> SET|  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora EXCEPT zwrócić kolekcję wszystkie unikatowe wartości z dwóch wyrażeń zapytania. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
