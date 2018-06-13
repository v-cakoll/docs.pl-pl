---
title: Parametry (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: c8bdb54e52b4c0d189f3bff72bdb24785c1a9c27
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765077"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="f8914-102">Parametry (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="f8914-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="f8914-103">Parametry są zmienne, które są zdefiniowane poza [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zwykle za pomocą interfejsu API powiązania, który jest używany przez języka hosta.</span><span class="sxs-lookup"><span data-stu-id="f8914-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="f8914-104">Każdy parametr ma nazwę i typ.</span><span class="sxs-lookup"><span data-stu-id="f8914-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="f8914-105">Nazwy parametrów zdefiniowanych w wyrażeniach zapytań z na (@) symbol jako prefiksu.</span><span class="sxs-lookup"><span data-stu-id="f8914-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="f8914-106">To pozwala odróżnić od siebie je z nazwy właściwości lub inne nazwy, które są zdefiniowane w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="f8914-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="f8914-107">Interfejs API powiązanie języka hosta udostępnia interfejsy API dla wiązania parametrów.</span><span class="sxs-lookup"><span data-stu-id="f8914-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8914-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8914-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8914-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8914-109">See Also</span></span>  
 [<span data-ttu-id="f8914-110">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f8914-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="f8914-111">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f8914-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
