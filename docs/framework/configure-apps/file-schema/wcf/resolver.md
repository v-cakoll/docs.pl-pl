---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 57fa67c9536d35775694c56c9053cffa4dea29ea
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257463"
---
# <a name="resolver"></a>\<resolver>
Określa program rozpoznawania elementów równorzędnych, który jest używany do rozpoznawania elementu równorzędnego siatki identyfikator do zbioru adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w siatce.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netPeerBinding>  
\<Powiązanie >  
\<resolver>  
  
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
|`mode`|Ciąg, który określa, czy wystąpienie równorzędnego programu rozpoznawania skojarzone z tą usługą jest specyficzne dla PNRP, niestandardowym programem rozpoznawania nazw czy określone automatycznie. Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.|  
|`referralPolicy`|Ciąg, który określa sposób odwołań są udostępniane między elementami równorzędnymi. Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Określa ustawienia dla równorzędnej niestandardowej usługi rozpoznawania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości wiązania [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Uwagi  
 Rozpoznawania nazw równorzędnych to Usługa odnajdywania używana przez kanały równorzędnej można znaleźć elementu równorzędnego węzłów, które uczestniczą w siatki elementów równorzędnych. Służy również "register" węzeł z siatki elementów równorzędnych, mechanizm, za pomocą którego węzła równorzędnego staje się znane i dostępne z siatki elementów równorzędnych. Aby uzyskać więcej informacji na temat mechanizmy rozpoznawania elementów równorzędnych, zobacz [mechanizmy rozpoznawania elementów równorzędnych](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [Mechanizmy rozpoznawania elementów równorzędnych](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- [Dodawanie niestandardowego mechanizmu do aplikacji PeerChannel](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
