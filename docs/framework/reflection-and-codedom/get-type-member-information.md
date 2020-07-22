---
title: 'Instrukcje: uzyskiwanie informacji o typie i elemencie członkowskim za pomocą odbicia'
description: Dowiedz się, jak uzyskać informacje o typie i elemencie członkowskim za pomocą odbicia przy użyciu przestrzeni nazw System. odbicie.
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: fa7af39c0addb328944a03236c26982301caf722
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865323"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="abcfe-103">Instrukcje: uzyskiwanie informacji o typie i elemencie członkowskim za pomocą odbicia</span><span class="sxs-lookup"><span data-stu-id="abcfe-103">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="abcfe-104"><xref:System.Reflection>Przestrzeń nazw zawiera wiele metod uzyskiwania informacji na temat typów i ich członków.</span><span class="sxs-lookup"><span data-stu-id="abcfe-104">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="abcfe-105">W tym artykule przedstawiono jedną z tych metod <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="abcfe-105">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="abcfe-106">Aby uzyskać dodatkowe informacje, zobacz [Omówienie odbicia](reflection.md).</span><span class="sxs-lookup"><span data-stu-id="abcfe-106">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="abcfe-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="abcfe-107">Example</span></span>

<span data-ttu-id="abcfe-108">Poniższy przykład pobiera informacje o typie i elemencie członkowskim za pomocą odbicia:</span><span class="sxs-lookup"><span data-stu-id="abcfe-108">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="abcfe-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abcfe-109">See also</span></span>

- [<span data-ttu-id="abcfe-110">Program z domenami aplikacji</span><span class="sxs-lookup"><span data-stu-id="abcfe-110">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="abcfe-111">Odbicie</span><span class="sxs-lookup"><span data-stu-id="abcfe-111">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="abcfe-112">Korzystanie z domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="abcfe-112">Use application domains</span></span>](../app-domains/use.md)
