---
title: 'Instrukcje: Uzyskiwanie informacji dotyczących elementu członkowskiego typów i z zestawu'
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
ms.openlocfilehash: ef3fbb7af3097a67cb39f0c3b2ee294b86f0600e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701602"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="d24c0-102">Instrukcje: Uzyskiwanie informacji dotyczących elementu członkowskiego typów i z zestawu</span><span class="sxs-lookup"><span data-stu-id="d24c0-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="d24c0-103"><xref:System.Reflection> Przestrzeń nazw zawiera wiele metod uzyskiwanie informacji z zestawu.</span><span class="sxs-lookup"><span data-stu-id="d24c0-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="d24c0-104">W tej sekcji przedstawiono jednej z następujących metod.</span><span class="sxs-lookup"><span data-stu-id="d24c0-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="d24c0-105">Aby uzyskać więcej informacji, zobacz [Przegląd odbicia](../../../docs/framework/reflection-and-codedom/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="d24c0-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="d24c0-106">W poniższym przykładzie uzyskano informacje typów i elementów członkowskich z zestawu.</span><span class="sxs-lookup"><span data-stu-id="d24c0-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d24c0-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d24c0-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="d24c0-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d24c0-108">See also</span></span>
- [<span data-ttu-id="d24c0-109">Programowanie z domenami aplikacji</span><span class="sxs-lookup"><span data-stu-id="d24c0-109">Programming with Application Domains</span></span>](./application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="d24c0-110">Odbicie</span><span class="sxs-lookup"><span data-stu-id="d24c0-110">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="d24c0-111">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="d24c0-111">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
