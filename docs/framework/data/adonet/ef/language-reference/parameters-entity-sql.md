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
# <a name="parameters-entity-sql"></a><span data-ttu-id="40053-102">Parametry (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="40053-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="40053-103">Parametry są zmienne, które są zdefiniowane poza [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zwykle za pomocą interfejsu API powiązania, który jest używany przez języka hosta.</span><span class="sxs-lookup"><span data-stu-id="40053-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="40053-104">Każdy parametr ma nazwę i typ.</span><span class="sxs-lookup"><span data-stu-id="40053-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="40053-105">Nazwy parametrów zdefiniowanych w wyrażeniach zapytań z na (@) symbol jako prefiksu.</span><span class="sxs-lookup"><span data-stu-id="40053-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="40053-106">To pozwala odróżnić od siebie je z nazwy właściwości lub inne nazwy, które są zdefiniowane w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="40053-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="40053-107">Interfejs API powiązanie języka hosta udostępnia interfejsy API dla wiązania parametrów.</span><span class="sxs-lookup"><span data-stu-id="40053-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40053-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="40053-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="40053-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40053-109">See Also</span></span>  
 [<span data-ttu-id="40053-110">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="40053-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="40053-111">Omówienie SQL jednostki</span><span class="sxs-lookup"><span data-stu-id="40053-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
