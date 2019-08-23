---
title: <add> dla <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 65398c5afa9750f215c95899bb6004cae671123a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920272"
---
# <a name="add-of-authorizationpolicies"></a>\<Dodawanie > \<authorizationPolicies >
Określa zasady autoryzacji dla transformacji odszkodowania.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<> zachowania  
\<serviceAuthorization>  
\<authorizationPolicies >  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`policyType`|Wymagany atrybut ciągu.<br /><br /> Model kontroli dostępu Windows Communication Foundation (WCF) obsługuje Inicjowanie obsługi zestawu zasad autoryzacji jako typów. Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń. Na podstawie tego można udzielić lub odmówić kontroli dostępu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<authorizationPolicies >](authorizationpolicies.md)|Określa kolekcję typów zasad autoryzacji.|  
  
## <a name="remarks"></a>Uwagi  
 Każda zasada autoryzacji zawiera jeden wymagany `policyType` atrybut, który jest ciągiem. Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń. Na podstawie tego można udzielić lub odmówić kontroli dostępu. Aby uzyskać więcej informacji na temat działania zasad autoryzacji, zobacz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i [zasady autoryzacji](../../../wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [Autoryzowanie dostępu do operacji usługi](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [Instrukcje: Tworzenie niestandardowego Menedżera autoryzacji dla usługi](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [Zasady autoryzacji](../../../wcf/samples/authorization-policy.md)
