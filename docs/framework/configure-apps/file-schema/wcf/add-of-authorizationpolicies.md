---
title: <add> z <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 6a1a7d6b1ef9732e015536d8a78c058fe348113f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255500"
---
# <a name="add-of-authorizationpolicies"></a>\<Dodaj > z \<authorizationPolicies >
Określa zasady autoryzacji dla transformacji roszczenia.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<zachowanie >  
\<serviceAuthorization>  
\<authorizationPolicies>  
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
|`policyType`|Wymagany atrybut ciągu.<br /><br /> Model kontroli dostępu Windows Communication Foundation (WCF) obsługuje zapewnienie zestawu zasad autoryzacji jako typów. Ten atrybut określa zasady autoryzacji, która umożliwia przekształcanie jednego zestawu oświadczeń wejściowych na inny zestaw oświadczeń. Udzielić lub odmówić kontrola dostępu oparta na.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<authorizationPolicies>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|Określa kolekcję typów zasad autoryzacji.|  
  
## <a name="remarks"></a>Uwagi  
 Zasady autoryzacji, każdy zawiera jeden wymagane `policyType` atrybut, który jest ciągiem. Ten atrybut określa zasady autoryzacji, która umożliwia przekształcanie jednego zestawu oświadczeń wejściowych na inny zestaw oświadczeń. Udzielić lub odmówić kontrola dostępu oparta na. Aby uzyskać więcej informacji na temat sposobu działania zasad autoryzacji, zobacz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i [zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [Autoryzowanie dostępu do operacji usługi](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [Instrukcje: Tworzenie Menedżera autoryzacji niestandardowej dla usługi](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)
- [Zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md)
