---
title: System.Convert Methods
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: c3b8c7105578c57547b79bc95b633bcc6449a0ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591724"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="ffdf2-102">System.Convert Methods</span><span class="sxs-lookup"><span data-stu-id="ffdf2-102">System.Convert Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ffdf2-103">nie obsługuje następujących <xref:System.Convert> metody.</span><span class="sxs-lookup"><span data-stu-id="ffdf2-103">does not support the following <xref:System.Convert> methods.</span></span>  
  
-   <span data-ttu-id="ffdf2-104">Wersje <xref:System.IFormatProvider> parametru.</span><span class="sxs-lookup"><span data-stu-id="ffdf2-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>  
  
-   <span data-ttu-id="ffdf2-105">Metody, które obejmują char tablic lub tablice typu byte:</span><span class="sxs-lookup"><span data-stu-id="ffdf2-105">Methods that involve char arrays or byte arrays:</span></span>  
  
    -   <xref:System.Convert.FromBase64CharArray%2A>  
  
    -   <xref:System.Convert.ToBase64CharArray%2A>  
  
    -   <xref:System.Convert.FromBase64String%2A>  
  
    -   <xref:System.Convert.ToBase64String%2A>  
  
-   <span data-ttu-id="ffdf2-106">Następujących metod:</span><span class="sxs-lookup"><span data-stu-id="ffdf2-106">The following methods:</span></span>  
  
    -   <span data-ttu-id="ffdf2-107">`public static <Type2> To<Type2>(<Type1> value);` gdzie</span><span class="sxs-lookup"><span data-stu-id="ffdf2-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>  
  
         <span data-ttu-id="ffdf2-108">`Type1` i `Type2` są każdego `sbyte`, `uint`, `ulong`, lub `ushort`.</span><span class="sxs-lookup"><span data-stu-id="ffdf2-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>  
  
    -   <span data-ttu-id="ffdf2-109">C#:</span><span class="sxs-lookup"><span data-stu-id="ffdf2-109">C#:</span></span>  
  
         `int To<int type>(string value, int fromBase),`  
  
         `ToString(... value, int toBase)`  
  
    -   <span data-ttu-id="ffdf2-110">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="ffdf2-110">Visual Basic:</span></span>  
  
         `Function To(Of [Numeric])(value as String, fromBase As Integer)`  
  
         `As [Numeric], ToString( value As …, toBase As Integer)`  
  
    -   <xref:System.Convert.IsDBNull%2A>  
  
    -   <xref:System.Convert.GetTypeCode%2A>  
  
    -   <xref:System.Convert.ChangeType%2A>  
  
## <a name="see-also"></a><span data-ttu-id="ffdf2-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffdf2-111">See also</span></span>
- [<span data-ttu-id="ffdf2-112">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="ffdf2-112">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
