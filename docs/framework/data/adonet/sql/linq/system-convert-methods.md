---
title: System.Convert, metody
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: d0aa0b11223e23b874471962d727d8e16e152ceb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781062"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="6d525-102">System.Convert, metody</span><span class="sxs-lookup"><span data-stu-id="6d525-102">System.Convert Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6d525-103">Program nie obsługuje następujących <xref:System.Convert> metod.</span><span class="sxs-lookup"><span data-stu-id="6d525-103">does not support the following <xref:System.Convert> methods.</span></span>

- <span data-ttu-id="6d525-104">Wersje z <xref:System.IFormatProvider> parametrem.</span><span class="sxs-lookup"><span data-stu-id="6d525-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>

- <span data-ttu-id="6d525-105">Metody, które obejmują tablice char lub tablice bajtowe:</span><span class="sxs-lookup"><span data-stu-id="6d525-105">Methods that involve char arrays or byte arrays:</span></span>

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- <span data-ttu-id="6d525-106">Następujące metody:</span><span class="sxs-lookup"><span data-stu-id="6d525-106">The following methods:</span></span>

  - <span data-ttu-id="6d525-107">`public static <Type2> To<Type2>(<Type1> value);`miejscu</span><span class="sxs-lookup"><span data-stu-id="6d525-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>

    <span data-ttu-id="6d525-108">`Type1`i `Type2` są każdym z `sbyte`nich, `uint`, `ulong`, lub `ushort`.</span><span class="sxs-lookup"><span data-stu-id="6d525-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>

  - <span data-ttu-id="6d525-109">C#:</span><span class="sxs-lookup"><span data-stu-id="6d525-109">C#:</span></span>

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - <span data-ttu-id="6d525-110">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="6d525-110">Visual Basic:</span></span>

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a><span data-ttu-id="6d525-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d525-111">See also</span></span>

- [<span data-ttu-id="6d525-112">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="6d525-112">Data Types and Functions</span></span>](data-types-and-functions.md)
