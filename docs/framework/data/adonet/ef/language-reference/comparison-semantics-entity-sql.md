---
title: Semantyka porównania (entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 57d81d4b581df76a4382ad5e1d72fe8250b10d43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150457"
---
# <a name="comparison-semantics-entity-sql"></a>Semantyka porównania (entity SQL)
Wykonywanie dowolnego z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] następujących operatorów obejmuje porównanie wystąpień typu:  
  
## <a name="explicit-comparison"></a>Jawne porównanie  
 Operacje równości:  
  
- =  
  
- !=  
  
 Operacje zamawiania:  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 Operacje anulowania:  
  
- MA WARTOŚĆ NULL  
  
- NIE MA WARTOŚCI NULL  
  
## <a name="explicit-distinction"></a>Wyraźne rozróżnienie  
 Rozróżnienie równości:  
  
- DISTINCT  
  
- GROUP BY  
  
 Wyróżnienie zamawiania:  
  
- ORDER BY  
  
## <a name="implicit-distinction"></a>Niejawne rozróżnienie  
 Ustaw operacje i predykaty (równość):  
  
- UNION  
  
- INTERSECT  
  
- EXCEPT  
  
- SET  
  
- OVERLAPS  
  
 Predykaty pozycji (równość):  
  
- IN  
  
## <a name="supported-combinations"></a>Obsługiwane kombinacje  
 W poniższej tabeli przedstawiono wszystkie obsługiwane kombinacje operatorów porównania dla każdego rodzaju typu:  
  
|**Typ**|**=**<br /><br /> **!=**|**GROUP BY**<br /><br /> **Odrębne**|**Unii**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **Ustawić**<br /><br /> **OVERLAPS**|**IN**|**< <=**<br /><br /> **> >=**|**ORDER BY**|**MA WARTOŚĆ NULL**<br /><br /> **NIE MA WARTOŚCI NULL**|  
|-|-|-|-|-|-|-|-|  
|Typ jednostki|Ref<sup>1</sup>|Wszystkie właściwości<sup>2</sup>|Wszystkie właściwości<sup>2</sup>|Wszystkie właściwości<sup>2</sup>|Rzut<sup>3</sup>|Rzut<sup>3</sup>|Ref<sup>1</sup>|  
|Typ złożony|Rzut<sup>3</sup>|Rzut<sup>3</sup>|Rzut<sup>3</sup>|Rzut<sup>3</sup>|Rzut<sup>3</sup>|Rzut<sup>3</sup>|Rzut<sup>3</sup>|  
|Wiersz|Wszystkie właściwości<sup>4</sup>|Wszystkie właściwości<sup>4</sup>|Wszystkie właściwości<sup>4</sup>|Rzut<sup>3</sup>|Rzut<sup>3</sup>|Wszystkie właściwości<sup>4</sup>|Rzut<sup>3</sup>|  
|Typ pierwotny|Specyficzne dla dostawcy|Specyficzne dla dostawcy|Specyficzne dla dostawcy|Specyficzne dla dostawcy|Specyficzne dla dostawcy|Specyficzne dla dostawcy|Specyficzne dla dostawcy|  
|Zestaw wielokrotny|Rzut<sup>3</sup>|Rzut<sup>3</sup>|Rzut<sup>3</sup>|Rzut<sup>3</sup>|Rzut<sup>3</sup>|Rzut<sup>3</sup>|Rzut<sup>3</sup>|  
|Ref|Tak<sup>5</sup>|Tak<sup>5</sup>|Tak<sup>5</sup>|Tak<sup>5</sup>|Throw|Throw|Tak<sup>5</sup>|  
|Stowarzyszenia<br /><br /> type|Rzut<sup>3</sup>|Throw|Throw|Throw|Rzut<sup>3</sup>|Rzut<sup>3</sup>|Rzut<sup>3</sup>|  
  
 <sup>1.</sup> Odwołania do wystąpienia danego typu jednostki są niejawnie porównywane, jak pokazano w poniższym przykładzie:  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Nie można porównać wystąpienia jednostki z jawnym odwołaniem. W przypadku podjęcia tej próby zostanie zgłoszony wyjątek. Na przykład następująca kwerenda zda wyjątek:  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <sup>2.</sup> Właściwości typów złożonych są spłaszczane przed wysłaniem do magazynu, więc stają się porównywalne (o ile wszystkie ich właściwości są porównywalne). Zobacz także <sup>4.</sup>  
  
 <sup>3</sup> Środowisko uruchomieniowe entity framework wykrywa nieobsługiwał przypadek i zgłasza znaczący wyjątek bez angażowania dostawcy/magazynu.  
  
 <sup>4</sup> Podejmowana jest próba porównania wszystkich właściwości. Jeśli istnieje właściwość, która jest typu niesymady, takich jak tekst, ntext lub obraz, może zostać zgłoszony wyjątek serwera.  
  
 <sup>5</sup> Wszystkie poszczególne elementy odwołań są porównywane (obejmuje to nazwę zestawu jednostek i wszystkie kluczowe właściwości typu jednostki).  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie jednostki SQL](entity-sql-overview.md)
