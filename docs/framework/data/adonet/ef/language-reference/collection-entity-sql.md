---
title: Kolekcja (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 0e611add4ce3f20e42bb01b0bf0392bbe81ec548
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251198"
---
# <a name="collection-entity-sql"></a>Kolekcja (Entity SQL)
Słowo kluczowe COLLECTION jest używane tylko w definicji wbudowanej funkcji. Funkcje kolekcji to funkcje, które działają na kolekcji wartości i tworzą skalarne dane wyjściowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a>Argumenty  
 `type_definition`  
 Wyrażenie zwracające kolekcję obsługiwanych typów, wierszy lub odwołań.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat słowa kluczowego kolekcja, zobacz [definicje typów](type-definitions-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać słowa kluczowego COLLECTION do deklarowania kolekcji miejsc dziesiętnych jako argumentu dla wbudowanej funkcji zapytania.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
