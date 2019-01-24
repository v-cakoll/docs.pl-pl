---
title: Semantyka porównania (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 371999df0fb3177ecc90f9b1fa43d457a51bfd7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492497"
---
# <a name="comparison-semantics-entity-sql"></a>Semantyka porównania (jednostka SQL)
Wykonanie dowolnego z następujących [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory obejmuje porównanie wystąpień typu:  
  
## <a name="explicit-comparison"></a>Porównanie jawne  
 Operacje równości:  
  
-   =  
  
-   !=  
  
 Kolejność operacji:  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 Operacje dopuszczania wartości null:  
  
-   MA WARTOŚĆ NULL  
  
-   NIE MA WARTOŚCI NULL  
  
## <a name="explicit-distinction"></a>Jawne różnicy  
 Rozróżnienie równości:  
  
-   DISTINCT  
  
-   GRUPUJ WEDŁUG  
  
 Kolejność różnicy:  
  
-   ORDER BY  
  
## <a name="implicit-distinction"></a>Niejawna różnicy  
 Ustaw operacje i predykatów (równości):  
  
-   UNION  
  
-   INTERSECT  
  
-   EXCEPT  
  
-   SET  
  
-   NAKŁADA SIĘ NA  
  
 Element predykatów (równości):  
  
-   INDIE  
  
## <a name="supported-combinations"></a>Obsługiwane kombinacje  
 W poniższej tabeli przedstawiono obsługiwane kombinacje operatorów porównania dla każdego rodzaju typu:  
  
|**Typ**|**=**<br /><br /> **\!=**|**GROUP BY**<br /><br /> **DISTINCT**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**<   <=**<br /><br /> **>   >=**|**ORDER BY**|**MA WARTOŚĆ NULL**<br /><br /> **NIE MA WARTOŚCI NULL**|  
|-|-|-|-|-|-|-|-|  
|Typ jednostki|REF<sup>1</sup>|Wszystkie właściwości<sup>2</sup>|Wszystkie właściwości<sup>2</sup>|Wszystkie właściwości<sup>2</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|REF<sup>1</sup>|  
|Typ złożony|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|Wiersz|Wszystkie właściwości<sup>4</sup>|Wszystkie właściwości<sup>4</sup>|Wszystkie właściwości<sup>4</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Wszystkie właściwości<sup>4</sup>|Throw<sup>3</sup>|  
|typ pierwotny|Właściwe dla dostawcy|Właściwe dla dostawcy|Właściwe dla dostawcy|Właściwe dla dostawcy|Właściwe dla dostawcy|Właściwe dla dostawcy|Właściwe dla dostawcy|  
|multiset|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|REF|Tak<sup>5</sup>|Tak<sup>5</sup>|Tak<sup>5</sup>|Tak<sup>5</sup>|throw|throw|Tak<sup>5</sup>|  
|Skojarzenie<br /><br /> — typ|Throw<sup>3</sup>|throw|throw|throw|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
  
 <sup>1</sup>odwołania do danej jednostki wystąpień typu są porównywane niejawnie, jak pokazano w poniższym przykładzie:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Wystąpienie jednostki nie można porównać do jawnego odwołania. Jeśli to jest podejmowana próba jest zgłaszany wyjątek. Na przykład następujące zapytanie spowoduje zgłoszenie wyjątku:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup>właściwości typy złożone są spłaszczone przed wysłaniem do magazynu, dzięki czemu staną się porównywalne (tak długo, jak ich właściwości są porównywalne). Zobacz też <sup>4.</sup>  
  
 <sup>3</sup>środowisko uruchomieniowe programu Entity Framework wykrywa nieobsługiwane przypadku i istotnych wyjątek bez angażowania dostawcy/magazynowania.  
  
 <sup>4</sup>zostanie podjęta próba, aby porównać wszystkie właściwości. Jeśli jest właściwością, która jest typu innego niż porównywalne, takich jak text, ntext lub image, może zostać wygenerowany wyjątek serwera.  
  
 <sup>5</sup>wszystkie poszczególne elementy odniesienia są porównywane (obejmuje to nazwa zestawu jednostek i wszystkich właściwości klucza typu jednostki).  
  
## <a name="see-also"></a>Zobacz także
- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
