---
title: '* (Należy pomnożyć) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 308df758d59a7e12a8b5a19ae72fcbee2f168490
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329729"
---
# <a name="-multiply-entity-sql"></a>* (Mnożenie) (jednostka SQL)
Mnoży dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie jeden z typów liczbowych.  
  
## <a name="result-types"></a>Typy wyników  
 Typ danych będącą wynikiem promocji niejawnego typu dwa argumenty. Aby uzyskać więcej informacji na temat podwyższania poziomu konwersjom typu niejawnego, zobacz [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa * operatora arytmetycznego na mnożenia dwóch liczb. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
