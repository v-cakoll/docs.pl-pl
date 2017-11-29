---
title: Metody System.Convert
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7f4ed9cc6ae4668fe978b0e7f685e360f1044e6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="systemconvert-methods"></a><span data-ttu-id="a931f-102">Metody System.Convert</span><span class="sxs-lookup"><span data-stu-id="a931f-102">System.Convert Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a931f-103">nie obsługuje następujących <xref:System.Convert> metody.</span><span class="sxs-lookup"><span data-stu-id="a931f-103"> does not support the following <xref:System.Convert> methods.</span></span>  
  
-   <span data-ttu-id="a931f-104">Wersje z <xref:System.IFormatProvider> parametru.</span><span class="sxs-lookup"><span data-stu-id="a931f-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>  
  
-   <span data-ttu-id="a931f-105">Metody, które wymagają znaków lub tablice typu byte:</span><span class="sxs-lookup"><span data-stu-id="a931f-105">Methods that involve char arrays or byte arrays:</span></span>  
  
    -   <xref:System.Convert.FromBase64CharArray%2A>  
  
    -   <xref:System.Convert.ToBase64CharArray%2A>  
  
    -   <xref:System.Convert.FromBase64String%2A>  
  
    -   <xref:System.Convert.ToBase64String%2A>  
  
-   <span data-ttu-id="a931f-106">Następujących metod:</span><span class="sxs-lookup"><span data-stu-id="a931f-106">The following methods:</span></span>  
  
    -   <span data-ttu-id="a931f-107">`public static <Type2> To<Type2>(<Type1> value);`gdzie</span><span class="sxs-lookup"><span data-stu-id="a931f-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>  
  
         <span data-ttu-id="a931f-108">`Type1`i `Type2` są każdego `sbyte`, `uint`, `ulong`, lub `ushort`.</span><span class="sxs-lookup"><span data-stu-id="a931f-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>  
  
    -   <span data-ttu-id="a931f-109">C#:</span><span class="sxs-lookup"><span data-stu-id="a931f-109">C#:</span></span>  
  
         `int To<int type>(string value, int fromBase),`  
  
         `ToString(... value, int toBase)`  
  
    -   <span data-ttu-id="a931f-110">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="a931f-110">Visual Basic:</span></span>  
  
         `Function To(Of [Numeric])(value as String, fromBase As Integer)`  
  
         `As [Numeric], ToString( value As …, toBase As Integer)`  
  
    -   <xref:System.Convert.IsDBNull%2A>  
  
    -   <xref:System.Convert.GetTypeCode%2A>  
  
    -   <xref:System.Convert.ChangeType%2A>  
  
## <a name="see-also"></a><span data-ttu-id="a931f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a931f-111">See Also</span></span>  
 [<span data-ttu-id="a931f-112">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="a931f-112">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
