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
ms.openlocfilehash: e2d3d33900dd894eea77420aac444ebde0df9a43
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68970775"
---
# <a name="how-to-compare-claims"></a>Instrukcje: porównywanie oświadczeń

Infrastruktura modelu tożsamości w Windows Communication Foundation (WCF) służy do sprawdzania autoryzacji. W związku z tym typowym zadaniem jest porównanie oświadczeń w kontekście autoryzacji do oświadczeń wymaganych do wykonania żądanej akcji lub uzyskania dostępu do żądanego zasobu. W tym temacie opisano sposób porównywania oświadczeń, w tym wbudowanych i niestandardowych typów oświadczeń. Aby uzyskać więcej informacji na temat infrastruktury modelu tożsamości, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).

Porównanie roszczeń obejmuje porównanie trzech części roszczeń (typu, praw i zasobu) z tymi samymi częściami w innym zasobie, aby sprawdzić, czy są równe. Zobacz Poniższy przykład.

[!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
[!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]

Oba oświadczenia mają typ <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>oświadczenia, z <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>prawej strony i zasób ciągu "ktoś". Ponieważ wszystkie trzy części oświadczenia są równe, same oświadczenia są równe.

Wbudowane typy zgłoszeń są porównywane przy użyciu <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody. Kod porównania specyficzny dla roszczeń jest używany w razie potrzeby. Na przykład uwzględniając następujące dwie oświadczenia głównej nazwy użytkownika (UPN):

[!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
[!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]

Kod porównania w <xref:System.IdentityModel.Claims.Claim.Equals%2A> metodzie zwraca `true`, przy założeniu, że `example\someone` identyfikuje tego samego użytkownikasomeone@example.comdomeny jako "".

Niestandardowe typy roszczeń można także porównać przy użyciu <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody. Jednakże w przypadkach, gdy <xref:System.IdentityModel.Claims.Claim.Resource%2A> typ zwracany przez właściwość żądania jest coś innego niż typ pierwotny <xref:System.IdentityModel.Claims.Claim.Equals%2A> , zwraca `true` tylko wtedy, gdy wartości zwracane przez `Resource` właściwości są równe w zależnościod<xref:System.IdentityModel.Claims.Claim.Equals%2A> Metoda. W przypadkach, gdy nie jest to odpowiednie, typ niestandardowy zwracany przez `Resource` właściwość powinna <xref:System.IdentityModel.Claims.Claim.Equals%2A> przesłaniać metody i <xref:System.Object.GetHashCode%2A> , aby wykonać dowolne niestandardowe przetwarzanie.

## <a name="comparing-built-in-claims"></a>Porównywanie wbudowanych oświadczeń

1. Podano dwa wystąpienia <xref:System.IdentityModel.Claims.Claim> klasy, użyj, <xref:System.IdentityModel.Claims.Claim.Equals%2A> aby dokonać porównania, jak pokazano w poniższym kodzie.

     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]

### <a name="comparing-custom-claims-with-primitive-resource-types"></a>Porównywanie oświadczeń niestandardowych z typami zasobów pierwotnych

1. W przypadku oświadczeń niestandardowych z typami zasobów pierwotnych można wykonać porównanie jako dla oświadczeń wbudowanych, jak pokazano w poniższym kodzie.

     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]

2. W przypadku oświadczeń niestandardowych ze strukturą lub typami zasobów opartymi na klasie typ zasobu powinien <xref:System.IdentityModel.Claims.Claim.Equals%2A> zastąpić metodę.

3. Najpierw sprawdź, czy `obj` parametr jest `null`, i jeśli tak, Return `false`.

     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]

4. Następne wywołanie <xref:System.Object.ReferenceEquals%2A> i przekazanie `obj` `this` oraz jako parametry. Jeśli funkcja zwróci `true`wartość, zwraca `true`.

     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]

5. Kolejna próba przypisania `obj` do zmiennej lokalnej typu klasy. Jeśli to się nie powiedzie, `null`odwołanie jest. W takich przypadkach zwracamy `false`.

6. Wykonaj niestandardowe porównanie niezbędne do poprawnego porównania bieżącego żądania z podanym zastrzeżeniem.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia porównanie niestandardowych oświadczeń, w których zasób oświadczenia jest typem niepierwotnym.

[!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
[!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]

## <a name="see-also"></a>Zobacz także

- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Instrukcje: Tworzenie niestandardowego żądania](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
