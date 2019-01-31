---
title: <serviceAuthorization> — element
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: c967993c3a3f7276cd3a9076741de202e1f4c343
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257854"
---
# <a name="serviceauthorization-element"></a>\<serviceAuthorization > element
Określa ustawienia, które zezwalają na dostęp do operacji usługi  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceAuthorization>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|impersonateCallerForAllOperations|Wartość logiczna określająca, jeśli wszystkie operacje usługi personifikują wywołującego. Wartość domyślna to `false`.<br /><br /> Kiedy określonej operacji usługi personifikuje obiekt wywołujący, kontekst wątku jest włączane do kontekstu obiekt wywołujący przed wykonaniem określonej usługi.|  
|principalPermissionMode|Ustawia zabezpieczenie używane do wykonywania operacji na serwerze. Następujące wartości:<br /><br /> -Brak<br />-UseWindowsGroups<br />-UseAspNetRoles<br />— Niestandardowa<br /><br /> Wartość domyślna to UseWindowsGroups. Wartość jest typu <xref:System.ServiceModel.Description.PrincipalPermissionMode>. Aby uzyskać więcej informacji na temat korzystania z tego atrybutu, zobacz [jak: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).|  
|roleProviderName|Ciąg, który określa nazwę dostawcy ról, który dostarcza informacje o rolach dla aplikacji Windows Communication Foundation (WCF). Wartość domyślna to ciąg pusty.|  
|ServiceAuthorizationManagerType|Ciąg zawierający typ Menedżera usług autoryzacji. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.ServiceAuthorizationManager>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|authorizationPolicies|Zawiera kolekcję typów zasad autoryzacji, które można dodać za pomocą `add` — słowo kluczowe. Zasady autoryzacji, każdy zawiera jeden wymagane `policyType` atrybut, który jest ciągiem. Ten atrybut określa zasady autoryzacji, która umożliwia przekształcanie jednego zestawu oświadczeń wejściowych na inny zestaw oświadczeń. Udzielić lub odmówić kontrola dostępu oparta na. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Zawiera kolekcję ustawień zachowania dla usługi.|  
  
## <a name="remarks"></a>Uwagi  
 Ta sekcja zawiera elementy wpływające na autoryzacji, ról niestandardowych dostawców i personifikacji.  
  
 `principalPermissionMode` Atrybut określa grupy użytkowników do użycia podczas nadanie Metoda chroniona. Wartość domyślna to `UseWindowsGroups` i określa, czy grupy Windows, takie jak "Administratorzy" lub "Użytkowników", są przeszukiwane pod kątem tożsamości próby uzyskania dostępu do zasobu. Można również określić `UseAspNetRoles` Używanie dostawcy roli niestandardowej, skonfigurowanym w ramach \<system.web > elementu, jak pokazano w poniższym kodzie.  
  
```xml  
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
           type="System.Web.Security.SqlMembershipProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipProvider"
           enablePasswordRetrieval="false"
           enablePasswordReset="false"
           requiresQuestionAndAnswer="false"
           requiresUniqueEmail="true"
           passwordFormat="Hashed" />
    </providers>
  </membership>
  <!-- Other configuration code not shown. -->
</system.web>
```  
  
 Poniższy kod przedstawia `roleProviderName` używane z `principalPermissionMode` atrybutu.  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 Aby uzyskać szczegółowy przykład przy użyciu tego elementu konfiguracji, zobacz [Autoryzowanie dostępu do operacji usługi](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) i [zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Autoryzowanie dostępu do operacji usługi](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [Instrukcje: Tworzenie Menedżera autoryzacji niestandardowej dla usługi](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Instrukcje: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md)
