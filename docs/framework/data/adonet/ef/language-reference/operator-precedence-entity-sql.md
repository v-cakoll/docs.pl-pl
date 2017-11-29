---
title: "Kolejność wykonywania działań (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 484eedffeaffb625cd43352dadedb8c99fbc65ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="operator-precedence-entity-sql"></a>Kolejność wykonywania działań (jednostka SQL)
Gdy [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania ma wiele operatorów, kolejność określa kolejność, w którym wykonywane są operacje. Kolejność wykonywania mogą znacznie wpływać na wynik zapytania.  
  
 Operatory ma poziomów pierwszeństwo przed, pokazano w poniższej tabeli. Operator o wyższym poziomie jest oceniane przed operatorem o niższym poziomie.  
  
|Poziom|Typ operacji|Operator|  
|-----------|--------------------|--------------|  
|1|podstawowy|`. , [] ()`|  
|2|Jednoargumentowe|`! not`|  
|3|Mnożenia|`* / %`|  
|4|Dodatku|`+ -`|  
|5|Szeregowanie|`< > <= >=`|  
|6|Równość|`= != <>`|  
|7|AND warunkowe|`and &&`|  
|8|OR warunkowe|`or &#124;&#124;`|  
  
 Po dwóch operatorów w wyrażeniu mają ten sam poziom pierwszeństwa operatora, ich są wykonywane od lewej do prawej, na podstawie ich położenia w zapytaniu. Na przykład `x+y-z` jest szacowana jako `(x+y)-z`.  
  
 Można użyć nawiasów do zastąpienia zdefiniowane pierwszeństwo operatorów w zapytaniu. Wszystkie elementy wewnątrz nawiasów oceny najpierw umożliwiające uzyskanie pojedynczego wyniku przed, czy wynik mogą być używane przez każdy podmiot poza nawiasów. Na przykład `x+y*z` mnoży `y` przez `z` , a następnie dodaje `x`, ale `(x+y)*z` dodaje `x` do `y` , a następnie mnoży wynik przez `z`.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie SQL jednostki](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
