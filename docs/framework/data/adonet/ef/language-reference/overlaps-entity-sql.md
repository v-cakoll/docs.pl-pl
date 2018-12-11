---
title: Nakładania się (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: f0c5d79b437ff06603ea10404357aa0b3270bc53
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150781"
---
# <a name="overlaps-entity-sql"></a>Nakładania się (jednostka SQL)
Określa, czy dwie kolekcje mają wspólne elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję do porównania z tą kolekcją zwrócony z innego wyrażenia zapytania. Wszystkie wyrażenia musi być tego samego typu lub wspólnej podstawowej lub pochodny typ jako `expression`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli dwie kolekcje mają wspólne elementy; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Nakładania się zawiera funkcjonalnie równoważne do następujących:  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 Nakładania się jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są przetwarzane od lewej do prawej. Pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zestaw operatorów, zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora nakłada się na Określa, czy dwie kolekcje mają wspólną wartość. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić ten, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
