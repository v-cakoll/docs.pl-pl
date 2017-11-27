---
title: '&lt;niestandardowe&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5bccfc95313ae3ae4a692be2165dc694783a460e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomgt"></a>&lt;niestandardowe&gt;
Określa ustawienia dla równorzędnej niestandardowej usługi rozpoznawania.  
  
\<system.serviceModel >  
\<powiązania >  
\<netPeerBinding >  
\<Powiązanie >  
\<mechanizm rozpoznawania >  
\<niestandardowe >  
  
## <a name="syntax"></a>Składnia  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`address`|Identyfikator URI, który określa adres punktu końcowego węzła równorzędnego, który jest hostem równorzędnej niestandardowej usługi rozpoznawania.|  
|`resolverType`|Ciąg określający typ równorzędnej niestandardowej usługi rozpoznawania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Określa tożsamość mechanizmy rozpoznawania elementów równorzędnych niestandardowych skonfigurowanych z tym elementem. Ten element jest typu <xref:System.ServiceModel.Configuration.IdentityElement>.|  
|[\<nagłówki >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Kolekcja dla wiadomości SOAP nagłówka adresu obsługiwane przez program rozpoznawania nazw dla równorzędnej niestandardowej.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<mechanizm rozpoznawania >](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|Program rozpoznawania elementów równorzędnych, który jest używany do rozpoznawania elementu równorzędnego ID siatki do zbioru adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w siatce.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element definiuje ustawienia podstawowe dla równorzędnej niestandardowej usługi rozpoznawania nazw, w tym adres punktu końcowego elementu równorzędnego obsługującego usługę, a wszystkie ustawienia określone powiązanie. Aby uzyskać więcej informacji na temat tworzenia niestandardowego programu rozpoznawania nazw, zobacz [Dodawanie niestandardowego programu rozpoznawania nazw dla aplikacji PeerChannel](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [Mechanizmy rozpoznawania elementów równorzędnych](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [Dodawanie do aplikacji PeerChannel niestandardowego programu rozpoznawania nazw](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
