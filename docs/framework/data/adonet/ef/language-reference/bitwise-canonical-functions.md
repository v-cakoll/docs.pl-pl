---
title: Bitowe or funkcje Canonical
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: 882ecd2e82c64981dd76b3c860711433293145b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742275"
---
# <a name="bitwise-canonical-functions"></a>Bitowe or funkcje Canonical
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] obejmuje funkcje canonical bitowe.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono operatora testu koniunkcji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje canonical. Te funkcje zwrócą `Null` Jeśli `Null` znajduje się dane wejściowe. Zwracany typ funkcji jest taka sama jak typy argumentów. Argumenty muszą być tego samego typu, jeśli funkcja przyjmuje więcej niż jeden argument. Aby wykonać operacje bitowe na różnych urządzeniach, należy rzutować na ten sam typ. jawne.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|Zwraca koniunkcję bitową programu `value1` i `value2` jako typ `value1` i `value2`.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, `Int32`, i `Int64`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|Zwraca wartość logiczną negację `value`.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, `Int32`, i `Int64`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|Zwraca sumę bitową programu `value1` i `value2` jako typ `value1` i `value2`.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, `Int32` i `Int64`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|Zwraca bitowego rozłączenia wyłączny z `value1` i `value2` jako typ `value1` i `value2`.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, `Int32` i `Int64`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>Zobacz także
- [Funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
