---
title: '&lt;add&gt; w &lt;authorizationPolicies&gt;'
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 008f465134860141293776130ebd75cd39120f5e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753957"
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a>&lt;add&gt; w &lt;authorizationPolicies&gt;
Określa zasady autoryzacji dla transformacji roszczenia.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<zachowanie >  
\<serviceAuthorization >  
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
|`policyType`|Wymagany atrybut ciągu.<br /><br /> Model kontroli dostępu Windows Communication Foundation (WCF) obsługuje zapewnienie zestawu zasad autoryzacji jako typów. Ten atrybut określa zasady autoryzacji, dzięki czemu przekształcania jednego zestawu oświadczeń wejściowych do innego zestawu oświadczeń. Udzielono lub odmówiono kontrola dostępu oparta na.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<authorizationPolicies >](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|Określa kolekcję typów zasad autoryzacji.|  
  
## <a name="remarks"></a>Uwagi  
 Każdej zasady autoryzacji zawiera jeden z wymaganych `policyType` atrybut, który jest ciągiem. Ten atrybut określa zasady autoryzacji, dzięki czemu przekształcania jednego zestawu oświadczeń wejściowych do innego zestawu oświadczeń. Udzielono lub odmówiono kontrola dostępu oparta na. Aby uzyskać więcej informacji dotyczących sposobu działania zasad autoryzacji, zobacz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i [zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [Autoryzowanie dostępu do operacji usługi](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [Zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md)
