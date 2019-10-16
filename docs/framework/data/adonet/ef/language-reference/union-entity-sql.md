---
title: Unia (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: a5a20beb0ab55dcbaf2dbbb75801b50ab9ef6722
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319216"
---
# <a name="union-entity-sql"></a>Unia (Entity SQL)
Łączy wyniki dwóch lub więcej zapytań w jedną kolekcję.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję do połączenia z kolekcją, wszystkie wyrażenia muszą być tego samego typu lub typu wspólnego lub pochodnego jako `expression`.  
  
 UNION  
 Określa, że wiele kolekcji ma być łączonych i zwracane jako pojedyncza kolekcja.  
  
 CAŁĄ  
 Określa, że wielokrotne kolekcje mają być połączone i zwracane jako pojedyncze kolekcje, w tym duplikaty. Jeśli nie zostanie określony, duplikaty są usuwane z kolekcji wyników.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja tego samego typu lub typowego typu podstawowego lub pochodnego jako `expression`.  
  
## <a name="remarks"></a>Uwagi  
 Unia jest jednym z operatorów zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Wszystkie operatory zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są oceniane od lewej do prawej. Aby uzyskać informacje o pierwszeństwie dla operatorów zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zobacz [except](except-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora UNION ALL do łączenia wyników dwóch zapytań w jedną kolekcję. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#UNION](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#union)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
