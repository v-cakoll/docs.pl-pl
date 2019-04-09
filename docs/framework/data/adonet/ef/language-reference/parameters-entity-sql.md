---
title: Parametry (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 47a1514933904daa623adc151d50525f011e07a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187678"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="51367-102">Parametry (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="51367-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="51367-103">Parametry są zmienne, które są zdefiniowane poza [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zwykle za pomocą API powiązania, który jest używany przez języka hosta.</span><span class="sxs-lookup"><span data-stu-id="51367-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="51367-104">Każdy parametr ma nazwy i typu.</span><span class="sxs-lookup"><span data-stu-id="51367-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="51367-105">Nazwy parametrów są zdefiniowane w wyrażeniach zapytań za pomocą u (@) symbol jako prefiksu.</span><span class="sxs-lookup"><span data-stu-id="51367-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="51367-106">To pozwala odróżnić od siebie je z nazwy właściwości lub innych nazw, które są zdefiniowane w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="51367-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="51367-107">Interfejs API języka hosta powiązania udostępnia interfejsy API dla wiązania parametrów.</span><span class="sxs-lookup"><span data-stu-id="51367-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51367-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="51367-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="51367-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51367-109">See also</span></span>

- [<span data-ttu-id="51367-110">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="51367-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="51367-111">Przegląd języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="51367-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
