---
title: '&lt;clear&gt; w &lt;claimTypeRequirements&gt;. element,'
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: c64e5450e01fdb011eb726f3bef1a85a5698d0d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568338"
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a>&lt;clear&gt; w &lt;claimTypeRequirements&gt;. element,
Określa, że wszystkie typy roszczeń do usunięcia w federacyjnym poświadczeniu. Daje to gwarancję, że uruchomieniu pusty kolekcji.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<wsFederatedBinding>  
\<Powiązanie >  
\<security>  
\<message>  
\<claimTypeRequirements>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|Określa kolekcję wymaganych typów oświadczeń. Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> W federacyjnym scenariuszu usługi stanu wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzących musi mieć określone typy oświadczeń. Każdy element w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, oczekiwano w federacyjnym poświadczeniu.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
