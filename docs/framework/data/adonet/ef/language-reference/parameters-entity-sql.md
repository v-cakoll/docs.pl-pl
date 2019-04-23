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
# <a name="parameters-entity-sql"></a><span data-ttu-id="c8de6-102">Parametry (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="c8de6-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="c8de6-103">Parametry są zmienne, które są zdefiniowane poza [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zwykle za pomocą API powiązania, który jest używany przez języka hosta.</span><span class="sxs-lookup"><span data-stu-id="c8de6-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="c8de6-104">Każdy parametr ma nazwy i typu.</span><span class="sxs-lookup"><span data-stu-id="c8de6-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="c8de6-105">Nazwy parametrów są zdefiniowane w wyrażeniach zapytań za pomocą u (@) symbol jako prefiksu.</span><span class="sxs-lookup"><span data-stu-id="c8de6-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="c8de6-106">To pozwala odróżnić od siebie je z nazwy właściwości lub innych nazw, które są zdefiniowane w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="c8de6-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="c8de6-107">Interfejs API języka hosta powiązania udostępnia interfejsy API dla wiązania parametrów.</span><span class="sxs-lookup"><span data-stu-id="c8de6-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8de6-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8de6-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8de6-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8de6-109">See also</span></span>

- [<span data-ttu-id="c8de6-110">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c8de6-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="c8de6-111">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c8de6-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
