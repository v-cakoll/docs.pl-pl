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
ms.openlocfilehash: 1954da20d382630f965582fcc01bbaf72665720a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595456"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="bcf60-102">Znajdowanie oświadczeń w zestawie oświadczeń</span><span class="sxs-lookup"><span data-stu-id="bcf60-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="bcf60-103">Badanie zawartości a <xref:System.IdentityModel.Claims.ClaimSet> dla określonych typów oświadczeń jest typowym zadaniem podczas korzystania z autoryzacji opartej na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="bcf60-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="bcf60-104">Aby poznać <xref:System.IdentityModel.Claims.ClaimSet> obecność określonych oświadczeń, należy użyć <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bcf60-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="bcf60-105">Ta metoda zapewnia lepszą wydajność niż iteracja bezpośrednio w usłudze <xref:System.IdentityModel.Claims.ClaimSet> .</span><span class="sxs-lookup"><span data-stu-id="bcf60-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="bcf60-106">Poniższy przykład ilustruje to użycie.</span><span class="sxs-lookup"><span data-stu-id="bcf60-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="bcf60-107">Należy pamiętać, `claimType` że `claimRight` Parametry i mogą być `null` .</span><span class="sxs-lookup"><span data-stu-id="bcf60-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="bcf60-108">W takim przypadku parametry będą zgodne ze wszystkimi typami i prawami roszczeń.</span><span class="sxs-lookup"><span data-stu-id="bcf60-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcf60-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="bcf60-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="bcf60-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bcf60-110">See also</span></span>

- [<span data-ttu-id="bcf60-111">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="bcf60-111">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
