---
title: Parametry (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2a3700b5f9bdc996b147609d86bcaed0ec0bb116
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="parameters-entity-sql"></a>Parametry (jednostka SQL)
Parametry są zmienne, które są zdefiniowane poza [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zwykle za pomocą interfejsu API powiązania, który jest używany przez języka hosta. Każdy parametr ma nazwę i typ. Nazwy parametrów zdefiniowanych w wyrażeniach zapytań z na (@) symbol jako prefiksu. To pozwala odróżnić od siebie je z nazwy właściwości lub inne nazwy, które są zdefiniowane w zapytaniu.  
  
 Interfejs API powiązanie języka hosta udostępnia interfejsy API dla wiązania parametrów.  
  
## <a name="example"></a>Przykład  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Omówienie SQL jednostki](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
