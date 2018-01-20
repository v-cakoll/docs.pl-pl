---
title: "Porady: uzyskiwanie informacji dotyczących typów i członków z zestawu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c3112b7484e4d03eaacd218ff8e8ac34e77745b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="94185-102">Porady: uzyskiwanie informacji dotyczących typów i członków z zestawu</span><span class="sxs-lookup"><span data-stu-id="94185-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="94185-103"><xref:System.Reflection> Przestrzeń nazw zawiera wiele metod uzyskiwania informacji z zestawu.</span><span class="sxs-lookup"><span data-stu-id="94185-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="94185-104">W tej sekcji przedstawiono jednej z tych metod.</span><span class="sxs-lookup"><span data-stu-id="94185-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="94185-105">Aby uzyskać dodatkowe informacje, zobacz [omówienie odbicia](../../../docs/framework/reflection-and-codedom/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="94185-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="94185-106">Poniższy przykład uzyskuje informacje o typie i element członkowski z zestawu.</span><span class="sxs-lookup"><span data-stu-id="94185-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94185-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="94185-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="94185-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94185-108">See Also</span></span>  
 [<span data-ttu-id="94185-109">Programowanie za pomocą domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="94185-109">Programming with Application Domains</span></span>](http://msdn.microsoft.com/library/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="94185-110">Odbicie</span><span class="sxs-lookup"><span data-stu-id="94185-110">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [<span data-ttu-id="94185-111">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="94185-111">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
