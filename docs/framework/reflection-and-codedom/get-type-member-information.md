---
title: 'Instrukcje: Uzyskiwanie informacji o typie i elemencie członkowskim za pomocą odbicia'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: da71845ea276267220636cfd661465ea02b2b50d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972922"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="527a0-102">Instrukcje: Uzyskiwanie informacji o typie i elemencie członkowskim za pomocą odbicia</span><span class="sxs-lookup"><span data-stu-id="527a0-102">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="527a0-103"><xref:System.Reflection> Przestrzeń nazw zawiera wiele metod uzyskiwania informacji na temat typów i ich członków.</span><span class="sxs-lookup"><span data-stu-id="527a0-103">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="527a0-104">W tym artykule przedstawiono jedną z tych metod <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="527a0-104">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="527a0-105">Aby uzyskać dodatkowe informacje, zobacz [Omówienie odbicia](reflection.md).</span><span class="sxs-lookup"><span data-stu-id="527a0-105">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="527a0-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="527a0-106">Example</span></span>

<span data-ttu-id="527a0-107">Poniższy przykład pobiera informacje o typie i elemencie członkowskim za pomocą odbicia:</span><span class="sxs-lookup"><span data-stu-id="527a0-107">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="527a0-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="527a0-108">See also</span></span>

- [<span data-ttu-id="527a0-109">Program z domenami aplikacji</span><span class="sxs-lookup"><span data-stu-id="527a0-109">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="527a0-110">Odbicie</span><span class="sxs-lookup"><span data-stu-id="527a0-110">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="527a0-111">Korzystanie z domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="527a0-111">Use application domains</span></span>](../app-domains/use.md)
