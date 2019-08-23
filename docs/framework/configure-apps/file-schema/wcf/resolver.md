---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: e3a9ee00aab6ab48a1ba891565b63824e62b20fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934217"
---
# <a name="resolver"></a>\<resolver>
Określa równorzędny program rozpoznawania, który jest używany do rozpoznawania identyfikatora siatki równorzędnej w zestawie adresów węzłów równorzędnych reprezentujących kilka węzłów, które uczestniczą w sieci.  
  
 \<system.ServiceModel>  
\<> powiązań  
\<netPeerBinding>  
\<> powiązania  
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
|`mode`|Ciąg określający, czy wystąpienie równorzędnego programu rozpoznawania skojarzone z tą usługą jest zależne od protokołu PNRP, niestandardowym programem rozpoznawania nazw czy określane automatycznie. Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.|  
|`referralPolicy`|Ciąg określający sposób, w jaki odwołania są współużytkowane przez elementy równorzędne. Ten atrybut jest typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<nagłówki >](headers.md)|Określa ustawienia niestandardowej usługi rozpoznawania elementów równorzędnych.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązania](../../../misc/binding.md)|Definiuje wszystkie możliwości [ \<powiązań NetPeerTcpBinding >](netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Uwagi  
 Program rozpoznawania nazw równorzędnych to usługa odnajdywania używana przez kanały równorzędne do znajdowania węzłów równorzędnych, które uczestniczą w sieci równorzędnej. Jest również używany do "Zarejestruj" węzeł z siatką równorzędną, mechanizm, za pomocą którego węzeł równorzędny jest znany i dostępny w sieci równorzędnej. Aby uzyskać więcej informacji na temat rozpoznawania elementów równorzędnych, zobacz [rozpoznawanie elementów równorzędnych](../../../wcf/feature-details/peer-resolvers.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [Mechanizmy rozpoznawania elementów równorzędnych](../../../wcf/feature-details/peer-resolvers.md)
- [Dodawanie niestandardowego programu rozpoznawania nazw do aplikacji PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))
