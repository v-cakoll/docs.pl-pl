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
ms.openlocfilehash: 7ca22d701277e71e509e6b291eb59a0223a0250c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="d569d-102">Znajdowanie oświadczeń w zestawie oświadczeń</span><span class="sxs-lookup"><span data-stu-id="d569d-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="d569d-103">Badanie zawartości <xref:System.IdentityModel.Claims.ClaimSet> dla określonych typów oświadczeń jest typowych zadań, używając autoryzacji na podstawie oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="d569d-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="d569d-104">Aby sprawdzić <xref:System.IdentityModel.Claims.ClaimSet> obecność konkretne oświadczenia, można użyć <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d569d-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="d569d-105">Ta metoda zapewnia lepszą wydajność niż Iterowanie bezpośrednio po <xref:System.IdentityModel.Claims.ClaimSet>.</span><span class="sxs-lookup"><span data-stu-id="d569d-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="d569d-106">W poniższym przykładzie pokazano to użycie.</span><span class="sxs-lookup"><span data-stu-id="d569d-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="d569d-107">Należy pamiętać, że `claimType` i `claimRight` parametry mogą być `null`.</span><span class="sxs-lookup"><span data-stu-id="d569d-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="d569d-108">W takim przypadku parametry będą zgodne wszystkie typy oświadczeń i oświadczeń praw.</span><span class="sxs-lookup"><span data-stu-id="d569d-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d569d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d569d-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d569d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d569d-110">See Also</span></span>  
 [<span data-ttu-id="d569d-111">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="d569d-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
