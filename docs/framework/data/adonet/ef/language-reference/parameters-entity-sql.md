---
title: Parametry (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 47a1514933904daa623adc151d50525f011e07a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187678"
---
# <a name="parameters-entity-sql"></a>Parametry (jednostka SQL)
Parametry są zmienne, które są zdefiniowane poza [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zwykle za pomocą API powiązania, który jest używany przez języka hosta. Każdy parametr ma nazwy i typu. Nazwy parametrów są zdefiniowane w wyrażeniach zapytań za pomocą u (@) symbol jako prefiksu. To pozwala odróżnić od siebie je z nazwy właściwości lub innych nazw, które są zdefiniowane w zapytaniu.  
  
 Interfejs API języka hosta powiązania udostępnia interfejsy API dla wiązania parametrów.  
  
## <a name="example"></a>Przykład  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
