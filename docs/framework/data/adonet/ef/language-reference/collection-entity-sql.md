---
title: KOLEKCJA (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 8cd440571726796ee3d2c91e0d2f6b50571e8e27
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217760"
---
# <a name="collection-entity-sql"></a>KOLEKCJA (jednostka SQL)
KOLEKCJA — słowo kluczowe jest używane tylko w definicji wbudowanej funkcji. Funkcje kolekcji są funkcje, które działają na zbiór wartości, a następnie generuje skalarne danych wyjściowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a>Argumenty  
 `type_definition`  
 Wyrażenie, które zwraca kolekcję obsługiwanych typów, wiersze lub odwołania.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat KOLEKCJI — słowo kluczowe zobacz [definicje typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób użycia KOLEKCJI — słowo kluczowe do deklarowania kolekcję jako argument wbudowanej funkcji zapytania liczbę miejsc dziesiętnych.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
