---
title: Parametry (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 723e40f523f8bb573e0ffcb1863ed0c082ea9d8d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249586"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="f418a-102">Parametry (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f418a-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="f418a-103">Parametry są zmiennymi, które są [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zdefiniowane poza, zwykle za pomocą powiązania interfejsu API, który jest używany przez język hosta.</span><span class="sxs-lookup"><span data-stu-id="f418a-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="f418a-104">Każdy parametr ma nazwę i typ.</span><span class="sxs-lookup"><span data-stu-id="f418a-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="f418a-105">Nazwy parametrów są zdefiniowane w wyrażeniach zapytania z symbolem at (@) jako prefiksem.</span><span class="sxs-lookup"><span data-stu-id="f418a-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="f418a-106">Pozwala to odróżnić je od nazw właściwości lub innych nazw zdefiniowanych w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="f418a-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="f418a-107">Interfejs API powiązania języka hosta udostępnia interfejsy API dla parametrów powiązań.</span><span class="sxs-lookup"><span data-stu-id="f418a-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f418a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="f418a-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="f418a-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f418a-109">See also</span></span>

- [<span data-ttu-id="f418a-110">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f418a-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f418a-111">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f418a-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
