---
title: KOLEKCJA (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: d4e52bb62412e61e1a71e0fe9a8555068ca18dbd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506462"
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
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
