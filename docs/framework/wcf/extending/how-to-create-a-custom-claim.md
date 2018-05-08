---
title: 'Instrukcje: Tworzenie oświadczenia niestandardowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: c1e8886ab3d9d90b217ce79078633433458bbe4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-custom-claim"></a>Instrukcje: Tworzenie oświadczenia niestandardowego
Infrastruktury modelu tożsamości w systemie Windows Communication Foundation (WCF) zawiera zestaw wbudowanych oświadczenia i prawa o funkcje pomocnicze do tworzenia <xref:System.IdentityModel.Claims.Claim> wystąpień z tych typów i praw. Te wbudowane oświadczenia są przeznaczone do informacji o modelu znaleziono w kliencie poświadczeń typy, które [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje domyślnie. W wielu przypadkach wbudowanych oświadczenia są wystarczające; Jednak niektóre aplikacje mogą wymagać oświadczenia niestandardowe. Oświadczenie składa się z typu oświadczenia, zasobów, dla której oświadczenia dotyczy i praw potwierdzona za pośrednictwem tego zasobu. W tym temacie opisano tworzenie oświadczenia niestandardowego.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Aby tworzenie oświadczenia niestandardowego, który jest oparty na typie danych pierwotnych  
  
1.  Tworzenie oświadczenia niestandardowego przez przekazanie typu oświadczenia i wartości zasobów prawo do <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktora.  
  
    1.  Wybierz unikatową wartość dla typu oświadczenia.  
  
         Typ oświadczenia jest identyfikator unikatowy ciąg. Odpowiada projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany dla typu oświadczenia jest unikatowa. Aby uzyskać listę typów oświadczeń, które są zdefiniowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zobacz <xref:System.IdentityModel.Claims.ClaimTypes> klasy.  
  
    2.  Wybierz typ danych pierwotnych i wartość zasobu.  
  
         Zasób jest obiektem. Typ CLR zasób może być typu pierwotnego, takich jak <xref:System.String> lub <xref:System.Int32>, lub typ możliwy do serializacji. Typ CLR zasobu musi być możliwy do serializacji, ponieważ oświadczenia są serializowane w różnych momentach przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Typy pierwotne są możliwy do serializacji.  
  
    3.  Wybierz uprawnienia, który jest definiowana za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lub unikatową wartość dla niestandardowego prawo.  
  
         Prawo to identyfikator unikatowy ciąg. Prawa, które są zdefiniowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasy.  
  
         Odpowiada projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany do prawej jest unikatowa.  
  
         Poniższy przykład kodu tworzy oświadczenia niestandardowego o typie oświadczenia `http://example.org/claims/simplecustomclaim`, dla zasobu o nazwie `Driver's License`oraz <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> prawo.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>Aby tworzenie oświadczenia niestandardowego, który jest oparty na typie danych innego niż pierwotny  
  
1.  Tworzenie oświadczenia niestandardowego przez przekazanie typu oświadczenia i wartości zasobów prawo do <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktora.  
  
    1.  Wybierz unikatową wartość dla typu oświadczenia.  
  
         Typ oświadczenia jest identyfikator unikatowy ciąg. Odpowiada projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany dla typu oświadczenia jest unikatowa. Aby uzyskać listę typów oświadczeń, które są zdefiniowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zobacz <xref:System.IdentityModel.Claims.ClaimTypes> klasy.  
  
    2.  Wybierz lub zdefiniuj serializacji typu innego niż pierwotny dla zasobu.  
  
         Zasób jest obiektem. Typ CLR zasobu musi być możliwy do serializacji, ponieważ oświadczenia są serializowane w różnych momentach przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Typy pierwotne są już możliwy do serializacji.  
  
         Jeśli nowy typ jest zdefiniowany, zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> do klasy. Mają zastosowanie również <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do wszystkich elementów członkowskich typu nowe, które muszą być Zserializowany jako część oświadczenia.  
  
         Poniższy przykład kodu określa niestandardowy typ zasobu o nazwie `MyResourceType`.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  Wybierz uprawnienia, który jest definiowana za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lub unikatową wartość dla niestandardowego prawo.  
  
         Prawo to identyfikator unikatowy ciąg. Prawa, które są zdefiniowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasy.  
  
         Odpowiada projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany do prawej jest unikatowa.  
  
         Poniższy przykład kodu tworzy oświadczenia niestandardowego o typie oświadczenia `http://example.org/claims/complexcustomclaim`, niestandardowy typ zasobu z `MyResourceType`oraz <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> prawo.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak tworzenie oświadczenia niestandardowego o typie pierwotnym zasobów i oświadczenia niestandardowe przy użyciu typu innego niż pierwotny zasobu.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
