---
title: + (Dodaj)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: a3c41ef8cf393a4d1b1deb362d6a3614558a34ba
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46529804"
---
# <a name="-add"></a>+ (Dodaj)
Dodaje dwie liczby.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie jeden z typów liczbowych.  
  
## <a name="result-types"></a>Typy wyników  
 Typ danych będącą wynikiem promocji niejawnego typu dwa argumenty. Aby uzyskać więcej informacji na temat podwyższania poziomu konwersjom typu niejawnego, zobacz [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać EDM. Typy ciągu, dodanie jest łączenia.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa + operatora arytmetycznego na dodanie dwóch liczb. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytania, że zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Model koncepcyjny typów (CSDL)](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
