---
title: 'Instrukcje: Tworzenie oświadczenia niestandardowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: e78f577e0fd3473575fab998e55616936212ebb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185619"
---
# <a name="how-to-create-a-custom-claim"></a>Instrukcje: Tworzenie oświadczenia niestandardowego
Infrastruktura modelu tożsamości w programie Windows Communication Foundation (WCF) udostępnia zestaw wbudowanych typów <xref:System.IdentityModel.Claims.Claim> oświadczeń i praw z funkcjami pomocnika do tworzenia wystąpień z tymi typami i prawami. Te wbudowane oświadczenia są przeznaczone do modelowania informacji znalezionych w typach poświadczeń klienta, które WCF obsługuje domyślnie. W wielu przypadkach wbudowane oświadczenia są wystarczające; jednak niektóre aplikacje mogą wymagać oświadczeń niestandardowych. Oświadczenie składa się z typu oświadczenia, zasobu, którego dotyczy oświadczenie i prawa, które jest dochodzony przez ten zasób. W tym temacie opisano sposób tworzenia oświadczenia niestandardowego.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Aby utworzyć oświadczenie niestandardowe oparte na pierwotnym typie danych  
  
1. Utwórz oświadczenie niestandardowe, przekazując typ oświadczenia, <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> wartość zasobu i prawo do konstruktora.  
  
    1. Zdecyduj o unikatowej wartości dla typu oświadczenia.  
  
         Typ oświadczenia jest unikatowym identyfikatorem ciągu. Jest to niestandardowy projektant oświadczeń jest odpowiedzialny, aby upewnić się, że identyfikator ciągu, który jest używany dla typu oświadczenia jest unikatowy. Aby uzyskać listę typów oświadczeń, które są zdefiniowane przez WCF, zobacz <xref:System.IdentityModel.Claims.ClaimTypes> klasy.  
  
    2. Wybierz pierwotny typ i wartość danych dla zasobu.  
  
         Zasób jest obiektem. Typ CLR zasobu może być pierwotny, <xref:System.String> taki <xref:System.Int32>jak lub , lub dowolny typ serializowalny. Typ CLR zasobu musi być serializowalny, ponieważ oświadczenia są serializowane w różnych punktach przez WCF. Typy pierwotne są serializable.  
  
    3. Wybierz prawo, które jest zdefiniowane przez WCF lub unikatową wartość dla prawa niestandardowego.  
  
         Prawo jest unikatowy identyfikator ciągu. Prawa, które są zdefiniowane przez WCF są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasie.  
  
         Jest to niestandardowy projektant oświadczeń jest odpowiedzialny, aby upewnić się, że identyfikator ciągu, który jest używany dla prawej jest unikatowa.  
  
         Poniższy przykład kodu tworzy oświadczenie niestandardowe `http://example.org/claims/simplecustomclaim`z typem `Driver's License`oświadczenia , <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> dla zasobu o nazwie i z prawej strony.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>Aby utworzyć oświadczenie niestandardowe oparte na nieizbowym typie danych  
  
1. Utwórz oświadczenie niestandardowe, przekazując typ oświadczenia, <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> wartość zasobu i prawo do konstruktora.  
  
    1. Zdecyduj o unikatowej wartości dla typu oświadczenia.  
  
         Typ oświadczenia jest unikatowym identyfikatorem ciągu. Jest to niestandardowy projektant oświadczeń jest odpowiedzialny, aby upewnić się, że identyfikator ciągu, który jest używany dla typu oświadczenia jest unikatowy. Aby uzyskać listę typów oświadczeń, które są zdefiniowane przez WCF, zobacz <xref:System.IdentityModel.Claims.ClaimTypes> klasy.  
  
    2. Wybierz lub zdefiniuj serializowalny typ nieiwersyjny dla zasobu.  
  
         Zasób jest obiektem. Typ CLR zasobu musi być serializowalny, ponieważ oświadczenia są serializowane w różnych punktach przez WCF. Typy pierwotne są już serializable.  
  
         Po zdefiniowaniu nowego typu <xref:System.Runtime.Serialization.DataContractAttribute> zastosuj do klasy. Zastosuj również <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut do wszystkich elementów członkowskich nowego typu, które muszą być serializowane jako część oświadczenia.  
  
         Poniższy przykład kodu definiuje niestandardowy `MyResourceType`typ zasobu o nazwie .  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. Wybierz prawo, które jest zdefiniowane przez WCF lub unikatową wartość dla prawa niestandardowego.  
  
         Prawo jest unikatowy identyfikator ciągu. Prawa, które są zdefiniowane przez WCF są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasie.  
  
         Jest to niestandardowy projektant oświadczeń jest odpowiedzialny, aby upewnić się, że identyfikator ciągu, który jest używany dla prawej jest unikatowa.  
  
         Poniższy przykład kodu tworzy oświadczenie niestandardowe `http://example.org/claims/complexcustomclaim`z typem `MyResourceType`oświadczenia , <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> niestandardowy typ zasobu , i z prawej.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano, jak utworzyć oświadczenie niestandardowe z pierwotnym typem zasobu i oświadczeniem niestandardowym z nieiderzym typem zasobu.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
