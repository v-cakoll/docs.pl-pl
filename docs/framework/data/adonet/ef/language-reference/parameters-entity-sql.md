---
title: Parametry (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 5fa050e43e4590f61c3011a1b9bb0937da7032a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632390"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="fc91c-102">Parametry (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="fc91c-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="fc91c-103">Parametry są zmienne, które są zdefiniowane poza [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zwykle za pomocą API powiązania, który jest używany przez języka hosta.</span><span class="sxs-lookup"><span data-stu-id="fc91c-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="fc91c-104">Każdy parametr ma nazwy i typu.</span><span class="sxs-lookup"><span data-stu-id="fc91c-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="fc91c-105">Nazwy parametrów są zdefiniowane w wyrażeniach zapytań za pomocą u (@) symbol jako prefiksu.</span><span class="sxs-lookup"><span data-stu-id="fc91c-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="fc91c-106">To pozwala odróżnić od siebie je z nazwy właściwości lub innych nazw, które są zdefiniowane w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="fc91c-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="fc91c-107">Interfejs API języka hosta powiązania udostępnia interfejsy API dla wiązania parametrów.</span><span class="sxs-lookup"><span data-stu-id="fc91c-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc91c-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc91c-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc91c-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc91c-109">See also</span></span>
- [<span data-ttu-id="fc91c-110">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="fc91c-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="fc91c-111">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="fc91c-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
