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
# <a name="finding-claims-in-a-claimset"></a>Znajdowanie oświadczeń w zestawie oświadczeń
Badanie zawartości <xref:System.IdentityModel.Claims.ClaimSet> dla określonych typów oświadczeń jest typowych zadań, używając autoryzacji na podstawie oświadczeń. Aby sprawdzić <xref:System.IdentityModel.Claims.ClaimSet> obecność konkretne oświadczenia, można użyć <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> metody. Ta metoda zapewnia lepszą wydajność niż Iterowanie bezpośrednio po <xref:System.IdentityModel.Claims.ClaimSet>. W poniższym przykładzie pokazano to użycie. Należy pamiętać, że `claimType` i `claimRight` parametry mogą być `null`. W takim przypadku parametry będą zgodne wszystkie typy oświadczeń i oświadczeń praw.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
