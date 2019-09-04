---
title: SPŁASZCZ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 327a20bbc53566846e7d828f511bcd1d25cc5504
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250969"
---
# <a name="flatten-entity-sql"></a>SPŁASZCZ (Entity SQL)
Konwertuje kolekcję kolekcji na spłaszczoną kolekcję. Nowa kolekcja zawiera wszystkie te same elementy co stara kolekcja, ale bez zagnieżdżonej struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a>Argumenty  
 `collection`  
 Dowolne prawidłowe wyrażenie zwracające kolekcję kolekcji wartości do spłaszczenia do pojedynczej kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 `FLATTEN`jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej. Zobacz [z wyjątkiem](except-entity-sql.md) informacji o priorytecie dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa `FLATTEN` operatora do konwertowania kolekcji kolekcji na spłaszczoną kolekcję. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
