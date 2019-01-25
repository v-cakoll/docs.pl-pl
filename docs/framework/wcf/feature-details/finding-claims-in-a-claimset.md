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
ms.openlocfilehash: 81212d5b85ec516ae69c9c015c147cd011a9fd14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495134"
---
# <a name="finding-claims-in-a-claimset"></a>Znajdowanie oświadczeń w zestawie oświadczeń
Sprawdzając zawartość <xref:System.IdentityModel.Claims.ClaimSet> dla określonych typów oświadczeń jest typowym zadaniem, korzystając z autoryzacja na podstawie oświadczeń. Aby zbadać <xref:System.IdentityModel.Claims.ClaimSet> obecność konkretne oświadczenia, można użyć <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> metody. Ta metoda zapewnia lepszą wydajność niż bezpośrednio Iterowanie <xref:System.IdentityModel.Claims.ClaimSet>. W poniższym przykładzie pokazano użycie tych. Należy pamiętać, że `claimType` i `claimRight` parametry mogą być `null`. W takim przypadku parametrów odpowiadać wszystkie typy oświadczeń i oświadczenia praw.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a>Zobacz także
- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
