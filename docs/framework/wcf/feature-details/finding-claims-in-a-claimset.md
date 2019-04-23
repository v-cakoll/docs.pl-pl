---
title: Znajdowanie oświadczeń w zestawie oświadczeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
ms.openlocfilehash: 42e6ee682220913f872da337eb41f6c290082988
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137127"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="133f6-102">Znajdowanie oświadczeń w zestawie oświadczeń</span><span class="sxs-lookup"><span data-stu-id="133f6-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="133f6-103">Sprawdzając zawartość <xref:System.IdentityModel.Claims.ClaimSet> dla określonych typów oświadczeń jest typowym zadaniem, korzystając z autoryzacja na podstawie oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="133f6-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="133f6-104">Aby zbadać <xref:System.IdentityModel.Claims.ClaimSet> obecność konkretne oświadczenia, można użyć <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="133f6-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="133f6-105">Ta metoda zapewnia lepszą wydajność niż bezpośrednio Iterowanie <xref:System.IdentityModel.Claims.ClaimSet>.</span><span class="sxs-lookup"><span data-stu-id="133f6-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="133f6-106">W poniższym przykładzie pokazano użycie tych.</span><span class="sxs-lookup"><span data-stu-id="133f6-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="133f6-107">Należy pamiętać, że `claimType` i `claimRight` parametry mogą być `null`.</span><span class="sxs-lookup"><span data-stu-id="133f6-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="133f6-108">W takim przypadku parametrów odpowiadać wszystkie typy oświadczeń i oświadczenia praw.</span><span class="sxs-lookup"><span data-stu-id="133f6-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="133f6-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="133f6-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="133f6-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="133f6-110">See also</span></span>

- [<span data-ttu-id="133f6-111">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="133f6-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
