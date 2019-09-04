---
title: Semantyka porównania (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: da7b8f662d10376abd649e674701b43b7b740a6f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251179"
---
# <a name="comparison-semantics-entity-sql"></a>Semantyka porównania (Entity SQL)
Wykonywanie któregokolwiek z następujących [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów obejmuje porównanie wystąpień typu:  
  
## <a name="explicit-comparison"></a>Jawne porównanie  
 Operacje równości:  
  
- =  
  
- !=  
  
 Operacje porządkowania:  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 Operacje dopuszczania wartości null:  
  
- MA WARTOŚĆ NULL  
  
- NIE MA WARTOŚCI NULL  
  
## <a name="explicit-distinction"></a>Jawne rozróżnienie  
 Rozróżnienie równości:  
  
- ITP  
  
- GROUP BY  
  
 Kolejność rozróżniania:  
  
- ORDER BY  
  
## <a name="implicit-distinction"></a>Niejawne rozróżnienie  
 Ustaw operacje i predykaty (równość):  
  
- UNION  
  
- INTERSECT  
  
- EXCEPT  
  
- SET  
  
- OVERLAPS  
  
 Predykaty elementów (równość):  
  
- IN  
  
## <a name="supported-combinations"></a>Obsługiwane kombinacje  
 W poniższej tabeli przedstawiono wszystkie obsługiwane kombinacje operatorów porównania dla każdego rodzaju typu:  
  
|**Typ**|**=**<br /><br /> **\!=**|**GROUP BY**<br /><br /> **ITP**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**<   <=**<br /><br /> **>   >=**|**ORDER BY**|**MA WARTOŚĆ NULL**<br /><br /> **NIE MA WARTOŚCI NULL**|  
|-|-|-|-|-|-|-|-|  
|Typ jednostki|Odwołanie<sup>1</sup>|Wszystkie właściwości<sup>2</sup>|Wszystkie właściwości<sup>2</sup>|Wszystkie właściwości<sup>2</sup>|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|Odwołanie<sup>1</sup>|  
|Typ złożony|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|  
|Wiersz|Wszystkie właściwości<sup>4</sup>|Wszystkie właściwości<sup>4</sup>|Wszystkie właściwości<sup>4</sup>|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|Wszystkie właściwości<sup>4</sup>|Zgłoś<sup>3</sup>|  
|Typ pierwotny|Specyficzne dla dostawcy|Specyficzne dla dostawcy|Specyficzne dla dostawcy|Specyficzne dla dostawcy|Specyficzne dla dostawcy|Specyficzne dla dostawcy|Specyficzne dla dostawcy|  
|Multiset|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|  
|Umieszczone|Tak<sup>5</sup>|Tak<sup>5</sup>|Tak<sup>5</sup>|Tak<sup>5</sup>|Throw|Throw|Tak<sup>5</sup>|  
|Skojarzenie<br /><br /> — typ|Zgłoś<sup>3</sup>|Throw|Throw|Throw|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|Zgłoś<sup>3</sup>|  
  
 <sup>1</sup> Odwołania do danego wystąpienia typu jednostki są niejawnie porównywane, jak pokazano w następującym przykładzie:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Nie można porównać wystąpienia jednostki z jawnym odwołaniem. Jeśli zostanie podjęta taka próba, zostanie zgłoszony wyjątek. Na przykład następujące zapytanie spowoduje zgłoszenie wyjątku:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup> Właściwości typów złożonych są spłaszczane przed wysłaniem do magazynu, dzięki czemu stają się one porównywalne (o ile wszystkie ich właściwości są porównywalne). Zobacz też <sup>4.</sup>  
  
 <sup>3</sup> Środowisko uruchomieniowe Entity Framework wykrywa nieobsługiwany przypadek i zgłasza znaczący wyjątek bez angażowania dostawcy/magazynu.  
  
 <sup>4</sup> Podjęto próbę porównania wszystkich właściwości. Jeśli istnieje właściwość, której typ nie jest porównywalny, taki jak text, ntext lub Image, może zostać zgłoszony wyjątek serwera.  
  
 <sup>5</sup> Wszystkie poszczególne elementy odwołań są porównywane (obejmuje to nazwę zestawu jednostek i wszystkie właściwości klucza typu jednostki).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
