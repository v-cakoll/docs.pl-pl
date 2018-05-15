---
title: Metody System.Convert
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: a16839bf64d5786caa6feb557333fe93c66edc3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="systemconvert-methods"></a><span data-ttu-id="79714-102">Metody System.Convert</span><span class="sxs-lookup"><span data-stu-id="79714-102">System.Convert Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="79714-103"> nie obsługuje następujących <xref:System.Convert> metody.</span><span class="sxs-lookup"><span data-stu-id="79714-103"> does not support the following <xref:System.Convert> methods.</span></span>  
  
-   <span data-ttu-id="79714-104">Wersje z <xref:System.IFormatProvider> parametru.</span><span class="sxs-lookup"><span data-stu-id="79714-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>  
  
-   <span data-ttu-id="79714-105">Metody, które wymagają znaków lub tablice typu byte:</span><span class="sxs-lookup"><span data-stu-id="79714-105">Methods that involve char arrays or byte arrays:</span></span>  
  
    -   <xref:System.Convert.FromBase64CharArray%2A>  
  
    -   <xref:System.Convert.ToBase64CharArray%2A>  
  
    -   <xref:System.Convert.FromBase64String%2A>  
  
    -   <xref:System.Convert.ToBase64String%2A>  
  
-   <span data-ttu-id="79714-106">Następujących metod:</span><span class="sxs-lookup"><span data-stu-id="79714-106">The following methods:</span></span>  
  
    -   <span data-ttu-id="79714-107">`public static <Type2> To<Type2>(<Type1> value);` gdzie</span><span class="sxs-lookup"><span data-stu-id="79714-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>  
  
         <span data-ttu-id="79714-108">`Type1` i `Type2` są każdego `sbyte`, `uint`, `ulong`, lub `ushort`.</span><span class="sxs-lookup"><span data-stu-id="79714-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>  
  
    -   <span data-ttu-id="79714-109">C#:</span><span class="sxs-lookup"><span data-stu-id="79714-109">C#:</span></span>  
  
         `int To<int type>(string value, int fromBase),`  
  
         `ToString(... value, int toBase)`  
  
    -   <span data-ttu-id="79714-110">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="79714-110">Visual Basic:</span></span>  
  
         `Function To(Of [Numeric])(value as String, fromBase As Integer)`  
  
         `As [Numeric], ToString( value As …, toBase As Integer)`  
  
    -   <xref:System.Convert.IsDBNull%2A>  
  
    -   <xref:System.Convert.GetTypeCode%2A>  
  
    -   <xref:System.Convert.ChangeType%2A>  
  
## <a name="see-also"></a><span data-ttu-id="79714-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79714-111">See Also</span></span>  
 [<span data-ttu-id="79714-112">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="79714-112">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
