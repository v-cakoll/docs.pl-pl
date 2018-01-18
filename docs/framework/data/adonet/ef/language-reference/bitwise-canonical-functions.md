---
title: Operator kanonicznej funkcji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1d703b2467d508324f3eb39b822c239484ac1c6e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="bitwise-canonical-functions"></a>Operator kanonicznej funkcji
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]obejmuje funkcje canonical bitowe.  
  
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
