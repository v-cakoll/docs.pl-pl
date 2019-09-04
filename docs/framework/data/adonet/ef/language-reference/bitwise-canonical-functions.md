---
title: Funkcje bitowe Canonical
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: 3c1f32acc7a035658198b807646c1ceb95dfed0b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251300"
---
# <a name="bitwise-canonical-functions"></a>Funkcje bitowe Canonical
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]zawiera bitowe funkcje kanoniczne.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono bitowe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje kanoniczne. Te funkcje będą zwracać `Null` , `Null` Jeśli dane wejściowe zostaną dostarczone. Zwracany typ funkcji jest taki sam jak typ argumentu (s). Argumenty muszą być tego samego typu, jeśli funkcja przyjmuje więcej niż jeden argument. Aby wykonywać operacje bitowe w różnych typach, należy jawnie rzutować na ten sam typ.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|Zwraca koniunkcję bitową `value1` typu `value2` `value1` `value2`i.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, ,`Int32`i .`Int64`<br /><br /> **Przykład**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|Zwraca bitową negację `value`.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, ,`Int32`i .`Int64`<br /><br /> **Przykład**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|Zwraca bitowe `value1` rozłączenie i `value2` jako typ `value1` i `value2`.<br /><br /> **Argumenty**<br /><br /> A `Byte` ,`Int16` i`Int64`. `Int32`<br /><br /> **Przykład**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|`value1` Zwraca bitowe, wyłączne rozłączenie i `value2` jako typ `value1` i `value2`.<br /><br /> **Argumenty**<br /><br /> A `Byte` ,`Int16` i`Int64`. `Int32`<br /><br /> **Przykład**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje Canonical](canonical-functions.md)
