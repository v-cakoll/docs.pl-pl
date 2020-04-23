---
title: 'Instrukcje: uzyskiwanie informacji o typie i elemencie członkowskim za pomocą odbicia'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 9ffc173bbd0ed12eedea0c191f6d39baf181793a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130214"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="5a92d-102">Instrukcje: uzyskiwanie informacji o typie i elemencie członkowskim za pomocą odbicia</span><span class="sxs-lookup"><span data-stu-id="5a92d-102">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="5a92d-103"><xref:System.Reflection> Przestrzeń nazw zawiera wiele metod uzyskiwania informacji na temat typów i ich członków.</span><span class="sxs-lookup"><span data-stu-id="5a92d-103">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="5a92d-104">W tym artykule przedstawiono jedną z tych metod <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5a92d-104">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5a92d-105">Aby uzyskać dodatkowe informacje, zobacz [Omówienie odbicia](reflection.md).</span><span class="sxs-lookup"><span data-stu-id="5a92d-105">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="5a92d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a92d-106">Example</span></span>

<span data-ttu-id="5a92d-107">Poniższy przykład pobiera informacje o typie i elemencie członkowskim za pomocą odbicia:</span><span class="sxs-lookup"><span data-stu-id="5a92d-107">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="5a92d-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a92d-108">See also</span></span>

- [<span data-ttu-id="5a92d-109">Program z domenami aplikacji</span><span class="sxs-lookup"><span data-stu-id="5a92d-109">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="5a92d-110">Odbicie</span><span class="sxs-lookup"><span data-stu-id="5a92d-110">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="5a92d-111">Korzystanie z domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="5a92d-111">Use application domains</span></span>](../app-domains/use.md)
