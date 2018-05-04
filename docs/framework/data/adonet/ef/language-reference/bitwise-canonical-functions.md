---
title: Operator kanonicznej funkcji
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: df3b81a47b8e1202884a5c38f55c7061279b245f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="bitwise-canonical-functions"></a>Operator kanonicznej funkcji
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] obejmuje funkcje canonical bitowe.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono operatora testu koniunkcji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji. Te funkcje będą zwracać `Null` Jeśli `Null` danych wejściowych jest dostępne. Zwracany typ funkcji jest taka sama jak typy argumentów. Argumenty muszą być tego samego typu, jeśli funkcja przyjmuje więcej niż jeden argument. Aby wykonać operacje bitowe na różnych urządzeniach, należy rzutować na ten sam typ. jawne.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|Zwraca koniunkcję z `value1` i `value2` jako typ `value1` i `value2`.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, `Int32`, i `Int64`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|Zwraca wartość logiczną negację `value`.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, `Int32`, i `Int64`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|Zwraca z bitowego rozłączenia z `value1` i `value2` jako typ `value1` i `value2`.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, `Int32` i `Int64`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|Zwraca z bitowego rozłączenia wyłącznego z `value1` i `value2` jako typ `value1` i `value2`.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, `Int32` i `Int64`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
