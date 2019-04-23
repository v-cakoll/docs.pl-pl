---
title: 'Instrukcje: porównywanie oświadczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: 932ad347730b35a936e040e116e5aa6af36cd3dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343314"
---
# <a name="how-to-compare-claims"></a>Instrukcje: porównywanie oświadczeń
Infrastruktura modelu tożsamości w Windows Communication Foundation (WCF) służy do sprawdzania autoryzacji. W efekcie zadanie często wykonywane jest porównanie oświadczeń w kontekście autoryzacji oświadczeń, wymagane do wykonania żądanej akcji ani uzyskać dostępu do żądanego zasobu. W tym temacie opisano sposób porównywania roszczenia, w tym typów wbudowanych i niestandardowych oświadczeń. Aby uzyskać więcej informacji na temat infrastruktury modelu tożsamości, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
 Porównywanie oświadczeń obejmuje porównanie trzy części (typ prawa i zasobów) oświadczenia o tej samej części w innym oświadczeń, aby zobaczyć, czy są równe. Zobacz poniższy przykład.  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 Zarówno oświadczeń ma typ oświadczenia <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, po prawej stronie <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>i zasobu ciągu "ktoś". Jak trzy części oświadczenia są równe, samodzielnie oświadczenia są równe.  
  
 Typy wbudowane oświadczeń są porównywane za pomocą <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody. Kod porównania specyficznego dla oświadczeń jest używany, gdy jest to konieczne. Na przykład biorąc pod uwagę następujące dwa główne nazwy (UPN) oświadczenia użytkowników:  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 Kod porównania w <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda zwraca `true`, przyjmuje `example\someone` identyfikuje tego samego użytkownika domeny jako "someone@example.com".  
  
 Niestandardowe typy oświadczeń można również porównać przy użyciu <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody. Jednak w przypadkach, gdzie typ zwrócony przez <xref:System.IdentityModel.Claims.Claim.Resource%2A> właściwość oświadczenia jest coś innego niż typ pierwotny <xref:System.IdentityModel.Claims.Claim.Equals%2A> zwraca `true` tylko wtedy, gdy wartości zwracane przez `Resource` właściwości są równe zgodnie z <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody. W przypadkach, gdy nie jest to odpowiedni typ niestandardowy zwrócony przez `Resource` należy zastąpić właściwość <xref:System.IdentityModel.Claims.Claim.Equals%2A> i <xref:System.Object.GetHashCode%2A> metody, aby wykonać dowolne niestandardowe przetwarzanie danych jest konieczne.  
  
### <a name="comparing-built-in-claims"></a>Porównywanie oświadczeń wbudowane  
  
1. Biorąc pod uwagę dwa wystąpienia <xref:System.IdentityModel.Claims.Claim> klasy, należy użyć <xref:System.IdentityModel.Claims.Claim.Equals%2A> się porównania, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a>Porównywanie oświadczeń niestandardowych typów pierwotnych zasobów  
  
1. Niestandardowe oświadczenia przy użyciu typów pierwotnych zasobów można wykonać porównania jak w przypadku wbudowanych oświadczenia, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2. Aby zastąpić powinny oświadczenia niestandardowe, struktury lub klasy na podstawie typów zasobów, typ zasobu <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.  
  
3. Najpierw należy sprawdzić, czy `obj` parametr jest `null`i jeśli tak, zwracają `false`.  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4. Następnie wywołaj <xref:System.Object.ReferenceEquals%2A> i przekazać `this` i `obj` jako parametry. Jeśli zostanie zwrócona `true`, a następnie wróć `true`.  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5. Następnie Przystąp do przypisania `obj` do zmiennej lokalnej o typie danej klasy. W przypadku niepowodzenia odwołanie jest `null`. W takiej sytuacji należy zwracać `false`.  
  
6. Wykonać porównanie niestandardowe poprawnie porównanie bieżącej oświadczenia do podanego oświadczeń.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawiono porównanie oświadczenia niestandardowe, gdzie zasobów oświadczeń jest typem niepodstawowe.  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Instrukcje: Tworzenie oświadczenia niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
