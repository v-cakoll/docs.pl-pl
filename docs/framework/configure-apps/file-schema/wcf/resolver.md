---
title: '&lt;Program rozpoznawania nazw&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5734a985c4941a12be5032c254a75987f2074da6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltresolvergt"></a>&lt;Program rozpoznawania nazw&gt;
Określa program rozpoznawania elementów równorzędnych, który jest używany do rozpoznawania elementu równorzędnego ID siatki do zbioru adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w siatce.  
  
 \<System. ServiceModel >  
\<powiązania >  
\<netPeerBinding >  
\<Powiązanie >  
\<mechanizm rozpoznawania >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`mode`|Ciąg, który określa, czy wystąpienie równorzędnego programu rozpoznawania skojarzone z tą usługą jest specyficzne dla PNRP, niestandardowym programem rozpoznawania nazw, czy określone automatycznie. Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.|  
|`referralPolicy`|Ciąg, który określa sposób według którego odwołania są współużytkowane przez elementy równorzędne. Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<nagłówki >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Określa ustawienia dla równorzędnej niestandardowej usługi rozpoznawania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Uwagi  
 Nazwa elementu równorzędnego program rozpoznawania nazw odnajdywania usługa jest używana przez kanałów elementów równorzędnych można znaleźć elementu równorzędnego węzłów, które uczestniczą w sieci równorzędnej. Służy również do "register" węzeł z siatki elementów równorzędnych, mechanizm, za pomocą którego węzła równorzędnego staje się znane i dostępne w sieci równorzędnej. Aby uzyskać więcej informacji dotyczących mechanizmy rozpoznawania elementów równorzędnych, zobacz [mechanizmy rozpoznawania elementów równorzędnych](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [Mechanizmy rozpoznawania elementów równorzędnych](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [Dodawanie do aplikacji PeerChannel niestandardowego programu rozpoznawania nazw](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
