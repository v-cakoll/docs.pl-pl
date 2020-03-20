---
title: Parametry (entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: e1bb633f7f7c7908a5f424991f20a5cd89aee5aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150017"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="dd205-102">Parametry (entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dd205-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="dd205-103">Parametry są zmienne, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]które są zdefiniowane na zewnątrz, zwykle za pośrednictwem powiązania interfejsu API, który jest używany przez język hosta.</span><span class="sxs-lookup"><span data-stu-id="dd205-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="dd205-104">Każdy parametr ma nazwę i typ.</span><span class="sxs-lookup"><span data-stu-id="dd205-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="dd205-105">Nazwy parametrów są definiowane w wyrażeniach kwerendy z symbolem at (@) jako prefiksem.</span><span class="sxs-lookup"><span data-stu-id="dd205-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="dd205-106">To odróżnia je od nazw właściwości lub innych nazw, które są zdefiniowane w kwerendzie.</span><span class="sxs-lookup"><span data-stu-id="dd205-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="dd205-107">Interfejs API powiązania języka hosta udostępnia interfejsy API dla parametrów powiązania.</span><span class="sxs-lookup"><span data-stu-id="dd205-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd205-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="dd205-108">Example</span></span>  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd205-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd205-109">See also</span></span>

- [<span data-ttu-id="dd205-110">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="dd205-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="dd205-111">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="dd205-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
