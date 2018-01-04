---
title: KOLEKCJA (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c850fe215c692f204c6762d82a3d37b29c556a7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="collection-entity-sql"></a>KOLEKCJA (jednostka SQL)
KOLEKCJA — słowo kluczowe jest używana tylko w definicji wbudowanej funkcji. Funkcje kolekcji są funkcje, które działają na kolekcję wartości i wygenerować skalarne dane wyjściowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a>Argumenty  
 `type_definition`  
 Wyrażenie, które zwraca kolekcję obsługiwanych typów, wierszy i odwołań.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat — słowo kluczowe KOLEKCJI, zobacz [definicje typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia słowa kluczowego KOLEKCJI można deklarować kolekcji miejsc dziesiętnych jako argumentu dla funkcji wbudowanej zapytania.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
