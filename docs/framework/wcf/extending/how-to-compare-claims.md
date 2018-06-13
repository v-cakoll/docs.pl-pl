---
title: 'Porady: Porównywanie oświadczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: 1ef957efcb4cc9330c1c273a1c953afc5b7dd240
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489086"
---
# <a name="how-to-compare-claims"></a>Porady: Porównywanie oświadczeń
Infrastruktura modelu tożsamości w systemie Windows Communication Foundation (WCF) służy do sprawdzania autoryzacji. W efekcie typowych zadań jest porównywanie oświadczeń w kontekście autoryzacji oświadczeń wymagane do wykonania żądanej akcji lub dostęp do żądanego zasobu. W tym temacie opisano sposób porównywania roszczenia, w tym typy oświadczeń wbudowanych i niestandardowych. Aby uzyskać więcej informacji na temat infrastruktury modelu tożsamości, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
 Porównanie oświadczeń obejmuje porównanie trzech części oświadczenia (typ uprawnienia i zasobów) o tej samej części w innym oświadczeń, aby zobaczyć, czy są równe. Zobacz poniższy przykład.  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 Zarówno oświadczenia mają typ oświadczenia <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, prawej strony <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>i zasobów ciągu "ktoś". Wszystkie trzy elementy oświadczenia są takie same, same oświadczenia są takie same.  
  
 Typy wbudowane oświadczeń są porównywane przy użyciu <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody. Kod oświadczenia dotyczące porównania jest używany w przypadku, gdy jest to konieczne. Przykładowo podana następujące dwa główne oświadczeniach nazwy użytkownika (UPN):  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 Kod porównania w <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda zwraca `true`, przyjmuje `example\someone` tego samego użytkownika domeny identyfikuje "someone@example.com".  
  
 Niestandardowe typy oświadczeń można również porównać przy użyciu <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody. Jednak w przypadku, gdy typ zwracany przez <xref:System.IdentityModel.Claims.Claim.Resource%2A> właściwość oświadczenia jest typem pierwotnym <xref:System.IdentityModel.Claims.Claim.Equals%2A> zwraca `true` tylko wtedy, gdy wartości zwracane przez `Resource` właściwości są takie same, zgodnie z <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody. W przypadkach, gdy nie jest to odpowiedni niestandardowy typ zwrócony przez `Resource` powinny zastępować właściwość <xref:System.IdentityModel.Claims.Claim.Equals%2A> i <xref:System.Object.GetHashCode%2A> metody służące do wykonania niestandardowej przetwarzania jest wymagane.  
  
### <a name="comparing-built-in-claims"></a>Porównywanie oświadczeń wbudowane  
  
1.  Podane dwa wystąpienia <xref:System.IdentityModel.Claims.Claim> klasy, należy użyć <xref:System.IdentityModel.Claims.Claim.Equals%2A> do wykonania porównania, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a>Porównywanie oświadczeń niestandardowych typów pierwotnych zasobów  
  
1.  Niestandardowe oświadczeń z typów pierwotnych zasobów można wykonać porównania podobnie jak w przypadku oświadczeń wbudowane, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2.  Dla oświadczenia niestandardowe struktury lub klasy na podstawie typów zasobów, typ zasobu powinny zastępować <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.  
  
3.  Najpierw sprawdź, czy `obj` parametr jest `null`, a jeśli tak, wróć `false`.  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4.  Następnie wywołaj <xref:System.Object.ReferenceEquals%2A> i przekaż `this` i `obj` jako parametry. Jeśli zmienna zwraca `true`, następnie zwracany `true`.  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5.  Następnie Przystąp do przypisania `obj` do zmiennej lokalnej typu klasy. Jeśli to się nie powiedzie, odwołanie jest `null`. W takiej sytuacji należy zwracać `false`.  
  
6.  Porównania niestandardowych poprawnie porównanie bieżącego oświadczenia do podanego oświadczeń.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono porównanie oświadczenia niestandardowe, gdy zasób oświadczenia jest typu innego niż pierwotny.  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Instrukcje: tworzenie oświadczenia niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
