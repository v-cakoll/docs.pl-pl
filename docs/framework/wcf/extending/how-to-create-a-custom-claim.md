---
title: 'Instrukcje: tworzenie oświadczenia niestandardowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 1892e910a86e01b7b2ee0f6a2403ad7af4688808
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295383"
---
# <a name="how-to-create-a-custom-claim"></a>Instrukcje: tworzenie oświadczenia niestandardowego
Infrastruktura modelu tożsamości w Windows Communication Foundation (WCF) zapewnia zestaw typów wbudowanych oświadczeń i uprawnień przy użyciu funkcji pomocnika dla tworzenia <xref:System.IdentityModel.Claims.Claim> wystąpień z tych typów i praw. Te wbudowane oświadczenia są przeznaczone do informacji o modelu znaleziono w typy poświadczeń klienta, które obsługuje WCF domyślnie. W wielu przypadkach wbudowanych oświadczenia są wystarczające; Jednak niektóre aplikacje mogą wymagać oświadczenia niestandardowe. Oświadczenia składa się z typu oświadczenia, zasobów, dla której oświadczenia ma zastosowanie do i potwierdzone praw za pośrednictwem tego zasobu. W tym temacie opisano tworzenie oświadczenia niestandardowego.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Aby utworzyć oświadczenia niestandardowego, który jest oparty na typie danych pierwotnych  
  
1. Tworzenie oświadczenia niestandardowego, przekazując typ oświadczenia, wartość zasobu i po prawej stronie, aby <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktora.  
  
    1.  Decyzję w sprawie unikatową wartość dla typu oświadczenia.  
  
         Typ oświadczenia jest identyfikator unikatowy ciąg. Odpowiada za projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany dla typu oświadczenia jest unikatowa. Aby uzyskać listę typów oświadczeń, które są zdefiniowane przez architekturę WCF, zobacz <xref:System.IdentityModel.Claims.ClaimTypes> klasy.  
  
    2.  Wybierz typ danych pierwotnych i wartość zasobu.  
  
         Zasób jest obiektem. Typ CLR zasób może być podstawowy, taką jak <xref:System.String> lub <xref:System.Int32>, lub dowolny typ możliwy do serializacji. Typ CLR zasobu musi być możliwy do serializacji, ponieważ oświadczeń są serializowane w różnych momentach przez architekturę WCF. Typy pierwotne są możliwe do serializacji.  
  
    3.  Wybierz po prawej stronie, który jest definiowany przez WCF lub unikatową wartość dla niestandardowych po prawej stronie.  
  
         Po prawej stronie jest identyfikator unikatowy ciąg. Prawa, które są definiowane przez architekturę WCF są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasy.  
  
         Odpowiada za projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany do prawej strony jest unikatowa.  
  
         Poniższy przykład kodu tworzy niestandardowe oświadczenia o typie oświadczenia `http://example.org/claims/simplecustomclaim`, zasobu o nazwie `Driver's License`i <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> prawo.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>Aby utworzyć oświadczenia niestandardowego, który jest oparty na typie danych niepodstawowe  
  
1. Tworzenie oświadczenia niestandardowego, przekazując typ oświadczenia, wartość zasobu i po prawej stronie, aby <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktora.  
  
    1.  Decyzję w sprawie unikatową wartość dla typu oświadczenia.  
  
         Typ oświadczenia jest identyfikator unikatowy ciąg. Odpowiada za projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany dla typu oświadczenia jest unikatowa. Aby uzyskać listę typów oświadczeń, które są zdefiniowane przez architekturę WCF, zobacz <xref:System.IdentityModel.Claims.ClaimTypes> klasy.  
  
    2.  Wybierz, czy definiowane serializacji typu niepodstawowych dla zasobu.  
  
         Zasób jest obiektem. Typ CLR zasobu musi być możliwy do serializacji, ponieważ oświadczeń są serializowane w różnych momentach przez architekturę WCF. Typy pierwotne są już możliwe do serializacji.  
  
         Jeśli nowy typ jest zdefiniowany, zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> do klasy. Mają zastosowanie również w <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu dla wszystkich członków nowy typ, który musi być serializowana jako część oświadczenia.  
  
         Poniższy kod definiuje niestandardowy typ zasobu o nazwie `MyResourceType`.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  Wybierz po prawej stronie, który jest definiowany przez WCF lub unikatową wartość dla niestandardowych po prawej stronie.  
  
         Po prawej stronie jest identyfikator unikatowy ciąg. Prawa, które są definiowane przez architekturę WCF są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasy.  
  
         Odpowiada za projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany do prawej strony jest unikatowa.  
  
         Poniższy przykład kodu tworzy niestandardowe oświadczenia o typie oświadczenia `http://example.org/claims/complexcustomclaim`, niestandardowy typ zasobu z `MyResourceType`i <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> prawo.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak utworzyć oświadczenia niestandardowego z typem pierwotnym zasobów i oświadczenia niestandardowego typu zasobów niepodstawowe.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
