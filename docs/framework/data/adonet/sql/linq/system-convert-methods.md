---
title: System.Convert, metody
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: 9836820f2c084a80fcc0a4856f20597716344dfd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877035"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="31762-102">System.Convert, metody</span><span class="sxs-lookup"><span data-stu-id="31762-102">System.Convert Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="31762-103">nie obsługuje następujących <xref:System.Convert> metody.</span><span class="sxs-lookup"><span data-stu-id="31762-103">does not support the following <xref:System.Convert> methods.</span></span>

- <span data-ttu-id="31762-104">Wersje <xref:System.IFormatProvider> parametru.</span><span class="sxs-lookup"><span data-stu-id="31762-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>

- <span data-ttu-id="31762-105">Metody, które obejmują char tablic lub tablice typu byte:</span><span class="sxs-lookup"><span data-stu-id="31762-105">Methods that involve char arrays or byte arrays:</span></span>

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- <span data-ttu-id="31762-106">Następujących metod:</span><span class="sxs-lookup"><span data-stu-id="31762-106">The following methods:</span></span>

  - <span data-ttu-id="31762-107">`public static <Type2> To<Type2>(<Type1> value);` gdzie</span><span class="sxs-lookup"><span data-stu-id="31762-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>

    <span data-ttu-id="31762-108">`Type1` i `Type2` są każdego `sbyte`, `uint`, `ulong`, lub `ushort`.</span><span class="sxs-lookup"><span data-stu-id="31762-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>

  - <span data-ttu-id="31762-109">C#:</span><span class="sxs-lookup"><span data-stu-id="31762-109">C#:</span></span>

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - <span data-ttu-id="31762-110">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="31762-110">Visual Basic:</span></span>

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a><span data-ttu-id="31762-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31762-111">See also</span></span>

- [<span data-ttu-id="31762-112">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="31762-112">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
