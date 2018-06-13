---
title: 'Porady: uzyskiwanie informacji dotyczących typów i członków z zestawu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fb06555f18c13f87347a5a76e6f4a3060777f02
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744070"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="8e89e-102">Porady: uzyskiwanie informacji dotyczących typów i członków z zestawu</span><span class="sxs-lookup"><span data-stu-id="8e89e-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="8e89e-103"><xref:System.Reflection> Przestrzeń nazw zawiera wiele metod uzyskiwania informacji z zestawu.</span><span class="sxs-lookup"><span data-stu-id="8e89e-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="8e89e-104">W tej sekcji przedstawiono jednej z tych metod.</span><span class="sxs-lookup"><span data-stu-id="8e89e-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="8e89e-105">Aby uzyskać dodatkowe informacje, zobacz [omówienie odbicia](../../../docs/framework/reflection-and-codedom/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="8e89e-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="8e89e-106">Poniższy przykład uzyskuje informacje o typie i element członkowski z zestawu.</span><span class="sxs-lookup"><span data-stu-id="8e89e-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e89e-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e89e-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="8e89e-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e89e-108">See Also</span></span>  
 <span data-ttu-id="8e89e-109">[Programowanie za pomocą domeny aplikacji](./application-domains.md#programming-with-application-domains) [odbicia](../../../docs/framework/reflection-and-codedom/reflection.md)</span><span class="sxs-lookup"><span data-stu-id="8e89e-109">[Programming with Application Domains](./application-domains.md#programming-with-application-domains) [Reflection](../../../docs/framework/reflection-and-codedom/reflection.md)</span></span>  
 [<span data-ttu-id="8e89e-110">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="8e89e-110">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
